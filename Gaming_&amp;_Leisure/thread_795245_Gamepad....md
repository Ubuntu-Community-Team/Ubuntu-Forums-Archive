---
title: "Gamepad..."
date: 2008-05-15
forum: Gaming &amp; Leisure
---

### Post by kamitsukai on 2008-05-15
Sorry i posted this in "Absolute Beginner Talk" by accident and then realized i would probably get more help here, so if i could post the link to my problem:lolflag: [http://ubuntuforums.org/showthread.php?p=4965058#post4965058](http://ubuntuforums.org/showthread.php?p=4965058#post4965058)

---

### Post by acoustibop on 2008-05-15
Simple answer, kamitsukai: remove jscalibrator, including its configuration.  You may need to reboot so your controller is properly redetected.

jscalibrator has a nasty habit of disabling the controls of game controllers, while still reporting them as working Ok.  I really don't know why Ubuntu includes such a problematic package in its repositories.

**Edit:** BTW although Ubuntu puts your first joystick device at /dev/input/js0, many games and applications may look for it at /dev/js0.  If you can get the application to look for it at /dev/input/js0, that's Ok, but it's not always possible.  So make a symlink to /dev/input/js0 in /dev and rename it js0 (or js whichever number it should be), so applications that look for /dev/js0 will find it there.

---

### Post by kamitsukai on 2008-05-15
thanks for the info but how do i make a sym link lol :P

*edit* just thanked you because your info on "jscalibrator" was spot on that was what was causing all my problems....although i would still like to map my gamepad so i could use with my other games...

---

### Post by kamitsukai on 2008-05-15
Ok looked around and found out how to make a symlink but this is what i get...

```
dreamsofubuntu@dreamsofubuntu-desktop:~$ sudo ln -s /dev/input/js0 /dev/js0
[sudo] password for dreamsofubuntu:
dreamsofubuntu@dreamsofubuntu-desktop:~$ joy2key
joy2key - reads joystick status and dispatches keyboard events
By Peter Amstutz (tetron@interreality.org)
This is free software under the GNU General Public License (GPL v2)
              (see COPYING in the joy2key archive)
You are welcome to use/modify this code, and please e-mail me
if anything cool comes of it!
Version: 1.6.1   Binary built on Oct 30 2007 at 08:10:20

Must specify a target!
dreamsofubuntu@dreamsofubuntu-desktop:~$

```

Please help lol

---

### Post by acoustibop on 2008-05-15
Have you checked the symlink is actually there, kamitsukai?  Use Nautilus to see.

---

### Post by kamitsukai on 2008-05-16
nautilus says that it couldnt find it...so what do i do now?

---

### Post by kamitsukai on 2008-05-16
never mind...

---

### Post by kamitsukai on 2008-05-16
Right ok ive found out that the symlink does exist and thats all fine its the error about "Must specify a target!" so what target? is there a better way to map my gamepad?

---

### Post by acoustibop on 2008-05-16
I think the problem is probably joy2key, kamitsukai - it has a poor reputation for configurability and useability.  Unfortunately, I don't know much about it.  I do know that there are some alternatives around that work better; see what you can find.

Ah, another member here, begemot., recommends [Rejoystick]("http://rejoystick.sourceforge.net/") in [this post]("http://ubuntuforums.org/showpost.php?p=4939388&postcount=6").  Check it out - and let us know what you think! ;)

**Edit:** BTW why do you want to use joy2key?  Have you tried using your controller directly in the game you wanted to play?  If it supports joysticks, your controller should work now.

---

### Post by kamitsukai on 2008-05-16
well i would like to use it on teeworlds but the developers have decided not to support gamepads... but thanks about the other reccomendation i will rey it out :)

---

