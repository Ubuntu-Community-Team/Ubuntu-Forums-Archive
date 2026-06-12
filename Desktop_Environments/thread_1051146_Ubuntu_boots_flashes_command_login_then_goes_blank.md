---
title: "Ubuntu boots flashes command login then goes blank."
date: 2009-01-26
forum: Desktop Environments
---

### Post by calmlunatic on 2009-01-26
Hello there.

I'm a rather experienced Windows user, but am somewhat lacking in my knowledge of using Linux. I have Ubuntu (8.1) loaded on an older system I'm working on and have recently tried to install a Matrox video card driver on it (as per the instructions on the Ubuntu website). After restarting the computer it shows the load screen for Ubuntu, then proceeds to go into a command prompt that allows me to log in. 

However, within 5 seconds of prompting for username and password, the screen "blinks" blank before returning to the command prompt login several times before going blank completely, where it stays like this indefinitely until reboot. The monitor indicator light stays on, indicating that it's still getting a signal but that it's blank.

Here's what I've tried so far:

-Ctrl + alt + (F1, F2, F3, F4, or F7)
-Ctrl + alt + Num+ or Num-

-Esc at grub menu
 -going to root and trying to edit the Xorg.conf file back to its original setting; I'm not sure the exact command on how to do this as it is stored in the /etc/X11/ directory but root doesn't let me get there: it keeps saying directory or file doesn't exist or something.
 -trying to repair the installation (this runs fine but doesn't resolve the issue)

I suspect the problem may lie with the editing of the xorg.conf file wrt to the display/video entry as well as the solution too, however I'm at a loss as to how to get there.

Any help/tips would be appreciated. Thanks.

I'm running the following system (not too sure about these details as they're what i've been able to gather from actually looking at the labels inside the box itself; no other documentation/boxes):
AMD 500 
Motherboard: VIA VT S1598S (?) 
384 MB RAM
Video Card: Matrox 906-04, MDH4A32G

---

### Post by gettinoriginal on 2009-01-26
First, back up your existing Xorg with this: (in case you need it back)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Then to edit it:
```
gksudo gedit /etc/X11/xorg.conf
```
In case you need to restore the original:
```
sudo cp -f /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by calmlunatic on 2009-01-26
Thanks for your reply!

> **gettinoriginal said:**
> First, back up your existing Xorg with this: (in case you need it back)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```


I tried this and it seemed to work (I'm current in the root command of the recovery mode); no errors or response.

> 
Then to edit it:
```
gksudo gedit /etc/X11/xorg.conf
```


When I tried this I got a "gksudo: 4594 - Gtk-Warning Cannot Open Display Error."
(though the number after gksudo: seems to change.

I'm still looking (searching forums/google etc.) for a solution to this too. Thanks :)

---

### Post by gettinoriginal on 2009-01-26
If you are already in the root of recovery, then you don't need gksudo in the command.

---

