---
title: "Screen resolution set ot 'off'"
date: 2008-12-07
forum: General Help
---

### Post by riley_17 on 2008-12-07
Hi, i have recently got ubuntu and have messed with the screen resolution today. I saw the off option and i was too tempted to see what it did. Now im just stuck with a black screen everytime i load up. Does anyone have any ideas how i can get my display back?

Cheers
Adam

---

### Post by NT4usB on 2008-12-07
Black screen like it's turned off, or black screen with text/cursor?

---

### Post by riley_17 on 2008-12-07
as in completely black like its switched off. I can hear the music when i log on but the screen is blank so i know its running fine.

---

### Post by NT4usB on 2008-12-07
Well, I've never noticed a off button for resolution.
Do you see stuff while it's booting?
If you Ctrl+Alt+F1 do you switch to a tty with text and a cursor? 
If so, sort of a brute force approach but you could try: (log in and)```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by riley_17 on 2008-12-07
Ive just tried the the above solution and while the tty loaded and the code could be entered it didnt seem to make a difference. I really have no clue as to what i am doing if im honest though. Thanks for your help though.

---

### Post by NT4usB on 2008-12-08
I'm just guessing myself since I've never managed to break mine that way, never had to fix this problem.
Which Ubuntu you running? What video card? Describe where you found that off option. I'm looking around and I don't see it. 
Open a terminal, type:```
cat /etc/X11/xorg.conf
``` Copy (highlight, Ctrl+Shift+c in the terminal) and paste the output here.
Did you restart the computer or gdm after the reconfigure?```
sudo /etc/init.d/gdm restart
```
Maybe you can put the Ubuntu CD back in and boot to the live CD. Then you can go back and see which setting you changed. 
Might try the reconfigure without the -phigh switch. It will ask you a bunch of questions about the keyboard, etc. Don't know if it would make any difference...

---

