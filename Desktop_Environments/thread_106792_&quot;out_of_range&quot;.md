---
title: "&quot;out of range&quot;"
date: 2005-12-21
forum: Desktop Environments
---

### Post by kennethalan on 2005-12-21
I have just received my ubuntu discs in the mail.  I've been trying to boot up.

After a few minutes, I get a screeen than says  simply "out of range" , aithout any further explanation.


Anyone got an idea what this could mean.

I am really not a computer wiz, and any help would be greatly appreciated.

---

### Post by 23meg on 2005-12-21
Please give some info about your configuration. Can you boot into recovery mode?

---

### Post by aysiu on 2005-12-21
Does pressing control-alt-F1 bring you to a black screen with a white login prompt?

---

### Post by kennethalan on 2005-12-21
When this screen appears, the keyboard and the mouse are completely unresponsives.

I pushed the boot-up button on the computer, and I get a new screen with a lot of lines, and a last line "unbuntu@ubuntu:~$".

There I rest blocked again for a few minutes, the disc reader with the Ubuntu live disc opens up, and a few minutes later the a new message that says "take out the disc, close the disc reader and "enter" " or something to that effect.


I've got a cordless moouse, but normally it works (in windows).

---

### Post by aysiu on 2005-12-21
The screen appears and your *keyboard* doesn't respond? Whoa. Something's seriously wrong. The "out of range" usually means it's just a video resolution problem. I don't know why that should affect your keyboard...

---

### Post by 23meg on 2005-12-21
Can you boot into recovery mode? If so, type ```
nano /etc/default/bootlogd
```and edit the file to look like this```
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes
```Hit ctrl+x to exit, save the changes. Reboot to reproduce the failure, and look into your /var/log/bootlog file for errors, and if possible, post it here as an attachment.

---

### Post by kennethalan on 2005-12-21
I don't know what you mean, boot into recovery mode.  Can you explain?

Also, I have a very long cable connecting the screen, 10 meters.  However, Ihave had no problem under windows.

---

### Post by 23meg on 2005-12-21
In the GRUB boot menu there must be at least one kernel option with (Recovery mode) next to it. Choose that.

---

### Post by kennethalan on 2005-12-21
I'm afraid again that I don't know what the GRUB boot menu is.

When I start up the computer, everything seems to go OK.  I am asked to choose my language and Keyboard and the screen resolution (Idon't know what I ought to enter, so I clicked on all the options). AT a certain moment there is a cort of checklist where everything is "OK" except for one entry: "synchronizing clock to ntp.ubuntulinux.org" and following this "Error: Temporary failure in name resolution" and then several more items "OK".

Then the screen goes blank and the message "out of range appears"

---

### Post by 23meg on 2005-12-21
I figure you're trying to run the live CD. You should have stated that. 

I don't have much experience with the live CD so can't help you there. If you do an install, there are ways of isolating the problem though.

---

### Post by dcstar on 2005-12-21
[QUOTE=kennethalan]I'm afraid again that I don't know what the GRUB boot menu is.

When I start up the computer, everything seems to go OK.  I am asked to choose my language and Keyboard and the screen resolution (Idon't know what I ought to enter, so I clicked on all the options). AT a certain moment there is a cort of checklist where everything is "OK" except for one entry: "synchronizing clock to ntp.ubuntulinux.org" and following this "Error: Temporary failure in name resolution" and then several more items "OK".

Then the screen goes blank and the message "out of range appears"[/QUOTE]
The "synchronising" stuff is just because the network connection isn't set up, you can disregard that.

The "Out of Range" issue is because the auto-detection of your video system has not happened correctly, and your monitor cannot handle the refresh rate/resolution that Ubuntu is trying to send to it.

Do another re-install, and this time select a screen resolution of 800x600 @60Hz. That should get you past the problem - and you can later change this once you have your system installed correctly.

---

### Post by kennethalan on 2005-12-21
David, you are right.  Thanks!

Now I've got to get my internet connection installed.  Wish me luck!

---

