---
title: "Dell inspiron 6400 E1505 issues"
date: 2007-06-24
forum: Dell  Ubuntu Support
---

### Post by jpbefx on 2007-06-24
I have the ubuntu 6.??? and I want to upgrade to the feisty fawn, I ran 'sudo apt-get update, and upgrades, did this do it for me? the desktop looks the same.  I also have downloaded beryl 0.2.0, and 0.2.1 and when I run 'sudo apt-get install beryl-core-0.2.1, and .0 it tells me this
[COLOR="Blue"]jpbefx@jpbefx-laptop:~$ sudo apt-get install beryl-core-0.2.0
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package beryl-core-0.2.0
jpbefx@jpbefx-laptop:~$[/COLOR]

I don't know what is going on, and I just want to get past this installation stage so I can move on the biger and better things, anyone who can help??

---

### Post by mhu on 2007-06-24
try sudo apt-get dist-upgrade

---

### Post by Tethtibis on 2007-06-26
i think the problem is that you have 6.06. the stable version, you cannot upgrade from 6.06 to 7.04. 7.04 is the unstable version, and you can only upgrade to it from 6.10 and up. you might try downloading the 7.04 cd and reinstalling. plus, Beryl is only part of 6.10 through 7.04. it won't be in the 6.06 repository, that is why you are getting the error about not being able to find it.

---

### Post by jpbefx on 2007-06-27
> **jpbefx said:**
> I have the ubuntu 6.??? and I want to upgrade to the feisty fawn, I ran 'sudo apt-get update, and upgrades, did this do it for me? the desktop looks the same.  I also have downloaded beryl 0.2.0, and 0.2.1 and when I run 'sudo apt-get install beryl-core-0.2.1, and .0 it tells me this
[COLOR="Blue"]jpbefx@jpbefx-laptop:~$ sudo apt-get install beryl-core-0.2.0
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package beryl-core-0.2.0
jpbefx@jpbefx-laptop:~$[/COLOR]

I don't know what is going on, and I just want to get past this installation stage so I can move on the biger and better things, anyone who can help??

I got rid of the 6.04 and am now trying to install 7.10 and gusty gibbon, neither one will load due to an error bcm43xx error, the xserver is not loading, it thinks I am using the wrong graphics driver.  I did the [FONT="Courier New"]_sudo dpkg-reconfigure -phigh xserver-xorg_[/FONT] and it let me choose ati as my driver. It then asked me what resolution and I chose the last three (basic, or master settings). I then went back to the[FONT="Courier New"]_ ubuntu@ubuntu:~$_[/FONT] and I restarted. it didn't work. I tried the [FONT="Courier New"]_sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf_backup_[/FONT] and it told me that there is no such place to save it to.  I then tried the [FONT="Courier New"]_sudo mv /etc/x11/xorg.conf /etc/x11/xorg.conf.orig_[/FONT] and it told me that there is no such directory as [FONT="Courier New"]_/etc/x11/xorg.conf_[/FONT] I've tried these different commands in soooo many different orders and nothing is working.  I'm also a noob and wonder if there is something else I can do to solve my issue I have the ati mobility radeon x1300 card it shares it's ram with the system, and has 128 of it's own I think or 64 of it's own (can't remember) I can load 6.04 on my laptop but can't get the beryl emrald on it afterwards, and that's what I'm originally aiming for.  if there is anything I can do please help. I suck and can't figure it out. I've also tried the live cd of gusty, and the live dvd of feisty. I've burned like 5 cd's and 1 dvd. I'm so lost there has to be a way. Sorry for such a long BLOG and thank you everyone.

---

### Post by jpbefx on 2007-06-27
I just put this on there so there is a open envelope.  My actual issue is posted above.

---

