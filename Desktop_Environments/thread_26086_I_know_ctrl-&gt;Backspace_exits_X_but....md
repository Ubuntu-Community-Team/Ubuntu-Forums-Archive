---
title: "I know ctrl-&gt;Backspace exits X but..."
date: 2005-04-11
forum: Desktop Environments
---

### Post by fizgig on 2005-04-11
how do I get back to my graphical screen?

---

### Post by 23meg on 2005-04-11
ctrl + **alt** + backspace is said to restart x, but it only works occasionally in my clean Hoary installation. i'd appreciate help on this since i need to do it so often!

---

### Post by Quake on 2005-04-11
After you login *In the command prompt*, Type startx to return to the graphical screen

---

### Post by jobezone on 2005-04-11
But If all you get is a blank screen,
 switch between the various Virtual Screens, using Ctrl+alt+F7, Ctrl+alt+F8 and so on up to F12. If GDM (Login Screen) is not in any of them, switch to a Virtual Terminal, Ctrl+alt+F1, log in, and either restart GDM by doing
 sudo /etc/rcS.d/gdm restart    (i believe this is the correct commandm please correct me if I'm wrong)

or do "startx"

---

### Post by fizgig on 2005-04-11
[QUOTE=jobezone]But If all you get is a blank screen,
 switch between the various Virtual Screens, using Ctrl+alt+F7, Ctrl+alt+F8 and so on up to F12. If GDM (Login Screen) is not in any of them, switch to a Virtual Terminal, Ctrl+alt+F1, log in, and either restart GDM by doing
 sudo /etc/rcS.d/gdm restart    (i believe this is the correct commandm please correct me if I'm wrong)

or do "startx"[/QUOTE]

Thanks!  Worked great!

---

### Post by stoneguy on 2005-04-11
[QUOTE=23meg]ctrl + **alt** + backspace is said to restart x, but it only works occasionally in my clean Hoary installation. i'd appreciate help on this since i need to do it so often![/QUOTE]

Something is dreadfully wrong if you have to do this often. Explain how you get into this situation, and what's on the screen when you do. Perhaps someone can assist.

Meanwhile, Quake's instructions are correct, assuming the the X shutdown ran properly. Sometimes it doesn't, and a reboot is required.

---

### Post by 23meg on 2005-04-11
nothing is wrong; i just fiddle with config files a lot to customize Hoary, and rather than rebooting, restarting X is sufficient for most changes to take effect.

in 9 out of 10 times of trying to restart X with this key combo, i get to a login prompt asking my login and password, and startx doesn't work; it either starts the bare X (without Gnome), or just quits back to the prompt. i know this description isn't very scientific, but that's what happens! i don't believe computers are logical creatures anymore anyway :)

---

### Post by jobezone on 2005-04-12
And are you using a login greeter such as GDM or KDM?
If they are working correctly, and you login into your session using them, doing ctrl+alt+backspace should kill X, and then gdm(or kdm) _should_ notice this and restart X and show the login screen.

---

### Post by 23meg on 2005-04-12
yes i'm using gdm. and when i try to restart it from the prompt manually, it fails to restart as well. this is the case even with a clean Hoary installation, no modification whatsoever.

---

