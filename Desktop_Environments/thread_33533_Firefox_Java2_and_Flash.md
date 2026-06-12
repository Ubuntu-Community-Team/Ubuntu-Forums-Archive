---
title: "Firefox Java2 and Flash"
date: 2005-05-11
forum: Desktop Environments
---

### Post by shanghaipi on 2005-05-11
Alright, I tried installing flash-mozilla from the ubuntu guide and got this:
tj@kubuntu:~$ sudo apt-get install flashplayer-mozilla
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla

I'm not certain what that means, but I have enabled all the repositires via the ubuntu guide.  I also followed all the directions for the jave2 runtime environment installation and nothing.  What should I do?  Reinstall firefox?  Is it corrupt?  I'm at a brickwall.  Any help would be much appreciated.

---

### Post by F for Fragging on 2005-05-11
[QUOTE=shanghaipi]Alright, I tried installing flash-mozilla from the ubuntu guide and got this:
tj@kubuntu:~$ sudo apt-get install flashplayer-mozilla
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla

I'm not certain what that means, but I have enabled all the repositires via the ubuntu guide.  I also followed all the directions for the jave2 runtime environment installation and nothing.  What should I do?  Reinstall firefox?  Is it corrupt?  I'm at a brickwall.  Any help would be much appreciated.[/QUOTE]
 If APT can't find it it can only mean one thing, IMO, and that is that you haven't added your repo's correctly, or that you didn't update package info.

Read it again:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Especially "sudo apt-get update" is important. Did you do that?

---

### Post by Zelut on 2005-05-11
You say you tried:

sudo apt-get install flashplayer-mozilla

and it tells you that it can't find the package?  That's odd.  Here, try this.  Its the ubuntuaddon pack which is a script that runs those listed on the guide.  Its really fast and easy & has made my life a lot easier.

[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

there is a .zip file on that page that includes all the packages listed on the ubuntuguide.org.  You just download it, unpack the .zip to a folder & run 'sudo sh ubuntuaddon.sh' and you're there.  (It will prompt you for each package with a Y/n/q)

---

### Post by shanghaipi on 2005-05-11
I will check my repositories when I get home from school and I'm downloading that add-on zip.  I just tried to upgrade my packets via synaptic and I got this error message when updating kdelibs:

E: /var/cache/apt/archives/kdelibs-data_40x0.0007fbfffd58p-10223.4.0-0ubuntu3.1_all.deb:  trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf

what is E:/

I don't think I have an E drive.

---

### Post by Zelut on 2005-05-11
> E: /var/cache/apt/archives/kdelibs-data_40x0.0007fbfffd58p-10223.4.0-0ubuntu3.1_all.deb: trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf

I dont think that refers to an E: drive as you would think of it in Windows.  I think that is just a notice of Error.  I'm not familiar enough with how apt-get works to decode that for you unfortunately...  

I'm guessing that the file that its trying to get & install is in the knetworkconf lib so its conflicting...

---

