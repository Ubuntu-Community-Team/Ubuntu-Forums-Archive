---
title: "How do I exit out of a Ctrl-Alt-T ?"
date: 2014-03-09
forum: Desktop Environments
---

### Post by oygle on 2014-03-09
I have read a number of articles about keyboard shortcuts. Many have Ctrl-Alt-T shown, but none I can find show how to "exit" out again and get back to the desktop.

I use Ctrl-Alt-T and a login appears. I enter username and pwd and I'm at a bash/shell command prompt, but how do I "exit" that and get back to the desktop again ?

Also what command from the desktop starts a new window with Konsole ?

Have used Alt-F2 to open a window for entering an app name. It doesn't seem to run shell/bash commands though, only app names.

Is there a tutorial somewhere that shows all the keyboard shortcuts under Kubuntu, and also shows what to do when that command is used ?

(i.e. when computer hangs at anytime, I can use Ctrl-Alt-F4 )

---

### Post by ajgreeny on 2014-03-09
Try **Ctrl+Alt+F7** which in the other OSs of the *ubuntu family is the tty on which the GUI resides.

That may be different in KDE/Kubuntu, however, as Ctrl+Alt+T more usually opens a GUI terminal, ie Konsole, not a command-line tty

---

### Post by Lars Noodén on 2014-03-09
> **oygle said:**
> 
Also what command from the desktop starts a new window with Konsole ?


ctrl-shift-n should start a new window, ctrl-alt-t should start a new tab but that has to be done with Konsole being the active application.

---

### Post by oygle on 2014-03-09
> **ajgreeny said:**
> Try **Ctrl+Alt+F7** which in the other OSs of the *ubuntu family is the tty on which the GUI resides.

That may be different in KDE/Kubuntu, however, as Ctrl+Alt+T more usually opens a GUI terminal, ie Konsole, not a command-line tty

Thanks for that tip. I tried it but now I can't even do a Ctrl-Alt-T for some reason. I did do a software update and it contained a kernel update, and I have seen older posrs where people have lost their keyboard shortcuts after a kernel update. I will write it down though, for the next time I can do a Ctrl-Alt-T

> **Lars Noodén said:**
> ctrl-shift-n should start a new window, ctrl-alt-t should start a new tab but that has to be done with Konsole being the active application.

Thanks, I will take note of that one. Ctrl-Shift-N does nothing but I assume the kernel update did that ??

$ **lsb_release -a**
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 13.10
Release: 13.10
Codename: saucy
$ **uname -r**
3.11.0-18-generic

---

### Post by Lars Noodén on 2014-03-10
Oops.  Ctrl-shift-T should open a new tab.  Ctrl-alt-T should still open a whole new terminal.

---

### Post by 23dornot23d on 2014-03-10
Sounds more like the user did a (ctrl + alt + f1) or ( ctrl + alt + f2 ) to get to the console to
do some work ........ (ctrl + alt + f7) will bring you back again 

As long as the DM was not stopped while in the console.

But even then by typing **lighdm** or **kdm** or **gdm** ....... whichever applies to your own login .... 

Will bring the login backup again ......

Ctrl + alt + T is usually for getting a terminal up - but this is not always set that way as I found out
recently.

also (Ctrl + alt + del) is usually the logout ...... but in Xfce4 its the way to lock the screen .....

Consistency is what makes a system easy to use for users where it is possible.

---

### Post by Erik1984 on 2014-03-10
CTRL + ALT + T does nothing for me in Kubuntu.

---

### Post by pauljw on 2014-04-06
try CTRL-D in the active terminal.  closes it for me.

---

