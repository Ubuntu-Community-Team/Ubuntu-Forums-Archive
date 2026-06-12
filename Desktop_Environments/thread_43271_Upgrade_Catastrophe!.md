---
title: "Upgrade Catastrophe!"
date: 2005-06-21
forum: Desktop Environments
---

### Post by radl33t on 2005-06-21
I attempted to upgrade my Hoary 5.04 install. Summary of events:

1 I ran Synaptic smart upgrade; this included the nvidia module.

2 On the reboot, X failed to start because of a driver mismatch. 

3 I d/led and installed the matching nvidia driver file.

4 The normal gui loaded with the first reboot.

5 Following the first reboot, X  fails to start with: 

[FONT=Fixedsys]Skipping "/usr/X11R6/lib/modules/libfb.a:fmbbx.o": No symbols found
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri
.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri
.a is unresolved!
XIO:	fatal IO error 104 (Connection reset by peer) on X server ":0.0"
	after 0 requests (0 known processed) with 0 events remaining.[/FONT]

I need help with this. I have no internet!

I run a nvidia geforce 5200 on a 15.4 wxga toshiba centrino laptop.

---

### Post by aglauser on 2005-06-21
> **radl33t]I attempted to upgrade my Hoary 5.04 install. Summary of events:

1 I ran Synaptic smart upgrade said:**
> Skipping "/usr/X11R6/lib/modules/libfb.a:fmbbx.o": No symbols found
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri
.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri
.a is unresolved!
XIO:	fatal IO error 104 (Connection reset by peer) on X server ":0.0"
	after 0 requests (0 known processed) with 0 events remaining.[/FONT]

I need help with this. I have no internet!

I run a nvidia geforce 5200 on a 15.4 wxga toshiba centrino laptop.


What happens if you try restarting using a 'failsafe' kernel?  I think this should be an option on the GRUB list when you boot.  It looks like you might be having a problem with framebuffers (libfb).  Mind you, this is just a guess based on the first error.

Another thing to try is to make sure that the 'Load DRI' option is commented out (or just not there) in your /etc/X11/xorg.conf file.

Sorry for lack of detail, don't have a Ubuntu box in front of me right now.

---

### Post by radl33t on 2005-06-21
I never got grub working on this laptop (with any distro) so I use Lilo instead with no failsafe option. =]

I attempted to uncomment the Load "dri" and it removed the getActiveScreen errors, but nothing else.

---

### Post by shakin on 2005-06-21
What was in your sources.list file when you did the upgrade?

---

### Post by radl33t on 2005-06-21
sources.list = places where I grab ubuntu packages? 

I added extra paths after reading some posts here, but that was before hoary was released. It is a 1 day turn around before I can provide that info, where is sources.list located?

---

### Post by cohort on 2005-06-21
[QUOTE=radl33t]It is a 1 day turn around before I can provide that info, where is sources.list located?[/QUOTE]
/etc/apt/sources.list

---

### Post by radl33t on 2005-06-22
I think I added some extra paths to download codecs? Regardless, package manager tells me a few are invalid on execution, but I haven't paid much attention to the warning.  I don't understand how this could be a problem?
I am super desperate I have a close deadline for stuff on my machine :o

/etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) hoary-backports main universe

---

### Post by jdong on 2005-06-22
[QUOTE=radl33t]I think I added some extra paths to download codecs? Regardless, package manager tells me a few are invalid on execution, but I haven't paid much attention to the warning.  I don't understand how this could be a problem?
I am super desperate I have a close deadline for stuff on my machine :o

/etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
[b]
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) hoary-backports main universe[/b][/QUOTE]

First, out the bolded lines. They're either known stability issues (debian-marillat) or deprecated (ubuntu-bp.sf.net).

Add what's shown at [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) . those are what I recommend.

Push forward again with **apt-get update && apt-get dist-upgrade** and see where you can get.

---

### Post by radl33t on 2005-06-22
I have a problem with internet :( My available wireless network requires I login through some html page. 

I might be able to go spend time at a coffee shop, but I have no idea how to manage wireless settings at the command prompt :\

I hooked up a wrapper that uses my intel 2200 xp drivers. I've never found good documentation for it. (yes I suck too)

---

### Post by radl33t on 2005-06-23
yeah, I failed getting net access for apt-get. I'm not sure if its ndiswrapper for the 2200, but this setup sucks. I can see wireless networks and set ssid, but it never picks up the AP (MAC anyways) so I can't pull an IP. 

This has been a problem with this wireless setup. campus wireless and my home network run fine, but anything public ( :mad: even open stuff I very with windows) don't seem to connect.


So much for getting my work done by fri :

---

### Post by radl33t on 2005-06-23
Updated sources.list and ran apt-get update and apt-get dist-upgrade.

Did some updating, did some upgrading, but the problem persists. Is there anything I can do to revert to a previous x/nvidia setup?

---

### Post by jdong on 2005-06-23
**sudo apt-get remove --purge nvidia-glx**
**sudo dpkg-reconfigure xserver-xorg**
**sudo apt-get install nvidia-glx**
**sudo nvidia-glx-config enable**

---

### Post by radl33t on 2005-06-23
okay.  I followed those steps and reverted back to the nvidia 7174 driver and it looks to be working. Thank you so much!

---

### Post by radl33t on 2005-06-23
okay I lied when I said it was fixed.

I executed your commands and attempted to startx. it told me I had a driver mismatch with API so I reverted back to the old nvidia driver. I ran a startx and it loaded up (in root). Since this happened last time, I rebooted to check for the error. I saw the nvidia logo load, assumed all was fine and shutdown before the gui loaded.
 :mad: 
I returned home to see that the error was still present from my cold boot. I don't know how startx after making those changes is different from a cold boot. 

help! wise ones (jdong)  :)

---

### Post by jdong on 2005-06-23
Ya sure you're booted up on the new 2.6.10 kernel?
Try **sudo apt-get install ubuntu-base ubuntu-desktop**

---

### Post by radl33t on 2005-06-24
nope totally unsure  :smile: 

I will try this command, erm Monday evening? Damn internet access. 

Thanks!

---

### Post by radl33t on 2005-06-28
I applied those commands. It said base & desktop were already the newest versions.

any help is appreciated. I have extremely limited internet access these days. hehe

---

### Post by radl33t on 2005-06-28
I found an xorg.conf from when this before all went down. I disabled glx and dri and it has booted up a few times under a few users.

I am still interested in a long term solution to this problem.

---

