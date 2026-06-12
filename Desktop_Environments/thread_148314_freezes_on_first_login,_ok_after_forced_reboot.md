---
title: "freezes on first login, ok after forced reboot"
date: 2006-03-21
forum: Desktop Environments
---

### Post by ACiDiC74 on 2006-03-21
I have what seems to be a strange problem. Every single day I turn my computer on, wait for the log in screen, enter my password, and KDE starts to load. Once it gets to the fourth step (loading desktop) the computer completely freezes, neither the keyboard nor mouse respond, and the screen stays loading forever (I tried waiting over a half hour once)

I hit reset on my computer, and allow the computer to reboot, and then I can log in and everything loads ok.

I recently tried installing Gnome to see that would be better, but that just freezes before any kind of splash screen comes up at all.

Does anyone have any suggestions on where to begin on figuring out this problem. I don't see anything unusual in dmesg, and tried searching the logs that change for the day, but no errors seem to be written to them. I'm not new to linux, but I am new to Kubuntu and never had to deal with a problem like this before.

Hopefully someone can lead me to an answer because it's anoying having to wait for Linux to start up twice everytime, plus I don't see how forcing the computer to restart can be good for my harddrives.

thanks for any help.

---

### Post by stefanr on 2006-03-23
Hi,

Strange behaviour, I must say. There might be hints to this in a file .xsession-errors in your home directory, but this gets overwritten the next time you login. Try retrieving it (i.e. make a copy with a different name) in a terminal logon using ctrl+alt+f1. Do this after a 'crash', but before you log on the second time. Also, try just restarting the xserver instead of rebooting with ctrl+alt+backspace.

good luck!

---

