---
title: "Problem apt-getting firefox."
date: 2005-07-14
forum: Desktop Environments
---

### Post by Evera on 2005-07-14
Here is my log.

brandon@BATTALION-DEBIANLINUX:~$ sudo apt-get install mozilla-firefox
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gcc-3.4-base gconf2 gnome-keyring gnome-mime-data libatk1.0-0 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libgconf2-4 libglade2-0
  libgnome-keyring0 libgnome2-0 libgnome2-common libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libpango1.0-0
  libpango1.0-common libstdc++6-0 shared-mime-info
Suggested packages:
  gnome-icon-theme ttf-thryomanes mozilla-firefox-gnome-support
  latex-xft-fonts xprt-xprintorg
Recommended packages:
  libatk1.0-data
The following NEW packages will be installed:
  gcc-3.4-base gconf2 gnome-keyring gnome-mime-data libatk1.0-0 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libgconf2-4 libglade2-0
  libgnome-keyring0 libgnome2-0 libgnome2-common libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libpango1.0-0
  libpango1.0-common libstdc++6-0 mozilla-firefox shared-mime-info
0 upgraded, 28 newly installed, 0 to remove and 36 not upgraded.
Need to get 0B/17.3MB of archives.
After unpacking 83.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
Selecting previously deselected package gcc-3.4-base.
(Reading database ... 59980 files and directories currently installed.)
Unpacking gcc-3.4-base (from .../gcc-3.4-base_3.4.3-9ubuntu4_amd64.deb) ...
Selecting previously deselected package libatk1.0-0.
Unpacking libatk1.0-0 (from .../libatk1.0-0_1.9.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgconf2-4.
Unpacking libgconf2-4 (from .../libgconf2-4_2.10.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgtk2.0-common.
Unpacking libgtk2.0-common (from .../libgtk2.0-common_2.6.4-0ubuntu3_all.deb) ...
Selecting previously deselected package libpango1.0-common.
Unpacking libpango1.0-common (from .../libpango1.0-common_1.8.1-0ubuntu2_amd64.deb) ...
Selecting previously deselected package libpango1.0-0.
Unpacking libpango1.0-0 (from .../libpango1.0-0_1.8.1-0ubuntu2_amd64.deb) ...
Selecting previously deselected package libgtk2.0-bin.
Unpacking libgtk2.0-bin (from .../libgtk2.0-bin_2.6.4-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libgtk2.0-0.
Unpacking libgtk2.0-0 (from .../libgtk2.0-0_2.6.4-0ubuntu3_amd64.deb) ...
Selecting previously deselected package gconf2.
Unpacking gconf2 (from .../gconf2_2.10.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package gnome-keyring.
Unpacking gnome-keyring (from .../gnome-keyring_0.4.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package gnome-mime-data.
Unpacking gnome-mime-data (from .../gnome-mime-data_2.4.2-1_all.deb) ...
Selecting previously deselected package libbonobo2-common.
Unpacking libbonobo2-common (from .../libbonobo2-common_2.8.1-2_amd64.deb) ...
Selecting previously deselected package libbonobo2-0.
Unpacking libbonobo2-0 (from .../libbonobo2-0_2.8.1-2_amd64.deb) ...
Selecting previously deselected package libglade2-0.
Unpacking libglade2-0 (from .../libglade2-0_1%3a2.5.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package shared-mime-info.
Unpacking shared-mime-info (from .../shared-mime-info_0.16-1_amd64.deb) ...
Selecting previously deselected package libgnomevfs2-common.
Unpacking libgnomevfs2-common (from .../libgnomevfs2-common_2.10.0-0ubuntu5_amd64.deb) ...
Selecting previously deselected package libgnomevfs2-0.
Unpacking libgnomevfs2-0 (from .../libgnomevfs2-0_2.10.0-0ubuntu5_amd64.deb) ...
Selecting previously deselected package libgnome2-common.
Unpacking libgnome2-common (from .../libgnome2-common_2.10.0-0ubuntu1_all.deb) ...
Selecting previously deselected package libgnome2-0.
Unpacking libgnome2-0 (from .../libgnome2-0_2.10.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgnomecanvas2-common.
Unpacking libgnomecanvas2-common (from .../libgnomecanvas2-common_2.10.0-0ubuntu1_all.deb) ...
Selecting previously deselected package libgnomecanvas2-0.
Unpacking libgnomecanvas2-0 (from .../libgnomecanvas2-0_2.10.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libbonoboui2-common.
Unpacking libbonoboui2-common (from .../libbonoboui2-common_2.8.1-1ubuntu1_all.deb) ...
Selecting previously deselected package libbonoboui2-0.
Unpacking libbonoboui2-0 (from .../libbonoboui2-0_2.8.1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libgnome-keyring0.
Unpacking libgnome-keyring0 (from .../libgnome-keyring0_0.4.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgnomeui-common.
Unpacking libgnomeui-common (from .../libgnomeui-common_2.10.0-0ubuntu1_all.deb) ...
Selecting previously deselected package libgnomeui-0.
Unpacking libgnomeui-0 (from .../libgnomeui-0_2.10.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libstdc++6-0.
Unpacking libstdc++6-0 (from .../libstdc++6-0_3.4.3-9ubuntu4_amd64.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/libstdc++6-0_3.4.3-9ubuntu4_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/libstdc++6-0/changelog.Debian.gz')
Selecting previously deselected package mozilla-firefox.
Unpacking mozilla-firefox (from .../mozilla-firefox_1.0.2-0ubuntu5.3_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6-0_3.4.3-9ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
brandon@BATTALION-DEBIANLINUX:~$ sudo apt-get install mozilla-firefox
Reading package lists... Done
Building dependency tree... Done
mozilla-firefox is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mozilla-firefox: Depends: libstdc++6-0 (>= 3.4.3-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
brandon@BATTALION-DEBIANLINUX:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libstdc++6-0
The following NEW packages will be installed:
  libstdc++6-0
0 upgraded, 1 newly installed, 0 to remove and 36 not upgraded.
27 not fully installed or removed.
Need to get 0B/324kB of archives.
After unpacking 1036kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 61123 files and directories currently installed.)
Unpacking libstdc++6-0 (from .../libstdc++6-0_3.4.3-9ubuntu4_amd64.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/libstdc++6-0_3.4.3-9ubuntu4_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/libstdc++6-0/changelog.Debian.gz')
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6-0_3.4.3-9ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Will someone tell me what to do? ^^;; thanks!~

UPDATE: I forgot to include what happened if I ran firefox. Here it is!
brandon@BATTALION-DEBIANLINUX:~/Desktop/tiblit-1.2$ sudo -H  firefox
/usr/lib/mozilla-firefox/firefox-bin: error while loading shared libraries: libstdc++.so.60: cannot open shared object file: No such file or directory

---

### Post by f1dave on 2005-07-15
Can you please post what repositories you are using? Thanks.

---

### Post by Evera on 2005-07-15
[QUOTE=f1dave]Can you please post what repositories you are using? Thanks.[/QUOTE]
 I'm not exactly sure how to check. Will you tell me how? ^_^;;

---

### Post by Lord Illidan on 2005-07-15
Type in 

vi /etc/apt/sources.list and give us the contents of that folder. Don't edit it or anything yet..

---

### Post by skyboy on 2005-07-15
and please tell us you are using a amd64 system.
what is your configuration ? because everything you tru to install is for amd64 system, so just in cae you have downloaded a wrong source.list

---

### Post by geearf on 2005-07-15
you could try 
apt-get clean
apt-get check
apt-get -f install
and see if it helps.

---

### Post by Evera on 2005-07-15
[QUOTE=geearf]you could try 
apt-get clean
apt-get check
apt-get -f install
and see if it helps.[/QUOTE]
 Oh, yeah, I forgot to mention I'm using the 64-bit version.. sorry ^_^;;
Here's my repositories:
eb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


And this is what happened when I tried qeearf's suggestion
brandon@BATTALION-DEBIANLINUX:~$ sudo apt-get clean
brandon@BATTALION-DEBIANLINUX:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  mozilla-firefox: Depends: libstdc++6-0 (>= 3.4.3-1) but it is not installed
E: Unmet dependencies. Try using -f.
brandon@BATTALION-DEBIANLINUX:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libstdc++6-0
The following NEW packages will be installed:
  libstdc++6-0
0 upgraded, 1 newly installed, 0 to remove and 36 not upgraded.
27 not fully installed or removed.
Need to get 324kB of archives.
After unpacking 1036kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libstdc++6-0 3.4.3-9ubuntu4 [324kB]
Fetched 324kB in 4s (70.4kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/libstdc++6-0_3.4.3-9ubuntu4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/libstdc++6-0_3.4.3-9ubuntu4_amd64.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by geearf on 2005-07-15
hmm, it might be an internal problem on the repo,

i'll check later on an ubuntu 64 to see if i get the same problem if you wish.

---

### Post by Evera on 2005-07-15
[QUOTE=geearf]hmm, it might be an internal problem on the repo,

i'll check later on an ubuntu 64 to see if i get the same problem if you wish.[/QUOTE]
 ah, that would be great. Thanks!

---

### Post by geearf on 2005-07-15
Well i've tried with the comp at work, i did not uninstall the file cause i cannot really mess the comp right now, but i reinstalled it without any problem on a ubuntu 64.
this is my version 3.4.3-9ubuntu4

---

### Post by Evera on 2005-07-15
[QUOTE=geearf]Well i've tried with the comp at work, i did not uninstall the file cause i cannot really mess the comp right now, but i reinstalled it without any problem on a ubuntu 64.
this is my version 3.4.3-9ubuntu4[/QUOTE]

I'm using Kubuntu 5.04 Hoary if that makes a difference.
 Hmm, how would I uninstall it?

---

### Post by geearf on 2005-07-16
I'm also using Hoary 5.04.

---

### Post by Evera on 2005-07-16
[QUOTE=geearf]I'm also using Hoary 5.04.[/QUOTE]
 Hmm, that's weird. o-o;; I don't know what's wrong.. I tried updating my packages and the same problem hit me with 3 different non-essential packages.. strange..

---

### Post by geearf on 2005-07-16
i can't help you on that sorry :(

---

### Post by ykpaiha on 2005-07-16
I had quite often some prob with the us repos ie : some package not found or missings or worst...
Try to remove reference to "us" from your repos i worked fine for me
in a console:
sudo gedit /etc/apt/sources.list

In you list remove all "us" it must look like this:(exemple)

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
save it

then 
sudo apt-get update
then .....your usual way

let me know if it worked fine as for me

---

### Post by rogerhc on 2005-07-16
Why all the gnome dependencies for this? We are Kubuntu users in this area of the forum, right? Does anyone know why apt-getting firefox brings any gnome dependencies with it for us Kubuntu users?

Is there a way to avoid that cruft?

My install is Kubuntu 5.04 AMD64 (and yes my CPU is an AMD64)

Thanks,

Roger

---

### Post by geearf on 2005-07-16
good question.

Maybe because of some gtk libs used in gnome ?

---

### Post by Gezzer on 2005-07-17
why not download FF 1.0.5 from mozilla and install it as a stand alone on the /home partition

thats what i have done with FF & TB ...

---

