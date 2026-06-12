---
title: "xfce desktop broken and unavailable."
date: 2018-06-03
forum: Desktop Environments
---

### Post by makem2 on 2018-06-03
I am using 16.04 and grub loads the login page ok. After I log in I have a blank blue screen and a mouse and that is all.

I can get to root shell but don't know how to access/reinstall the desktop from there.

I also have a live xubuntu usb which was used for this install but have no idea how to access/reinstall the desktop from there.

My /home is on a separate partition so I could re-install the system from scratch but there are some files on the desktop I would like to keep. I am not sure if they would be kept. One reason for re-installing is because lately grub has been slow to start up, only half the white surrounding line coming on and when it does, selection is also slow.

I believe the cause of the missing desktop was the un-installing of some unused programs as when I went to start the terminal for an update I got an error saying a file was missing and terminal was unavailable.

I would appreciate an opinion as to whether I would lose anything from the desktop during a reinstall or whether it would be better to reinstate the desktop first.

Decided to re-install

---

### Post by Bashing-om on 2018-06-03
makem2; ouch -

Maybe a hard row here to hoe.
> 
when I went to start the terminal for an update I got an error saying a file was missing and terminal was unavailable.

Can you activate a console interface -  At the login screen key combo ctl+alt+F1 ? And login to the system there.
IF so what results when executing terminal commands:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```

Else one can try the recovery console .

[INDENT][INDENT]bad things can happen
[INDENT][INDENT]but in linux - we get to keep the pieces and put it back together
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2018-06-03
Sorry late for the party but for future reference:
```
xfce4-session
```
Starts up the Xfce Desktop Environment
Read "xfce4-session man" page on Linux: $ man 1 xfce4-session
```
man xfce4-session
 The xfce4-session program starts up the Xfce Desktop Environment [B]and is
       typically executed by your login manager (e.g. xdm, gdm,  kdm,  wdm  or
       from  your  X  startup  scripts).[/B]  It  will load your last session or a
       default session that includes the standard Xfce programs  if  no  saved
       session is available.

       xfce4-session  is an standard X11R6 session manager that can manage any
       X11R6 SM compliant program, including GNOME and KDE programs.

       xfce4-session uses the contents of the ~/.cache/sessions/ directory for
       starting previously saved sessions.

```
But you solved by way of a fresh install. ;)

---

