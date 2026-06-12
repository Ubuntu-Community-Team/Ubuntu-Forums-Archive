---
title: "[SOLVED] Desktop Manager Not Loading"
date: 2007-07-14
forum: Desktop Environments
---

### Post by pgcrockhead on 2007-07-14
I am a beginner who thinks he may have broken his Ubuntu 7.04 installation.

I was learning about the X server and messing around with gdm, trying to see if I could remotely log into my desktop from my laptop. Both have the same version of Ubuntu. I forgot exactly what I changed last on my laptop, but now when I try to boot into Ubuntu, the splash screen shows up, and when it goes away, all I can see is a black screen where my mouse cursor is an X. I can move the mouse around, but other than that, I can do nothing.

I've looked around on other threads on this side where people are having similar problems, but nothing I have seen has helped. I've tried using ctrl+alt F1 to type some commands, but I'm so new to the CLI that I don't really know what I'm doing or what I need to do. I've also tried ctrl+alt backspace, and that only causes the black screen to flicker and bring me back to where I was. The only thing I think I know is that something is wrong with my desktop manager. Anyone want to help me get back to the normal login screen?

FYI: I dual boot my laptop with Windows XP using GRUB, but I haven't messed with XP for a long time and don't think that has anything to do with my problem.

Also, I will blindly use any commands that anyone tells me to use, but I would appreciate it if you explained exactly what various commands mean so I can learn a little more about the CLI.

Thanks!

---

### Post by pgcrockhead on 2007-07-15
Well, nobody is interested in helping me out, but never mind! I just figured it out.

For those of you who may have the same problem, it might be helpful to know that gdmsetup changes the /etc/X11/gdm/gdm.conf-custom file, which is read when Linux boots. If there is a problem with that file, gnome doesn't start up. So I used ctrl+alt F1 to get to a command line, and then renamed the file to Xgdm.conf-custom. That way, gdm isn't able to find a conf-custom file, so it defaults back to the gdm.conf file (which only has default values in it). Reboot, and it's fixed.

---

### Post by dasan on 2007-07-16
Thankssssssssss....................lott.........
i was having the same problem and it is solved.........:o
:guitar:

---

