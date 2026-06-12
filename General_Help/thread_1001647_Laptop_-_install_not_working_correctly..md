---
title: "Laptop - install not working correctly."
date: 2008-12-04
forum: General Help
---

### Post by Grolsche on 2008-12-04
ok, ive installed ubuntu on my laptop.

when it first loaded it ran ok. It did the updates and some installed and some updated okay. It restarted and now I can get to the login section but when i login the screen just goes black and all i see is a white mouse.

Any ideas as to what to do here?

---

### Post by roger_1960 on 2008-12-04
Hi

Try

contrl-alt-backspace

This should restart X (the graphics)

If no good, reboot, pres ESC as soon as grub1.5 appears and go for Recovery mode and then select the Xfix option.

Let us know what happens

---

### Post by Grolsche on 2008-12-04
ok, i did all them and still get black screen  with a white arrow after logging in

---

### Post by Grolsche on 2008-12-04
eeek not many help replys. lol. i take it this problem has you all stumped?

---

### Post by sedawk on 2008-12-04
Do the graphics work when you run the LiveCD?

Save the log file /var/log/Xorg.0.log to some USB-stick or
to your harddisk.

Next time you run Ubuntu from HDD try to get a text mode
(Ctrl+Alt+F1 ?). Then compare the new /var/log/Xorg.0.log
with the one from the LiveCD.

Are they using different hardware drivers? E.g. vesa vs. nvidia?

If you get an error in Xorg.0.log search the internet for that
error, there should be instructions how to bypass your problem somewhere ...

---

### Post by Grolsche on 2008-12-04
it worked ok on the livecd, apart from probably being a bit sluggish  but that is to be expected is uppose with 128mb ram. but I installed it on the harddrive, it was working fine till it decided to do an update then it had some problems with some updates but were fine on others and once it restarted it showed the logon screen and when i enter username and password and go to log on, it looks to be working fine, but then the screen goes black and a white cursor arrow which can be moved around and it makes the start up sound but the screen remains black.

---

