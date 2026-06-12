---
title: "GNOME don!t start - xorg.conf"
date: 2008-01-16
forum: Desktop Environments
---

### Post by tzg6sa on 2008-01-16
Hi!

I write from the Live CD, because my Ubuntu refuse to start. All I have done (in this order):
-I have troubles with touchpad sensitive, but qsynaptics didnt help, after a restart the problem were there
-Somebody wrote that I should write lines in my xorg.conf in the Section Synaptic touchpad
(All should be an Option. Something like that: - I dont remember corectly
TouchPadOff 2
TapButton1 0
TapButton2 0
TapButton3 0)
-I think after that I made a Ctrl+Alt+Backspace to log in again. (I think I dont rebbot mz computer) After that it was fine.
-today morning: first I become a failure message. It was about Xorg and kbd (the keyboard layout has changed too). All I have done with the system files was the thing above. So I decided to make them "comment" with #-sign. Ctrl+Alt+Backspace didnt help. 
-I renamed the xorg.conf.5 file, because it looked like it was the good.  Ctrl+Alt+Backspace didnt help. Before that I was trouble with xorg.conf, but the "sudo dpkg-reconfigure -phigh xserver-xorg" command helped. But now all what I get is a black screen! Reboot: it refuses to reboot!!!!!!! The last message: "Running local boot scripts (/etc/rc.local)". After a minute I shout down with Ctrl+Alt+Del. The first message was: "*Stopping GNOME Display Manager". 

Please help me!
How should I boot my machine to get a GNOME? How could restore the settings?

Thanks!
Zoli

---

### Post by karth on 2008-01-16
When gnome fails to start, you end up in command line mode.
Then you should try to run this:

Through sudo: ```
sudo dpkg-reconfigure xserver-xorg
```

This will revert xorg.conf to default, and hopefully working, state according to your hardware. Then, rememeber to backup a working xorg.conf to paste it back when trying various things ;)

---

### Post by tzg6sa on 2008-01-19
Hi!

With the safe mode I was able to log in, and solve the problem. 
Solution: xserver-xorg reconfigure

---

