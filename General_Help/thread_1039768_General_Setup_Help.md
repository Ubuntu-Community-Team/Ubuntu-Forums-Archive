---
title: "General Setup Help"
date: 2009-01-14
forum: General Help
---

### Post by pandaking on 2009-01-14
Hello,
I thought I would make a post here as in the past the members have always got me the answer I needed.
I have a purchased a dedicated server and whilst I have it setup currently, it's not performing quite how it should (and crashes about twice a week :( )

I can only assume I missed a few steps with the various setups, and have decided to start fresh. I was hoping somebody could link me to some recommended guides (and which order to install in) to get the server running as the following:

[LIST=1]
[*]SFTP Server - The server will contain many confidential files and I will be downloading, and I need the transfers to be a secure as possible. (I have it setup currently, but it downloads very slow.)
[*]Web server - I will be hosting a couple of websites. I am happy to use ftp to access these as the data is not confidential (it seems to be running ok at the moment) MySQL would be good too.
[*]BNC - I use IRC and it would be nice to not be broadcasting my IP address to every tom dick and harry.
[/LIST]

I did also try to set up a samba share with hamachi, but couldn't quite get the settings right.

I am not sure what I did wrong before, as most of it *sort of* works.
As I say I can only assume I used an old guide, or missed a step.


Many thanks in advance, any comments appreciated. Any other good uses for a server?

---

### Post by Titan8990 on 2009-01-14
What is it specifically that doesn't work?


1) sudo apt-get install openssh-server

2) [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

3) IRC never was and never will be considered a "secure" protocol. What exactly do you use your IRC server for?


Why did you need Hamachi for your samba share? Is highly recommended that you do not share files over the internet using SMB. You should use one of the following:

sftp
scp
WebDAV

scp and sftp are not slower than many other file transfer protocols due the encryption. For faster transfers try WebDAV w/ SSL (or without if you don't have the need).

---

### Post by pandaking on 2009-01-14
> **Titan8990 said:**
> What is it specifically that doesn't work?


1) sudo apt-get install openssh-server

2) [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

3) IRC never was and never will be considered a "secure" protocol. What exactly do you use your IRC server for?
Thanks for the fast response.

As I say, it crashes about twice a week which is the main problem.

SFTP is working, but very slowly. I have tried many different FTP apps (currently using WinSCP) and they all download about 500KB/s.
The server is on a 100Mb connection, and I am on 20Mb.
The odd thing is, if I add another file to the queue they will both download at 500KB/s. This means to download a folder full of files I am currently, copying the file name, making the directory and then adding each item to the queue separately. It's very time consuming, and quite frankly it's a daft system. It's obviously not being maxed out, it's just some kid of cap.

I realise IRC isn't secure, and I am not running my own IRC server, as I said I use IRC to chat to people, and idle channels and I would rather not be broadcasting my home IP address to everyone.

**P.S.**
> **Titan8990 said:**
> Why did you need Hamachi for your samba share? Is highly recommended that you do not share files over the internet using SMB. You should use one of the following:

sftp
scp
WebDAV

scp and sftp are not slower than many other file transfer protocols due the encryption. For faster transfers try WebDAV w/ SSL (or without if you don't have the need).
As SFTP has been causing me a few hassles, I thought using hamachi would solve the problem by allowing me to browse to the file and transfer it to my local drives securely and quickly.

As to your other suggestions, I am after the most secure - I heard this was SFTP. If you think the other are more secure / better then I am more than happy to take your advice on that.

Thanks again Titan8990 :)

---

### Post by pandaking on 2009-01-22
Well the time has come, and I am ready to re-install. I have decided to  use the Server Version of Ubuntu this time round rather than the desktop, as I don't feel I need to use VNC anymore.

I have opted to use [ZNC]("http://en.znc.in/wiki/ZNC") as my IRC Bouncer, as I feel is has the most features and is being actively developed / has a good support community.

I will keep you posted on how I get on :)

---

### Post by Titan8990 on 2009-01-22
sftp is not a good choice if speed is a concern. To host files over the internet using a fast speed you should use FTP or WebDAV. If encryption is needed, then I would defiantly do WebDAV over SSL.

 

Interested to hear how things go.


Good luck.

---

### Post by pandaking on 2009-01-22
Well I have just finished seeting up LAMP (Linux,Apache,MySQL,PHP).
After installing "Ubuntu 8.10 Server Edition" (using my hosts online tool), I connected to my server via SSH with Putty and entered the following commands:
```
sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart
sudo apt-get install mysql-server
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
sudo /etc/init.d/apache2 restart
sudo a2enmod rewrite
sudo /etc/init.d/apache2 restart
```

I haven't tested everything yet (my ip brings up the test page), but so far so good. 

The only error/warning I got was that repeatedly throughout installation I got:
```
manconv: can't set the locale; make sure $LC_* and $LANG are correct
```or
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```

It doesn't seem critical, but would be nice to know what's wrong :p

---

### Post by pandaking on 2009-01-23
Next hurdle, it seems ZNC doesn't like to be installed a root. Also, the devleopers don't seem to have allowed for "make uninstall" so I have been forced to rummage around looking for files it's installed :(
It's a shame the version of ZNC in Ubuntus package manager is so out of date....

Anyway, live and learn. I now know about [Checkinstall]("http://www.asic-linux.com.mx/~izto/checkinstall/index.php") - I just wish I didn't need to find out the hard way.

So my questions now are:
&#8226; Should I have installed Apache, MySQL and PHP under a user account and not root?
&#8226; How can I fix the "Locale" errors mentioned in the post above?

Many thanks :)

---

### Post by IeU on 2009-02-09
I am also getting tons of errors . . .

```

root@xxxxxxxx:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  bind9 bind9-host bind9utils busybox-initramfs ca-certificates console-setup cpp-4.3 dnsutils gcc-4.3 gcc-4.3-base libbind9-40 libc6 libc6-dev libdns43 libgcc1 libgnutls26
  libgomp1 libisc44 libisccc40 libisccfg40 libldap-2.4-2 liblwres40 libssl0.9.8 libstdc++6 libx11-6 libx11-data linux-libc-dev login ntpdate openssl passwd perl perl-base
  perl-modules ufw vim vim-common vim-runtime vim-tiny xkb-data
40 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 38.3MB of archives.
After this operation, 36.9kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://fr.archive.ubuntu.com intrepid-updates/main login 1:4.1.1-1ubuntu1.2 [308kB]
Get:2 http://fr.archive.ubuntu.com intrepid-updates/main perl-modules 5.10.0-11.1ubuntu2.2 [3273kB]
Get:3 http://fr.archive.ubuntu.com intrepid-updates/main linux-libc-dev 2.6.27-11.27 [664kB]
Get:4 http://fr.archive.ubuntu.com intrepid-updates/main libc6-dev 2.8~20080505-0ubuntu8 [2590kB]
Get:5 http://fr.archive.ubuntu.com intrepid-updates/main libgomp1 4.3.2-1ubuntu12 [15.6kB]
Get:6 http://fr.archive.ubuntu.com intrepid-updates/main gcc-4.3-base 4.3.2-1ubuntu12 [105kB]
Get:7 http://fr.archive.ubuntu.com intrepid-updates/main libgcc1 1:4.3.2-1ubuntu12 [44.6kB]
Get:8 http://fr.archive.ubuntu.com intrepid-updates/main cpp-4.3 4.3.2-1ubuntu12 [3388kB]
Get:9 http://fr.archive.ubuntu.com intrepid-updates/main gcc-4.3 4.3.2-1ubuntu12 [2790kB]
Get:10 http://fr.archive.ubuntu.com intrepid-updates/main libstdc++6 4.3.2-1ubuntu12 [336kB]
Get:11 http://fr.archive.ubuntu.com intrepid-updates/main libc6 2.8~20080505-0ubuntu8 [4854kB]
Get:12 http://fr.archive.ubuntu.com intrepid-updates/main perl 5.10.0-11.1ubuntu2.2 [5224kB]
Get:13 http://fr.archive.ubuntu.com intrepid-updates/main perl-base 5.10.0-11.1ubuntu2.2 [947kB]
Get:14 http://fr.archive.ubuntu.com intrepid-updates/main passwd 1:4.1.1-1ubuntu1.2 [885kB]
Get:15 http://fr.archive.ubuntu.com intrepid-updates/main busybox-initramfs 1:1.10.2-1ubuntu7 [596kB]
Get:16 http://fr.archive.ubuntu.com intrepid-updates/main libssl0.9.8 0.9.8g-10.1ubuntu2.1 [958kB]
Get:17 http://fr.archive.ubuntu.com intrepid-updates/main openssl 0.9.8g-10.1ubuntu2.1 [404kB]
Get:18 http://fr.archive.ubuntu.com intrepid-updates/main ca-certificates 20080514-0ubuntu1.1 [143kB]
Get:19 http://fr.archive.ubuntu.com intrepid-updates/main xkb-data 1.3-2ubuntu4.4 [361kB]
Get:20 http://fr.archive.ubuntu.com intrepid-updates/main console-setup 1.25ubuntu4 [472kB]
Get:21 http://fr.archive.ubuntu.com intrepid-updates/main libgnutls26 2.4.1-1ubuntu0.2 [411kB]
Get:22 http://fr.archive.ubuntu.com intrepid-updates/main libldap-2.4-2 2.4.11-0ubuntu6.1 [204kB]
Get:23 http://fr.archive.ubuntu.com intrepid-updates/main vim-tiny 1:7.1.314-3ubuntu3.1 [394kB]
Get:24 http://fr.archive.ubuntu.com intrepid-updates/main vim 1:7.1.314-3ubuntu3.1 [959kB]
Get:25 http://fr.archive.ubuntu.com intrepid-updates/main vim-runtime 1:7.1.314-3ubuntu3.1 [5417kB]
Get:26 http://fr.archive.ubuntu.com intrepid-updates/main vim-common 1:7.1.314-3ubuntu3.1 [201kB]
Get:27 http://fr.archive.ubuntu.com intrepid-updates/main dnsutils 1:9.5.0.dfsg.P2-1ubuntu3.1 [125kB]
Get:28 http://fr.archive.ubuntu.com intrepid-updates/main bind9-host 1:9.5.0.dfsg.P2-1ubuntu3.1 [50.1kB]
Get:29 http://fr.archive.ubuntu.com intrepid-updates/main bind9 1:9.5.0.dfsg.P2-1ubuntu3.1 [256kB]
Get:30 http://fr.archive.ubuntu.com intrepid-updates/main libbind9-40 1:9.5.0.dfsg.P2-1ubuntu3.1 [30.9kB]
Get:31 http://fr.archive.ubuntu.com intrepid-updates/main libisccfg40 1:9.5.0.dfsg.P2-1ubuntu3.1 [48.6kB]
Get:32 http://fr.archive.ubuntu.com intrepid-updates/main libisccc40 1:9.5.0.dfsg.P2-1ubuntu3.1 [27.4kB]
Get:33 http://fr.archive.ubuntu.com intrepid-updates/main libdns43 1:9.5.0.dfsg.P2-1ubuntu3.1 [590kB]
Get:34 http://fr.archive.ubuntu.com intrepid-updates/main libisc44 1:9.5.0.dfsg.P2-1ubuntu3.1 [156kB]
Get:35 http://fr.archive.ubuntu.com intrepid-updates/main liblwres40 1:9.5.0.dfsg.P2-1ubuntu3.1 [46.2kB]
Get:36 http://fr.archive.ubuntu.com intrepid-updates/main bind9utils 1:9.5.0.dfsg.P2-1ubuntu3.1 [95.9kB]
Get:37 http://fr.archive.ubuntu.com intrepid-updates/main libx11-data 2:1.1.5-2ubuntu1.1 [170kB]
Get:38 http://fr.archive.ubuntu.com intrepid-updates/main libx11-6 2:1.1.5-2ubuntu1.1 [649kB]
Get:39 http://fr.archive.ubuntu.com intrepid-updates/main ufw 0.23.3 [43.5kB]
Get:40 http://fr.archive.ubuntu.com intrepid-updates/main ntpdate 1:4.2.4p4+dfsg-6ubuntu2.2 [65.8kB]
Fetched 38.3MB in 2s (16.5MB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Extracting templates from packages: 100%
Preconfiguring packages ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_CTYPE to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_MESSAGES to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_ALL to default locale: No such file or directory
console-setup failed to preconfigure, with exit status 10
(Reading database ... 20832 files and directories currently installed.)
Preparing to replace login 1:4.1.1-1ubuntu1.1 (using .../login_1%3a4.1.1-1ubuntu1.2_amd64.deb) ...
Unpacking replacement login ...
Processing triggers for man-db ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
Setting up login (1:4.1.1-1ubuntu1.2) ...

(Reading database ... 20832 files and directories currently installed.)
Preparing to replace perl-modules 5.10.0-11.1ubuntu2 (using .../perl-modules_5.10.0-11.1ubuntu2.2_all.deb) ...
Unpacking replacement perl-modules ...
Preparing to replace linux-libc-dev 2.6.27-9.19 (using .../linux-libc-dev_2.6.27-11.27_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace libc6-dev 2.8~20080505-0ubuntu7 (using .../libc6-dev_2.8~20080505-0ubuntu8_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libgomp1 4.3.2-1ubuntu11 (using .../libgomp1_4.3.2-1ubuntu12_amd64.deb) ...
Unpacking replacement libgomp1 ...
Preparing to replace gcc-4.3-base 4.3.2-1ubuntu11 (using .../gcc-4.3-base_4.3.2-1ubuntu12_amd64.deb) ...
Unpacking replacement gcc-4.3-base ...
Processing triggers for man-db ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
manconv: can't set the locale; make sure $LC_* and $LANG are correct
Setting up gcc-4.3-base (4.3.2-1ubuntu12) ...

(Reading database ... 20832 files and directories currently installed.)
.
.
.
.
.
.
.
.

```


any idea ?

---

