FROM kalilinux/kali-rolling

# KaliLinux Package
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get install -y kali-linux-core kali-linux-default kali-tools-web

# Windows RDP
RUN apt-get install -y xfce4 xfce4-goodies xrdp dbus-x11

# Install Metasploit
RUN apt-get install -y build-essential zlib1g zlib1g-dev \
    libpq-dev libpcap-dev libsqlite3-dev \
    ruby ruby-dev git

RUN mkdir -p /opt/metasploit && \
    cd /opt/metasploit && \
    git clone https://github.com/rapid7/metasploit-framework.git && \
    cd metasploit-framework && \
    gem install bundler && \
    bundle install

RUN apt-get install -y postgresql postgresql-contrib    

CMD ["sh", "-c", "echo 'startxfce4' > ~/.xsession && service xrdp start && bash"]
