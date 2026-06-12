---
title: "Attention to all guru's? Need help with an unmet dependency"
date: 2009-02-19
forum: General Help
---

### Post by cunrah on 2009-02-19
Hey Guys,

Im new here but not new to linux, Also in saying that im really sorry if this has been brought up before in another thread. 

If it has then more the fool me as I've searched for threads containing words from this and i've not found anything..

Anyways... This is what I've stumbled across and I have no idea how this has happened... Hence why i'm here asking for help and some guidence.


I've been wanting to install a package on a box of mine, but when i did so i got a libstdc++ error, I've fixed that, but now for some reason apt-get wants to removed everything from the box... (ive never see this happen ever!)


Here's the box info

root@server01:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

root@server01:~# uname -a
Linux *******.*********.co.uk 2.6.15-52-386 #1 PREEMPT Fri Sep 5 14:00:47 UTC 2008 i686 GNU/Linux


Here's the bash dump.
So you can see the various thing's I did etc...


```

root@server01:~# apt-get check
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run âapt-get -f installâ to correct these.
The following packages have unmet dependencies.
  cpp-4.2: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is installed
  g++: Depends: gcc (>= 4:4.2.3-1ubuntu6) but 4:4.2.3-1ubuntu3 is installed
  g++-4.2: Depends: gcc-4.2 (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is installed
           Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is installed
  gcc-4.2: Depends: cpp-4.2 (= 4.2.4-3ubuntu4) but 4.2.4-1ubuntu3 is installed
           Depends: libgcc1 (>= 1:4.2.4-3ubuntu4) but 1:4.2.3-2ubuntu7 is installed
  libgcc1: Depends: gcc-4.2-base (= 4.2.3-2ubuntu7) but 4.2.4-3ubuntu4 is installed
  libgomp1: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is installed
  libstdc++6-4.2-dev: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is installed
E: Unmet dependencies. Try using -f.


root@server01:~# apt-get install gcc-4.2-base
Reading package lists... Done
Building dependency tree
Reading state information... Done
gcc-4.2-base is already the newest version.
You might want to run âapt-get -f installâ to correct these:
The following packages have unmet dependencies.
  cpp-4.2: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is to be installed
  g++: Depends: gcc (>= 4:4.2.3-1ubuntu6) but 4:4.2.3-1ubuntu3 is to be installed
  g++-4.2: Depends: gcc-4.2 (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is to be installed
           Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is to be installed
  gcc-4.2: Depends: cpp-4.2 (= 4.2.4-3ubuntu4) but 4.2.4-1ubuntu3 is to be installed
           Depends: libgcc1 (>= 1:4.2.4-3ubuntu4) but 1:4.2.3-2ubuntu7 is to be installed
  libgcc1: Depends: gcc-4.2-base (= 4.2.3-2ubuntu7) but 4.2.4-3ubuntu4 is to be installed
  libgomp1: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is to be installed
  libstdc++6-4.2-dev: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is to be installed
E: Unmet dependencies. Try âapt-get -f installâ with no packages (or specify a solution).


root@server01:~# apt-get install gcc-4.2-base
Reading package lists... Done
Building dependency tree
Reading state information... Done
gcc-4.2-base is already the newest version.
You might want to run âapt-get -f installâ to correct these:
The following packages have unmet dependencies.
  cpp-4.2: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is to be installed
  g++: Depends: gcc (>= 4:4.2.3-1ubuntu6) but 4:4.2.3-1ubuntu3 is to be installed
  g++-4.2: Depends: gcc-4.2 (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is to be installed
           Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is to be installed
  gcc-4.2: Depends: cpp-4.2 (= 4.2.4-3ubuntu4) but 4.2.4-1ubuntu3 is to be installed
           Depends: libgcc1 (>= 1:4.2.4-3ubuntu4) but 1:4.2.3-2ubuntu7 is to be installed
  libgcc1: Depends: gcc-4.2-base (= 4.2.3-2ubuntu7) but 4.2.4-3ubuntu4 is to be installed
  libgomp1: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is to be installed
  libstdc++6-4.2-dev: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-3ubuntu4 is to be installed
E: Unmet dependencies. Try âapt-get -f installâ with no packages (or specify a solution).


root@server01:~# apt-get --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies...Done
The following packages will be REMOVED
  adduser alsa-base alsa-utils apache-common apache-ssl apache2 apache2-mpm-prefork apache2-utils apache2.2-common apt apt-utils aptitude at autoconf automake1.9
  base-files base-passwd bash belocs-locales-bin bind9 bind9-host binfmt-support binutils binutils-static bison bsdmainutils bsdutils bzip2 ca-certificates chkrootkit
  console-common console-data console-tools coreutils courier-authdaemon courier-authlib courier-authlib-userdb courier-base courier-ssl cpio cpp cpp-3.3 cpp-4.0 cpp-4.2
  cramfsprogs cron dash db4.6-util debconf debconf-i18n debianutils defoma diff dmidecode dmsetup dnsutils dosfstools dpkg dselect e2fslibs e2fsprogs ed eject elinks
  ethtool evms evms-ncurses expect fdutils fetchmail ffmpeg file findutils flex fontconfig fontconfig-config ftp g++ g++-4.0 g++-4.2 gamin gcc gcc-3.3 gcc-4.0 gcc-4.2
  gettext gettext-base gnupg gpgv grep grepmap groff-base grub gsfonts gzip hdparm hostname ifupdown imagemagick info initramfs-tools initrd-tools initscripts inputattach
  iproute iptables iputils-arping iputils-ping iputils-tracepath jfsutils klogd laptop-detect less libacl1 libapache2-mod-php5 libapr0 libapr1 libaprutil1
  libarchive-zip-perl libart-2.0-2 libasn1-6-heimdal libasound2 libatk1.0-0 libatm1 libattr1 libaudio2 libaudiofile0 libavcodec1d libavformat1d libavutil1d libbind9-0
  libbind9-30 libblkid1 libbz2-1.0 libc6 libc6-dev libc6-i686 libcairo2 libcap1 libck-connector0 libcomerr2 libcompress-raw-zlib-perl libcompress-zlib-perl libconsole
  libcroco3 libcupsys2 libcurl3 libcurl3-gnutls libcwidget3 libdatrie0 libdb-file-lock-perl libdb3 libdb3-util libdb4.2 libdb4.3 libdb4.3-dev libdb4.4 libdb4.5 libdb4.6
  libdbd-mysql-perl libdbi-perl libdbus-1-3 libdc1394-13 libdevmapper1.02.1 libdigest-hmac-perl libdigest-sha1-perl libdirectfb-1.0-0 libdjvulibre15 libdns21 libdns35
  libdrm2 libedit2 libelfg0 libesd-alsa0 libevms-2.5 libexif12 libexpat1 libfontconfig1 libfreetype6 libfribidi0 libgamin0 libgc1c2 libgcc1 libgcrypt11 libgd-gif1
  libgd2-xpm libgdbm3 libgeoip1 libgif4 libgl1-mesa-glx libglib2.0-0 libglu1-mesa libgnutls12 libgnutls13 libgomp1 libgpg-error0 libgphoto2-2 libgphoto2-port0 libgpmg1
  libgraphviz4 libgsf-1-114 libgsm1 libgssapi4-heimdal libgtk2.0-0 libhal1 libhtml-parser-perl libhtml-tagset-perl libice6 libid3tag0 libidn11 libimlib2
  libio-compress-base-perl libio-compress-zlib-perl libisc11 libisc35 libisccc0 libisccc30 libisccfg1 libisccfg30 libiw28 libiw29 libjasper-1.701-1 libjasper1 libjpeg62
  libkeyutils1 libkrb5-17-heimdal libkrb53 liblcms1 libldap-2.4-2 libldap2 liblocale-gettext-perl liblockfile1 libltdl3 liblua50 liblualib50 liblwres30 liblwres9 liblzo1
  liblzo2-2 libmagic1 libmagick10 libmagick9 libmcrypt4 libmhash2 libmysqlclient15off libncurses5 libncursesw5 libnet-daemon-perl libnet-dns-perl libnet-ip-perl
  libnetpbm10 libnewt0.52 libogg0 libopencdk10 libopencdk8 libopenexr2ldbl libpam-foreground libpam-modules libpam0g libpango1.0-0 libpango1.0-common libparted1.6-13
  libparted1.7-1 libpcap0.8 libpcre3 libperl5.8 libpixman-1-0 libplrpc-perl libpng12-0 libpopt-dev libpopt0 libpq4 libpq5 libraw1394-5 libraw1394-8 libreadline5
  libroken16-heimdal librrd2 librsvg2-2 libruby1.8 libsasl2 libsasl2-2 libsasl2-modules libsdl1.2debian libsdl1.2debian-alsa libselinux1 libsensors3 libsepol1
  libsigc++-2.0-0c2a libslang2 libsm6 libsnmp-session-perl libsnmp15 libsnmp9 libsqlite3-0 libss2 libssl0.9.8 libstdc++6 libstdc++6-4.0-dev libstdc++6-4.2-dev libswscale1d
  libsysfs2 libt1-5 libtasn1-2 libtasn1-3 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libthai0 libtheora0 libtiff4 libtool libungif4g liburi-perl
  libusb-0.1-4 libuuid1 libvolume-id0 libvorbis0a libvorbisenc2 libwmf0.2-7 libwrap0 libx11-6 libx11-data libxau6 libxcb-xlib0 libxcb1 libxcomposite1 libxcursor1
  libxdamage1 libxdmcp6 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxml2 libxpm4 libxrandr2 libxrender1 libxslt1.1 libxt6 libxxf86dga1 libxxf86vm1 libzzip-0-12
  linux-386 linux-image-2.6.15-26-386 linux-image-2.6.15-26-686 linux-image-2.6.15-52-386 linux-image-2.6.24-21-386 linux-image-386 linux-restricted-modules-2.6.15-26-386
  linux-restricted-modules-2.6.15-52-386 linux-restricted-modules-2.6.24-21-386 linux-restricted-modules-386 linux-restricted-modules-common linux-sound-base
  linux-ubuntu-modules-2.6.24-21-386 locales locate login logrotate lsb-base lsb-release lshw lsof ltrace lvm-common lynx lzma m4 mailx make makedev man-db mawk mcrypt
  mdadm mii-diag mktemp module-init-tools mount mrtg mtr-tiny mysql-client-5.0 mysql-server mysql-server-5.0 nano ncftp ncurses-base ncurses-bin net-tools netbase netcat
  netcat-traditional netpbm nmap ntp ntpdate nvidia-kernel-common openssh-client openssh-server openssl openssl-blacklist parted passwd pciutils pcmciautils perl perl-base
  perl-modules php4-common php5 php5-common php5-curl php5-gd php5-mcrypt php5-mysql popularity-contest postfix ppp pppconfig pppoeconf procmail procps proftpd psmisc
  python python-central python-minimal python2.4 python2.4-minimal python2.5 python2.5-minimal quota reiser4progs reiserfsprogs reportbug rrdtool rsync samba samba-common
  sasl2-bin screen sed sendmail-base sendmail-cf sensible-mda snmp snmpd ssh ssl-cert strace sudo sysklogd sysvinit sysvutils tar tcl8.4 tcpd tcpdump telnet time
  ttf-bitstream-vera ttf-dejavu ttf-dejavu-core ttf-dejavu-extra ttf-freefont tzdata ubuntu-keyring ubuntu-standard ucf udev ufw unrar-free unzip update-inetd usbutils
  util-linux uuid-runtime vim vim-common w3m webalizer webware wget whiptail winbind wine wireless-tools wpasupplicant x11-common xfsprogs zip zlib1g zlib1g-dev
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt) base-files base-passwd (due to base-files) libpam-modules (due to base-files) bash debianutils (due
  to bash) libncurses5 (due to bash) bsdutils coreutils libacl1 (due to coreutils) libselinux1 (due to coreutils) dash mktemp (due to debianutils) diff dpkg lzma (due to
  dpkg) e2fsprogs e2fslibs (due to e2fsprogs) libblkid1 (due to e2fsprogs) libcomerr2 (due to e2fsprogs) libss2 (due to e2fsprogs) libuuid1 (due to e2fsprogs) findutils
  grep gzip hostname login libpam0g (due to login) mount ncurses-base ncurses-bin perl-base python-minimal python2.5-minimal (due to python-minimal) sed sysvutils
  libsepol1 (due to sysvutils) tar util-linux lsb-base (due to util-linux) tzdata (due to util-linux) libslang2 (due to util-linux) zlib1g (due to util-linux)
0 upgraded, 0 newly installed, 495 to remove and 5 not upgraded.
3 not fully installed or removed.
After this operation, 1072MB disk space will be freed.
You are about to do something potentially harmful
To continue type in the phrase âYes, do as I say!â
 ?]
root@server01:~#

```


If anyone could advice me into what to do... because I really dont want to loose anything... :s

Cheers.
C.

---

### Post by dcstar on 2009-02-19
> **cunrah said:**
> 
..........
I've been wanting to install a package on a box of mine, but when i did so i got a libstdc++ error, I've fixed that, but now for some reason apt-get wants to removed everything from the box... (ive never see this happen ever!)
..........
If anyone could advice me into what to do... because I really dont want to lose anything... :s

Cheers.
C.

I would say you have obtained a package that is not built for the Ubuntu version you are using and it has dependencies that cannot be satisfied, so the bottom-line is that you have to uninstall that package as it will not work on your current Ubuntu version (as those messages suggest).

You cannot just install .deb packages that you find somewhere, they all have to meet specific pre-conditions and in some cases you just cannot make your system compatible with them.

---

### Post by cunrah on 2009-02-19
Cheers dcstar, I wasn't aware that i'd installed a package that was the wrong version so to speak, I shall have a look through the system and find whats actually gone head over heals so to speak,

I can honestly say i feel rather daft if thats the reason for this! *kicks head*

Thanks for you help.
C.

---

### Post by cunrah on 2009-02-19
I know this is silly, but is there any references online as to guide me in finding this package thats messed up? 

Im really worried that if the server drops it won't come back up again due to the wrong gcc and libs that are in use... 


Cheers
C.

---

### Post by bodhi.zazen on 2009-02-19
Well, what software did you install from outside the ubuntu repositories ?

What repo did you add in your sources list ?

What *.deb did you manually install ?

Those answers ponder you must.

---

### Post by mc4man on 2009-02-19
> but when i did so i got a  libstdc++ error, I've fixed that

You may want to revisit what you did to 'fix that', it would appear you forced libstdc++ to the intrepid version or otherwise added repo's so it could be

---

### Post by cunrah on 2009-02-19
Sorted it, apprently i needed cpp-4.2_4.2.4-1ubuntu3_i386.deb for gcc++ to work correctly, I've followed the loops and ref'd packages.ubuntu.com

and installed all of the following to fix my dependency issue:

cpp-4.2_4.2.4-1ubuntu3_i386.deb 
cpp-4.2_4.2.4-3ubuntu4_i386.deb   
gcc-4.2-base_4.2.4-1ubuntu3_i386.deb  
gcc_4.2.3-1ubuntu6_i386.deb  
gcc-4.2_4.2.4-1ubuntu3_i386.deb  
libstdc++6_4.2.3-2ubuntu7_i386.deb
libstdc++6_4.2.4-1ubuntu3_i386.deb
libgcc1_4.3.2-1ubuntu11_i386.deb

All is now working correctly in dpkg and apt-get now runs as it should :) 

Cheers for your help guys, Its 2am, I think i've had my head screwed on backwards tonight! Thank god for cafine! :)

Cheers
C.

---

### Post by cunrah on 2009-02-19
Sorry for double post... but this is an FYI,

It all started from this:

apt-get: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

So if anyone has that issue, follow your file system in /usr/lib and /lib and make sure you have the correct versions of libstdc++ 

Hope that helps anyone who's stumbled onto that error... It sure as hell didnt help me, but working my steps backwards finxed my issues.

Regards
C.

---

