---
title: "Problem with today's Flash update..."
date: 2006-09-20
forum: Desktop Environments
---

### Post by mjpatey on 2006-09-20
I hope this is an isolated incident on my system alone, but here's what happened:

I clicked the update notifier, it downloaded and began the installation process, then as it finished, I got an error.  Unfortunately, I thought I copied it for pasting here, but I must not have, and now it's gone.

I'll reboot and post an update here.

Anybody else get an error while installing the update for Flash 7?

---

### Post by mjpatey on 2006-09-20
Well, I rebooted and everything's working fine, including Flash.  Not sure what the error was or what it meant.

---

### Post by Paulo Wageck on 2006-09-20
Just got these problems... samba was broken already... but flash wasn't!
I will reboot.... brb

> avatar@avatar-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-headers-k7 linux-image-386 linux-image-686 linux-image-k7 linux-restricted-modules-386 linux-restricted-modules-686
  linux-restricted-modules-k7
The following packages will be upgraded:
  clamav-base clamav-freshclam flashplugin-nonfree gzip libclamav1 libgnutls-dev libgnutls11 libgnutls12 linux-386 linux-686
  linux-k7 linux-restricted-modules-common
12 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 6012kB of archives.
After unpacking 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libgnutls-dev 1.2.9-2ubuntu1.1 [445kB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse flashplugin-nonfree 7.0.68~ubuntu1~dapper1 [15.8kB]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libgnutls12 1.2.9-2ubuntu1.1 [373kB]
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main gzip 1.3.5-12ubuntu0.1 [71.2kB]
Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe libclamav1 0.88.2-1ubuntu1.1 [263kB]
Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe clamav-freshclam 0.88.2-1ubuntu1.1 [4297kB]
Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe clamav-base 0.88.2-1ubuntu1.1 [172kB]
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe libgnutls11 1.0.16-14ubuntu1.1 [288kB]
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-386 2.6.15.25 [23.4kB]
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-686 2.6.15.25 [23.4kB]
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-k7 2.6.15.25 [23.4kB]
Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-common 2.6.15.11-5 [17.9kB]
Fetched 6012kB in 13s (436kB/s)
Preconfiguring packages ...
(Reading database ... 210868 files and directories currently installed.)
Preparing to replace libgnutls-dev 1.2.9-2ubuntu1 (using .../libgnutls-dev_1.2.9-2ubuntu1.1_i386.deb) ...
Unpacking replacement libgnutls-dev ...
Preparing to replace libgnutls12 1.2.9-2ubuntu1 (using .../libgnutls12_1.2.9-2ubuntu1.1_i386.deb) ...
Unpacking replacement libgnutls12 ...
Preparing to replace gzip 1.3.5-12 (using .../gzip_1.3.5-12ubuntu0.1_i386.deb) ...
Unpacking replacement gzip ...
Setting up gzip (1.3.5-12ubuntu0.1) ...

(Reading database ... 210868 files and directories currently installed.)
Preparing to replace libclamav1 0.88.2-1ubuntu1 (using .../libclamav1_0.88.2-1ubuntu1.1_i386.deb) ...
Unpacking replacement libclamav1 ...
Preparing to replace clamav-freshclam 0.88.2-1ubuntu1 (using .../clamav-freshclam_0.88.2-1ubuntu1.1_i386.deb) ...
Unpacking replacement clamav-freshclam ...
Preparing to replace clamav-base 0.88.2-1ubuntu1 (using .../clamav-base_0.88.2-1ubuntu1.1_all.deb) ...
Unpacking replacement clamav-base ...
Preparing to replace flashplugin-nonfree 7.0.63.3ubuntu3 (using .../flashplugin-nonfree_7.0.68~ubuntu1~dapper1_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Preparing to replace libgnutls11 1.0.16-14ubuntu1 (using .../libgnutls11_1.0.16-14ubuntu1.1_i386.deb) ...
Unpacking replacement libgnutls11 ...
Preparing to replace linux-386 2.6.15.24 (using .../linux-386_2.6.15.25_i386.deb) ...
Unpacking replacement linux-386 ...
Preparing to replace linux-686 2.6.15.24 (using .../linux-686_2.6.15.25_i386.deb) ...
Unpacking replacement linux-686 ...
Preparing to replace linux-k7 2.6.15.24 (using .../linux-k7_2.6.15.25_i386.deb) ...
Unpacking replacement linux-k7 ...
Preparing to replace linux-restricted-modules-common 2.6.15.11-4 (using .../linux-restricted-modules-common_2.6.15.11-5_all.deb) ...
Unpacking replacement linux-restricted-modules-common ...
Setting up libgnutls12 (1.2.9-2ubuntu1.1) ...

Setting up libgnutlsavatar@avatar-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-headers-k7 linux-image-386 linux-image-686 linux-image-k7 linux-restricted-modules-386 linux-restricted-modules-686
  linux-restricted-modules-k7
The following packages will be upgraded:
  clamav-base clamav-freshclam flashplugin-nonfree gzip libclamav1 libgnutls-dev libgnutls11 libgnutls12 linux-386 linux-686
  linux-k7 linux-restricted-modules-common
12 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 6012kB of archives.
After unpacking 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libgnutls-dev 1.2.9-2ubuntu1.1 [445kB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse flashplugin-nonfree 7.0.68~ubuntu1~dapper1 [15.8kB]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libgnutls12 1.2.9-2ubuntu1.1 [373kB]
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main gzip 1.3.5-12ubuntu0.1 [71.2kB]
Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe libclamav1 0.88.2-1ubuntu1.1 [263kB]
Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe clamav-freshclam 0.88.2-1ubuntu1.1 [4297kB]
Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe clamav-base 0.88.2-1ubuntu1.1 [172kB]
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe libgnutls11 1.0.16-14ubuntu1.1 [288kB]
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-386 2.6.15.25 [23.4kB]
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-686 2.6.15.25 [23.4kB]
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-k7 2.6.15.25 [23.4kB]
Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-common 2.6.15.11-5 [17.9kB]
Fetched 6012kB in 13s (436kB/s)
Preconfiguring packages ...
(Reading database ... 210868 files and directories currently installed.)
Preparing to replace libgnutls-dev 1.2.9-2ubuntu1 (using .../libgnutls-dev_1.2.9-2ubuntu1.1_i386.deb) ...
Unpacking replacement libgnutls-dev ...
Preparing to replace libgnutls12 1.2.9-2ubuntu1 (using .../libgnutls12_1.2.9-2ubuntu1.1_i386.deb) ...
Unpacking replacement libgnutls12 ...
Preparing to replace gzip 1.3.5-12 (using .../gzip_1.3.5-12ubuntu0.1_i386.deb) ...
Unpacking replacement gzip ...
Setting up gzip (1.3.5-12ubuntu0.1) ...

(Reading database ... 210868 files and directories currently installed.)
Preparing to replace libclamav1 0.88.2-1ubuntu1 (using .../libclamav1_0.88.2-1ubuntu1.1_i386.deb) ...
Unpacking replacement libclamav1 ...
Preparing to replace clamav-freshclam 0.88.2-1ubuntu1 (using .../clamav-freshclam_0.88.2-1ubuntu1.1_i386.deb) ...
Unpacking replacement clamav-freshclam ...
Preparing to replace clamav-base 0.88.2-1ubuntu1 (using .../clamav-base_0.88.2-1ubuntu1.1_all.deb) ...
Unpacking replacement clamav-base ...
Preparing to replace flashplugin-nonfree 7.0.63.3ubuntu3 (using .../flashplugin-nonfree_7.0.68~ubuntu1~dapper1_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Preparing to replace libgnutls11 1.0.16-14ubuntu1 (using .../libgnutls11_1.0.16-14ubuntu1.1_i386.deb) ...
Unpacking replacement libgnutls11 ...
Preparing to replace linux-386 2.6.15.24 (using .../linux-386_2.6.15.25_i386.deb) ...
Unpacking replacement linux-386 ...
Preparing to replace linux-686 2.6.15.24 (using .../linux-686_2.6.15.25_i386.deb) ...
Unpacking replacement linux-686 ...
Preparing to replace linux-k7 2.6.15.24 (using .../linux-k7_2.6.15.25_i386.deb) ...
Unpacking replacement linux-k7 ...
Preparing to replace linux-restricted-modules-common 2.6.15.11-4 (using .../linux-restricted-modules-common_2.6.15.11-5_all.deb) ...
Unpacking replacement linux-restricted-modules-common ...
Setting up libgnutls12 (1.2.9-2ubuntu1.1) ...

Setting up libgnutls-dev (1.2.9-2ubuntu1.1) ...
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Setting up libclamav1 (0.88.2-1ubuntu1.1) ...

Setting up clamav-base (0.88.2-1ubuntu1.1) ...
Replacing config file /etc/clamav/clamd.conf with new version

Setting up clamav-freshclam (0.88.2-1ubuntu1.1) ...

Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libgnutls11 (1.0.16-14ubuntu1.1) ...

Setting up linux-386 (2.6.15.25) ...
Setting up linux-686 (2.6.15.25) ...
Setting up linux-k7 (2.6.15.25) ...
Setting up linux-restricted-modules-common (2.6.15.11-5) ...

Errors were encountered while processing:
 samba
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
avatar@avatar-laptop:~$ sudo apt-get remove samba
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  samba
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 210869 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
-dev (1.2.9-2ubuntu1.1) ...
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Setting up libclamav1 (0.88.2-1ubuntu1.1) ...

Setting up clamav-base (0.88.2-1ubuntu1.1) ...
Replacing config file /etc/clamav/clamd.conf with new version

Setting up clamav-freshclam (0.88.2-1ubuntu1.1) ...

Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libgnutls11 (1.0.16-14ubuntu1.1) ...

Setting up linux-386 (2.6.15.25) ...
Setting up linux-686 (2.6.15.25) ...
Setting up linux-k7 (2.6.15.25) ...
Setting up linux-restricted-modules-common (2.6.15.11-5) ...

Errors were encountered while processing:
 samba
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
avatar@avatar-laptop:~$ sudo apt-get remove samba
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  samba
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 210869 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
avatar@avatar-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-headers-k7 linux-image-386 linux-image-686 linux-image-k7 linux-restricted-modules-386 linux-restricted-modules-686
  linux-restricted-modules-k7
The following packages will be upgraded:
  clamav-base clamav-freshclam flashplugin-nonfree gzip libclamav1 libgnutls-dev libgnutls11 libgnutls12 linux-386 linux-686
  linux-k7 linux-restricted-modules-common
12 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 6012kB of archives.
After unpacking 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libgnutls-dev 1.2.9-2ubuntu1.1 [445kB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse flashplugin-nonfree 7.0.68~ubuntu1~dapper1 [15.8kB]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libgnutls12 1.2.9-2ubuntu1.1 [373kB]
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main gzip 1.3.5-12ubuntu0.1 [71.2kB]
Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe libclamav1 0.88.2-1ubuntu1.1 [263kB]
Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe clamav-freshclam 0.88.2-1ubuntu1.1 [4297kB]
Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe clamav-base 0.88.2-1ubuntu1.1 [172kB]
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe libgnutls11 1.0.16-14ubuntu1.1 [288kB]
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-386 2.6.15.25 [23.4kB]
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-686 2.6.15.25 [23.4kB]
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-k7 2.6.15.25 [23.4kB]
Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-common 2.6.15.11-5 [17.9kB]
Fetched 6012kB in 13s (436kB/s)
Preconfiguring packages ...
(Reading database ... 210868 files and directories currently installed.)
Preparing to replace libgnutls-dev 1.2.9-2ubuntu1 (using .../libgnutls-dev_1.2.9-2ubuntu1.1_i386.deb) ...
Unpacking replacement libgnutls-dev ...
Preparing to replace libgnutls12 1.2.9-2ubuntu1 (using .../libgnutls12_1.2.9-2ubuntu1.1_i386.deb) ...
Unpacking replacement libgnutls12 ...
Preparing to replace gzip 1.3.5-12 (using .../gzip_1.3.5-12ubuntu0.1_i386.deb) ...
Unpacking replacement gzip ...
Setting up gzip (1.3.5-12ubuntu0.1) ...

(Reading database ... 210868 files and directories currently installed.)
Preparing to replace libclamav1 0.88.2-1ubuntu1 (using .../libclamav1_0.88.2-1ubuntu1.1_i386.deb) ...
Unpacking replacement libclamav1 ...
Preparing to replace clamav-freshclam 0.88.2-1ubuntu1 (using .../clamav-freshclam_0.88.2-1ubuntu1.1_i386.deb) ...
Unpacking replacement clamav-freshclam ...
Preparing to replace clamav-base 0.88.2-1ubuntu1 (using .../clamav-base_0.88.2-1ubuntu1.1_all.deb) ...
Unpacking replacement clamav-base ...
Preparing to replace flashplugin-nonfree 7.0.63.3ubuntu3 (using .../flashplugin-nonfree_7.0.68~ubuntu1~dapper1_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Preparing to replace libgnutls11 1.0.16-14ubuntu1 (using .../libgnutls11_1.0.16-14ubuntu1.1_i386.deb) ...
Unpacking replacement libgnutls11 ...
Preparing to replace linux-386 2.6.15.24 (using .../linux-386_2.6.15.25_i386.deb) ...
Unpacking replacement linux-386 ...
Preparing to replace linux-686 2.6.15.24 (using .../linux-686_2.6.15.25_i386.deb) ...
Unpacking replacement linux-686 ...
Preparing to replace linux-k7 2.6.15.24 (using .../linux-k7_2.6.15.25_i386.deb) ...
Unpacking replacement linux-k7 ...
Preparing to replace linux-restricted-modules-common 2.6.15.11-4 (using .../linux-restricted-modules-common_2.6.15.11-5_all.deb) ...
Unpacking replacement linux-restricted-modules-common ...
Setting up libgnutls12 (1.2.9-2ubuntu1.1) ...

Setting up libgnutls-dev (1.2.9-2ubuntu1.1) ...
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Setting up libclamav1 (0.88.2-1ubuntu1.1) ...

Setting up clamav-base (0.88.2-1ubuntu1.1) ...
Replacing config file /etc/clamav/clamd.conf with new version

Setting up clamav-freshclam (0.88.2-1ubuntu1.1) ...

Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libgnutls11 (1.0.16-14ubuntu1.1) ...

Setting up linux-386 (2.6.15.25) ...
Setting up linux-686 (2.6.15.25) ...
Setting up linux-k7 (2.6.15.25) ...
Setting up linux-restricted-modules-common (2.6.15.11-5) ...

Errors were encountered while processing:
 samba
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
avatar@avatar-laptop:~$ sudo apt-get remove samba
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  samba
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 210869 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by mjpatey on 2006-09-20
Yeah, here's the error I got earlier.  I got it again when doing a sudo apt-get upgrade:

> dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

However, Flash seems to be working fine.

---

### Post by neymac on 2006-09-20
The same occurred here.



> dpkg: error processing flashplugin-nonfree (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kalpik on 2006-09-20
Im also getting the same error.. Any fix yet?

---

### Post by X.Cyclop on 2006-09-20
This is what my terminal shows:

```
Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

But, i'm able to play flash files with Firefox. So... :confused:

---

### Post by cptnapalm on 2006-09-20
What's up with things breaking up on updates these days...  :(

---

### Post by neymac on 2006-09-20
Open Firefox (or Swiftfox) an type "about: plugins" in address bar.

The last flashplayer (at the moment) is Shockwave Flash 7.0 r68.

See [http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/) , there are instructions to install the last version manually, or you can wait for the fix.

---

### Post by jethro10 on 2006-09-20
I do believe this was caused by the adobe site temporarily not having the flash program available for download.

J

---

### Post by nullmind on 2006-09-20
Same error here:

```

Preparing to replace flashplugin-nonfree 7.0.63.3ubuntu3 (using .../flashplugin-nonfree_7.0.68~ubuntu1~dapper1_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by mssm on 2006-09-20
I got the same error, however flash is working.

---

### Post by piroshki on 2006-09-20
I think the upgraded package is trying to drop a new script (/etc/init.d/flashplugin-nonfree) to fix some of the flash plugin sound problems.

Looking in the packages post install script, my system seems to be having problems with this line:
```

update-rc.d flashplugin-nonfree multiuser >/dev/null
```

It doesn't like the "multiuser" argument in there on my system, if I try it with "defaults" instead, then the command succeeds:

```
sudo perl -pi -e 's/multiuser/defaults/' /var/lib/dpkg/info/flashplugin-nonfree.postinst
sudo dpkg --configure flashplugin-nonfree
```

It still says "installation failed" at the end, but the other errors are gone.```
dpkg -l|grep flash
``` says that the package was installed successfully.
```
find /etc/rc* -name S20flashplugin-nonfree
```
shows that the new script is installed and it appears to work for me after reboot.

---

### Post by matgates on 2006-09-21
Why is flashplayer installing something in the /etc/rc* directories anyway?  Since when did a browser plugin need something running as a daemon?

---

### Post by kairu0 on 2006-09-21
> **cptnapalm said:**
> What's up with things breaking up on updates these days...  :(

No kidding. It's not safe to update anything anymore.

---

### Post by raintheory on 2006-09-21
I kept getting this error as well (and it would keep trying to update itself whenever synaptic or apt was running).

I used Automatix to update/reinstall Flash and it updated fine.  Any other way gave me errors.

---

### Post by oyvindaa on 2006-09-21
> **raintheory said:**
> I kept getting this error as well (and it would keep trying to update itself whenever synaptic or apt was running).

I used Automatix to update/reinstall Flash and it updated fine.  Any other way gave me errors.

Same here mate. Done and dusted.

---

### Post by Cable on 2006-09-21
Check out [this]("http://www.ubuntuforums.org/showthread.php?t=261179") thread.

---

