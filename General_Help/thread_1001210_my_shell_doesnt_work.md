---
title: "my shell doesnt work"
date: 2008-12-03
forum: General Help
---

### Post by kev380 on 2008-12-03
when i try to access the shell with ctrl alt f1 its just a blank screen. none of them work except the gui. i just started using linux last night and i already switched from mandriva to ubuntu because in mandriva when i access the shell and then try to go back to gui the gui is a black screen. whats going on and how can i fix this?

---

### Post by spiderbatdad on 2008-12-03
try ctrl+alt+2-7

---

### Post by kev380 on 2008-12-03
i tried that f1- f6 dont work. f7 is the gui

---

### Post by sedawk on 2008-12-03
Try to login blindly:

login: username
password: password

then enter command (still blind)
```

touch ghostwriter_is_blind.txt
exit

```
Go back to GUI.
If there is a new file "ghostwriter_is_blind.txt" in your
home directory the shell works, but the graphic card or the monitor
freak out in text mode.

I have a stupid TFT here that doesn't show any text - not even
the "BIOS" startup. It can only do the GUI stuff. When connecting
another monitor everythings works as it should be.

---

### Post by kev380 on 2008-12-03
thanks that is the problem. i guess i need to try a new monitor...

---

### Post by doas777 on 2008-12-03
I had a simillar problem on one of my laptops with hardy ( gutsy/fiesty were fine). I tracked it to the VGA mode that is used with text only screens (at boot, at shutdown, and the VTTYs on C+A + F1-F6). you may want to look into them. you configure them in your grub menu.lst.

good luck

---

