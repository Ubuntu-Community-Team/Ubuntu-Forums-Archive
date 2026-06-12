---
title: "window and ubuntu"
date: 2008-07-08
forum: Forum Feedback &amp; Help
---

### Post by captain-von-stog on 2008-07-08
hello can any help me please ill start from the bottom

today i installed windows on my hard drive that also had ubuntu on it after i tryed to get into my ubuntu system and i cant get into it so i deleted my windows part and rebooted and now they nothing i cant get into ubuntu still unless i put my ubuntu disk and load it up from they i cant get into ubuntu

but thats really not the problem what is is that i cant get into my own part of ubuntu it says my password and username is incorrect but i know they right as i put it on paper by my desk just incase i forgot. 

but what i really dont understand is that only last week i had both windows and ubuntu on the same drive and i could get into the both of em so why cant i know. 

i really dont like windows but i have a part so i can play music and dvds as ubuntu wont play them and i cant be bothered to mess about trying to get ubuntu ton play them 

im looking for anyone with some simply answer to why this has happened

---

### Post by LaRoza on 2008-07-08
> **captain-von-stog said:**
> hello can any help me please ill start from the bottom

today i installed windows on my hard drive that also had ubuntu on it after i tryed to get into my ubuntu system and i cant get into it so i deleted my windows part and rebooted and now they nothing i cant get into ubuntu still unless i put my ubuntu disk and load it up from they i cant get into ubuntu


You'll have to give more information. Windows should be install first, because Windows doesn't dual boot easily (or at all) when it is being installed.

> 
i really dont like windows but i have a part so i can play music and dvds as ubuntu wont play them and i cant be bothered to mess about trying to get ubuntu ton play them 


That is easy to do. I suggest you use VLC to watch movies (and deal with any other troublesome media)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by tamoneya on 2008-07-08
when you installed windows it removed the GRUB the bootloader.  You can replace it with supergrub so that you no longer have to boot with the liveCD.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

As for your password I am not certain what happened to it.  As for a fix though I can help you out.  After restoring grub you should hit escape when GRUB loads and select ubuntu in recovery mode.  This will boot you to a root shell.  From here just type:```
passwd <username>
```Then enter your new password twice.  Note that <username> is the username you set up previously.

---

### Post by bobbob1016 on 2008-07-08
Installing Windows after you have Ubuntu is a bad idea.  Windows overwrites the MBR without asking.  This means it overwrites grub, and erases it.  Basically you need to repair grub after installing Windows after Ubuntu.  There are one or two things you need:
1) (If you want to have Windows installed dual-boot) Reinstall Windows if you want to keep it, make sure you still have Ubuntu installed.

2) Boot from an Ubuntu LiveCD and there is a way to repair grub, just search the forums for "fix grub" or "repair grub" or something, and follow those directions.

---

### Post by LaRoza on 2008-07-08
This forum isn't the place for this thread ("Forum Feedback and Help") but I am not going to move it until the OP replies.

The automatic PM's on moves have been broken (the developer of the plugin stopped working on it) and it is hard to find your own threads if they are moved.

---

