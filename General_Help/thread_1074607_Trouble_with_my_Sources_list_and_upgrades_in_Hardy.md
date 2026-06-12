---
title: "Trouble with my Sources list and upgrades in Hardy"
date: 2009-02-19
forum: General Help
---

### Post by MedianMajik on 2009-02-19
[COLOR="black"][COLOR="Silver"]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8AD328D8A58BCAE3
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problems

I've been trying to iron out any issues with my sources.list as I've been getting a lot of little errors in the last 6 weeks.  I've been using [this]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories") guide to help me out, but I'm still having problems.[/COLOR][/COLOR]

Right now I have some upgrades being held back and I'd like to them while using Hardy.  I'm currently running 2.6.24.22-generic on x86_64.

The following packages have been kept back:
  abiword-common deluge-torrent linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-generic
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-style-human openoffice.org-writer python-uno vlc vlc-nox
  vlc-plugin-pulse

Edit: I've noticed that overall my upgrades are way out of date.  For example I'd love to get the latest version of Gnome-Do 0.8, but it still won't show up as a possible upgrade after adding the necessary repository/key
Thanks in advance for your help!

---

### Post by drs305 on 2009-02-19
You can import the two keys with the following:
```

gpg --keyserver keyserver.ubuntu.com --recv 8AD328D8A58BCAE3  60D11217247D1CFF
gpg --export --armor 8AD328D8A58BCAE3  60D11217247D1CFF | sudo apt-key add -
sudo apt-get update

# if they can't be combined:
gpg --keyserver keyserver.ubuntu.com --recv 8AD328D8A58BCAE3
gpg --export --armor 8AD328D8A58BCAE3 | sudo apt-key add -
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
sudo apt-get update

```

---

### Post by MedianMajik on 2009-02-19
Thanks, that solved my sources list problem.  I've saved that method for future use.  Got any ideas about why my upgrades are still being held back?

---

### Post by drs305 on 2009-02-19
One option is to run the "dist-update" option of apt-get. Since this is normally associated with upgrading to a newer version of ubuntu, run it first with the "-s" option to *simulate* what actions would be taken. You should see some upgrades, including possibly a kernel update (since that was on your list) but the kernel should still be 2.6.24-XX and NOT 2.6.27-XX, which is the intrepid kernel.

```
sudo apt-get update
sudo apt-get -s dist-upgrade
```

Once you are satisfied with what the command will do, run it again without the "-s" option.

---

### Post by MedianMajik on 2009-02-20
Thanks a ton.  That fixed my update issues.  Now I seem to be getting random errors from Firefox every couple hours that say things like:

carnot.physics.buffalo.edu:443 uses an invalid security certificate.
The certificate is not trusted because the issuer certificate is unknown.
(Error code: sec_error_unknown_issuer)

---

### Post by forger on 2009-02-20
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

---

### Post by MedianMajik on 2009-02-20
Thank you Forger.  You've both really helped me out!  Problems solved.

---

### Post by MedianMajik on 2009-02-21
Things seem to have upgraded.  Only error I'm getting is from Deluge.  
sudo apt-get -f install isn't doing the trick though it is recommended

E: /var/cache/apt/archives/deluge-core_1.1.3+dfsg-1~hardy2_all.deb: trying to overwrite `/usr/share/man/man1/deluged.1.gz', which is also in package deluge-torrent-common
E: /var/cache/apt/archives/deluge-common_1.1.3+dfsg-1~hardy2_all.deb: trying to overwrite `/usr/share/man/man1/deluge.1.gz', which is also in package deluge-torrent-common
E: /var/cache/apt/archives/deluge_1.1.3+dfsg-1~hardy2_all.deb: trying to overwrite `/usr/share/pixmaps/deluge.xpm', which is also in package deluge-torrent-common

---

### Post by drs305 on 2009-02-21
Try reinstalling deluge:
```

sudo apt-get install --reinstall deluge-torrent deluge-torrent-comment

```

---

### Post by MedianMajik on 2009-02-21
> **drs305 said:**
> Try reinstalling deluge:
```

sudo apt-get install --reinstall deluge-torrent deluge-torrent-comment

```Syaptic is reporting ' Error: BrokenCount > 0'

medianmajik@medianmajik-desktop:~$ sudo apt-get install --reinstall deluge-torrent deluge-torrent-comment
[sudo] password for medianmajik: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deluge-torrent-comment
medianmajik@medianmajik-desktop:~$ sudo apt-get install deluge-torrent-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
deluge-torrent-common is already the newest version.
deluge-torrent-common set to manually installed.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  deluge-torrent: Depends: deluge but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
medianmajik@medianmajik-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-setuptools python-json python-openssl libboost-date-time1.34.1
  deluge-torrent-common python-pyopenssl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  deluge deluge-common deluge-core
The following NEW packages will be installed:
  deluge deluge-common deluge-core
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1709kB of archives.
After this operation, 7090kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 157953 files and directories currently installed.)
Unpacking deluge-core (from .../deluge-core_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge-core_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/deluged.1.gz', which is also in package deluge-torrent-common
Unpacking deluge-common (from .../deluge-common_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge-common_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/deluge.1.gz', which is also in package deluge-torrent-common
Unpacking deluge (from .../deluge_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
 trying to overwrite `/usr/share/pixmaps/deluge.xpm', which is also in package deluge-torrent-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/deluge-core_1.1.3+dfsg-1~hardy2_all.deb
 /var/cache/apt/archives/deluge-common_1.1.3+dfsg-1~hardy2_all.deb
 /var/cache/apt/archives/deluge_1.1.3+dfsg-1~hardy2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by drs305 on 2009-02-21
Spellchecker error: comment is supposed to be common but you figured that out I see. Sorry.
```
sudo apt-get install --reinstall deluge-torrent deluge-torrent-common
```

Added:
You could try renaming the files(s) it won't allow you to overwrite, for whatever reason. Example:
```

sudo mv /usr/share/man/man1/deluge.1.gz /usr/share/man/man1/deluge.1.old.gz
sudo mv /usr/share/pixmaps/deluge.xpm /usr/share/pixmaps/deluge.old.xpm

```

---

### Post by MedianMajik on 2009-02-24
I used those two commands to move parts of deluge.  Still getting the same errors when running
$ Sudo apt-get -f install

medianmajik@medianmajik-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  deluge-torrent: Depends: deluge but it is not installed
E: Unmet dependencies. Try using -f.
medianmajik@medianmajik-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-setuptools python-json python-openssl libboost-date-time1.34.1
  deluge-torrent-common python-pyopenssl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  deluge deluge-common deluge-core
The following NEW packages will be installed:
  deluge deluge-common deluge-core
0 upgraded, 3 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/1709kB of archives.
After this operation, 7090kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 157953 files and directories currently installed.)
Unpacking deluge-core (from .../deluge-core_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge-core_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/deluged.1.gz', which is also in package deluge-torrent-common
Unpacking deluge-common (from .../deluge-common_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge-common_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/deluge.1.gz', which is also in package deluge-torrent-common
Unpacking deluge (from .../deluge_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
 trying to overwrite `/usr/share/pixmaps/deluge.xpm', which is also in package deluge-torrent-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/deluge-core_1.1.3+dfsg-1~hardy2_all.deb
 /var/cache/apt/archives/deluge-common_1.1.3+dfsg-1~hardy2_all.deb
 /var/cache/apt/archives/deluge_1.1.3+dfsg-1~hardy2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

-----------------------------------------------------
So, I used Synaptic to remove the broken package Deluge-torrent and downloaded the deb of Deluge 1.1.3 from GetDeb.  It installed and after I updated via the command line I got the following

medianmajik@medianmajik-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-setuptools python-json python-openssl libboost-date-time1.34.1
  deluge-torrent-common python-pyopenssl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
medianmajik@medianmajik-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  language-pack-en language-pack-gnome-en libgnutls13
  linux-restricted-modules-common nvidia-glx-new
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9953kB of archives.
After this operation, 500kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main language-pack-en 1:8.04+20090212 [192kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main language-pack-gnome-en 1:8.04+20090212 [15.3kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main libgnutls13 2.0.4-1ubuntu2.5 [344kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted linux-restricted-modules-common 2.6.24.16-24.57 [29.1kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted nvidia-glx-new 169.12+2.6.24.16-24.57 [9372kB]
Fetched 9953kB in 10s (937kB/s)                                                
(Reading database ... 157948 files and directories currently installed.)
Preparing to replace language-pack-en 1:8.04+20090105.1 (using .../language-pack-en_1%3a8.04+20090212_all.deb) ...
Unpacking replacement language-pack-en ...
Replacing files in old package language-pack-en-base ...
Preparing to replace language-pack-gnome-en 1:8.04+20090105.1 (using .../language-pack-gnome-en_1%3a8.04+20090212_all.deb) ...
Unpacking replacement language-pack-gnome-en ...
Replacing files in old package language-pack-gnome-en-base ...
Preparing to replace libgnutls13 2.0.4-1ubuntu2.4 (using .../libgnutls13_2.0.4-1ubuntu2.5_amd64.deb) ...
Unpacking replacement libgnutls13 ...
Preparing to replace linux-restricted-modules-common 2.6.24.16-23.56 (using .../linux-restricted-modules-common_2.6.24.16-24.57_all.deb) ...
Unpacking replacement linux-restricted-modules-common ...
Preparing to replace nvidia-glx-new 169.12+2.6.24.16-23.56 (using .../nvidia-glx-new_169.12+2.6.24.16-24.57_amd64.deb) ...
Unpacking replacement nvidia-glx-new ...
Setting up language-pack-en (1:8.04+20090212) ...
Setting up language-pack-gnome-en (1:8.04+20090212) ...
Setting up libgnutls13 (2.0.4-1ubuntu2.5) ...

Setting up linux-restricted-modules-common (2.6.24.16-24.57) ...

Setting up nvidia-glx-new (169.12+2.6.24.16-24.57) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
medianmajik@medianmajik-desktop:~$ deluge
The program 'deluge' is currently not installed.  You can install it by typing:
sudo apt-get install deluge-torrent
bash: deluge: command not found
medianmajik@medianmajik-desktop:~$ sudo apt-get install deluge-torrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-setuptools python-json python-openssl libboost-date-time1.34.1
  deluge-torrent-common python-pyopenssl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  deluge deluge-common deluge-core
The following NEW packages will be installed:
  deluge deluge-common deluge-core deluge-torrent
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1732kB of archives.
After this operation, 7176kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 157948 files and directories currently installed.)
Unpacking deluge-core (from .../deluge-core_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge-core_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/deluged.1.gz', which is also in package deluge-torrent-common
Unpacking deluge-common (from .../deluge-common_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge-common_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/deluge.1.gz', which is also in package deluge-torrent-common
Unpacking deluge (from .../deluge_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
 trying to overwrite `/usr/share/pixmaps/deluge.xpm', which is also in package deluge-torrent-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking deluge-torrent (from .../deluge-torrent_1.1.3+dfsg-1~hardy2_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/deluge-core_1.1.3+dfsg-1~hardy2_all.deb
 /var/cache/apt/archives/deluge-common_1.1.3+dfsg-1~hardy2_all.deb
 /var/cache/apt/archives/deluge_1.1.3+dfsg-1~hardy2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by forger on 2009-02-26
Try with aptitude:
```
sudo aptitude purge deluge-torrent-common
sudo aptitude -f install
```

or:
```
sudo aptitude purge deluge-core deluge-common deluge deluge-torrent-common
sudo aptitude install deluge
```

---

### Post by MedianMajik on 2009-02-26
> **forger said:**
> Try with aptitude:
```
sudo aptitude purge deluge-torrent-common
sudo aptitude -f install
```Thanks!  This fixed my problem.  How does aptitude differ from Synaptic?  Does it lack a source.list?  Just wondering why Synaptic is so popular if Aptitude does the job.

---

### Post by forger on 2009-02-26
I just followed the errors:
> Unpacking deluge-core (from .../deluge-core_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge-core_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
trying to overwrite `/usr/share/man/man1/deluged.1.gz', **which is also in package deluge-torrent-common**
Unpacking deluge-common (from .../deluge-common_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge-common_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
trying to overwrite `/usr/share/man/man1/deluge.1.gz', **which is also in package deluge-torrent-common**
Unpacking deluge (from .../deluge_1.1.3+dfsg-1~hardy2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/deluge_1.1.3+dfsg-1~hardy2_all.deb (--unpack):
trying to overwrite `/usr/share/pixmaps/deluge.xpm', **which is also in package deluge-torrent-common**
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking deluge-torrent (from .../deluge-torrent_1.1.3+dfsg-1~hardy2_all.deb) ...
Errors were encountered while processing:
/var/cache/apt/archives/deluge-core_1.1.3+dfsg-1~hardy2_all.deb
/var/cache/apt/archives/deluge-common_1.1.3+dfsg-1~hardy2_all.deb
/var/cache/apt/archives/deluge_1.1.3+dfsg-1~hardy2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

It was logical that deluge-torrent-common is creating problems, that's why by removing/purging it you allow to the packages to be installed correctly. :)

aptitude is generally better in handling dependencies and providing various solutions, for which you choose yes ("y") or no ("n") or quit ("q").

---

### Post by MedianMajik on 2009-02-26
> **forger said:**
> aptitude is generally better in handling dependencies and providing various solutions, for which you choose yes ("y") or no ("n") or quit ("q").

Interesting, because I removed it via broken packages listing in Synaptic and ended up with the same error after re-installation despite running ```
sudo apt-get -f install
```

---

### Post by forger on 2009-02-27
I don't know, maybe aptitude favours new packages, whereas synaptic probably favours packages from ubuntu archives. It's really hard to say

---

### Post by MedianMajik on 2009-03-29
I upgraded to 8.10 and now I'm getting 404 errors.

W: Failed to fetch [http://ubuntu.tribler.org/dists/intrepid/main/binary-amd64/Packages.gz](http://ubuntu.tribler.org/dists/intrepid/main/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/stevenharperuk/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/stevenharperuk/ubuntu/dists/intrepid/main/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/stevenharperuk/ubuntu/dists/intrepid/restricted/binary-amd64/Packages.gz](http://ppa.launchpad.net/stevenharperuk/ubuntu/dists/intrepid/restricted/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/stevenharperuk/ubuntu/dists/intrepid/universe/binary-amd64/Packages.gz](http://ppa.launchpad.net/stevenharperuk/ubuntu/dists/intrepid/universe/binary-amd64/Packages.gz)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/stevenharperuk/ubuntu/dists/intrepid/multiverse/binary-amd64/Packages.gz](http://ppa.launchpad.net/stevenharperuk/ubuntu/dists/intrepid/multiverse/binary-amd64/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by drs305 on 2009-03-29
MedianMajik,

The stevenharperuk server doesn't currently contain files for intrepid. It looks like the ubuntu.tribler.org server is not working if there is such a place. 

You can change servers or deselect these to get the rest of your updates. Untick them in synaptic, repositories, third-party software or manually edit your /etc/apt/sources.list and remove them or place a comment symbol at the start of each line that references the above servers.

---

### Post by MedianMajik on 2009-03-30
Thanks for the fast response.  I've fixed my sources list and I'm now up to date with all my software via synaptic. 
  I'm having problems with the internet.  Firefox is really slow since the update to 8.10.  I'm using a broadcom wireless g card, which hasn't given me trouble in the past.

---

