---
title: "Help! Experiencing major OS crashes after a failed update"
date: 2009-05-18
forum: General Help
---

### Post by senor.ehlert on 2009-05-18
I am still fairly new to ubuntu and have only been using ubuntu occasionally. I recently started using it as my primary OS and all has been fine until very recently. I followed this tutorial: [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683") and in the process I followed the steps in part one and added more software sources. All was fine until I noticed that new updates were available after I added these new sources. I then downloaded the updates and there was a problem while installing the new updates which caused my the OS to crash.

> rick@rick-laptop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  smbclient: Depends: samba-common (= 3.0.28a-1ubuntu4.8) but 3.0.28a-1ubuntu4.7 is installed
E: Unmet dependencies. Try using -f.
rick@rick-laptop:~$ sudo 
rick@rick-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libswt3.2-gtk-java libaccess-bridge-java
  libseda-java libcommons-cli-java rhino libcommons-lang-java
  libswt3.2-gtk-jni linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  samba-common
The following packages will be upgraded:
  samba-common
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/2840kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 162247 files and directories currently installed.)
Preparing to replace samba-common 3.0.28a-1ubuntu4.7 (using .../samba-common_3.0.28a-1ubuntu4.8_i386.deb) ...
Unpacking replacement samba-common ...
dpkg: error processing /var/cache/apt/archives/samba-common_3.0.28a-1ubuntu4.8_i386.deb (--unpack):
 unable to install new version of `./usr/share/man/man5/lmhosts.5.gz': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/samba-common_3.0.28a-1ubuntu4.8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rick@rick-laptop:~$ 


I really have no idea how to fix this and could really use some help. This is all the info I have right now. If you need to know anything else to help me just let me know and I will try to get it for you.

---

### Post by gettinoriginal on 2009-05-18
You can always remove the offending packages and then reinstall.
```
sudo apt-get remove --purge samba-common
```
then
```
sudo apt-get autoclean
```
then
install samba-common from Synaptic, as 2:3.3.2 is the most stable for Ubuntu, see this link:
[http://packages.ubuntu.com/ko/hardy-updates/amd64/samba-common/download](http://packages.ubuntu.com/ko/hardy-updates/amd64/samba-common/download)
Hope this helps  :p

---

### Post by stefangr1 on 2009-05-18
What specific distribution of Ubuntu do you have?

Looking at the information above you are using kernel 2.6.24-19, which was included with Ubuntu 8.04 - Hardy. The repositories on the site you are referring to, on the other hand, are corresponding to Ubuntu 9.04 - Jaunty. That explains (if this is indeed the case) why so much updates were found and why you're now experiencing crashes.

What I would recommend in THAT case is (1) try a full dist upgrade to Jaunty, and if that doesn't work (2) do a fresh install.

Can you post your sources.list to see if things are indeed mixed up?

---

### Post by senor.ehlert on 2009-05-18
I tried to remove it, but I can't for some reason. I get this error:
> rick@rick-laptop:~$ sudo apt-get remove --purge samba-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  smbclient: Depends: samba-common (= 3.0.28a-1ubuntu4.8) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I am running Hardy, but the tutorial that I followed said that the sources would be fine with all versions of ubuntu. How do I get the sources list?

---

### Post by s.fox on 2009-05-18
Hi,

The sources list is located here in Hardy:

```
/etc/apt/sources.list
```

Hope this helps.

-Ash R

---

### Post by senor.ehlert on 2009-05-18
Ok here is the info. I uploaded the file and I have a screen shot of it.

---

### Post by senor.ehlert on 2009-05-19
Is this the info you needed? Do you need anything else?

---

### Post by stefangr1 on 2009-05-19
> **senor.ehlert said:**
> Is this the info you needed? Do you need anything else?

Yes, it is. However, there's nothing wrong with them...

---

### Post by gettinoriginal on 2009-05-19
Go to synaptic, quick search for "smbclient" and check for installation, then quick search for "samba-common" and make sure it is also checked for installation.  If you right click any app in synaptic, and choose properties, it will list all dependencies for that app.
[ATTACH]114316[/ATTACH]

---

### Post by senor.ehlert on 2009-05-19
Well, my computer is no longer saying that there are broken dependencies. But here is a screen shot of the samba dependencies anyways. I don't know what I did (if anything) to fix the dependencies.

However, the samba update is still not installing along with three other updates. All of them fail and give the same reason for failing.

> E: /var/cache/apt/archives/samba-common_3.0.28a-1ubuntu4.8_i386.deb: unable to install new version of `./usr/share/man/man5/lmhosts.5.gz'
E: /var/cache/apt/archives/xserver-xorg-video-intel_2%3a2.2.1-1ubuntu13.9_i386.deb: unable to install new version of `./usr/share/man/man4/intel.4.gz'
E: /var/cache/apt/archives/mencoder_2%3a1.0~rc2-0ubuntu13.1+medibuntu1_i386.deb: unable to install new version of `./usr/share/man/man1/mencoder.1.gz'
E: /var/cache/apt/archives/mplayer_2%3a1.0~rc2-0ubuntu13.1+medibuntu1_i386.deb: unable to install new version of `./usr/lib/mime/packages/mplayer'

I also attached a screen shot of the "more details" tab after the updates all failed. My OS seems a lot more stable now, but it still froze on me once.

So basically is there anyway for me to install these updates? If not, what should I do?

Thanks for all the help you guys have been giving me. Your extremely helpful.


***Edit:***

I also tried to uninstall samba, but it won't let me and gives me an error

> rick@rick-laptop:~$ sudo apt-get remove --purge samba-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libswt3.2-gtk-java libaccess-bridge-java
  libseda-java libcommons-cli-java rhino libcommons-lang-java
  libswt3.2-gtk-jni linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  samba-common*
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
rick@rick-laptop:~$ 


---

### Post by gettinoriginal on 2009-05-19
Aha, I think I see the problem.  Go to software sources, update tab, and uncheck "proposed updates"
[ATTACH]114363[/ATTACH]

---

### Post by senor.ehlert on 2009-05-19
Thank you very much! That completely fixed my problem with samba. :D

However, for some reason it still won't let me install mplayer and mencoder, but that is a much secondary problem compared to the problem which I had.

If you have any idea how to fix the problem with mplayer and mencoder that would be great, but it isn't my primary concern right now.

Thank You all so much for your help. People like you are the reason that Ubuntu is such a great community.

---

### Post by gettinoriginal on 2009-05-19
You can always remove the offending packages and then reinstall.

```
sudo apt-get remove --purge mplayer
```
```
sudo apt-get remove --purge mencoder
```
then
```
sudo apt-get autoclean
```
```
sudo apt-get install mplayer
```
```
sudo apt-get install mencoder
```

---

### Post by senor.ehlert on 2009-05-19
I have tried uninstalling and reinstalling them, but I have been getting multiple errors.  

> rick@rick-laptop:~$ sudo apt-get remove --purge mplayer
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
rick@rick-laptop:~$ sudo dpkg --configure -a
dpkg: unable to access dpkg status area: Read-only file system

What do I need to do to fix this?

---

### Post by senor.ehlert on 2009-05-19
Never mind. I figured out how to fix everything.

Thank you all for your help!

---

