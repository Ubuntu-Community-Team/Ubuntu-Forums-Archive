---
title: "[SOLVED] no minimize maximize or close icons in upper right"
date: 2008-05-04
forum: Desktop Environments
---

### Post by johnnyhop on 2008-05-04
There are other problems too.  The fresh install of kubuntu 8.04 gave me no icons in upper right corner to close, minimize or maximize, am unable to move the open field by moving the mouse pointer over the title bar.  Actually there is no title bar.  Can't resize open window by dragging boarder.  Pointer must be on some open fields like login and terminal to input text.

---

### Post by Oldsoldier2003 on 2008-05-04
> **johnnyhop said:**
> There are other problems too.  The fresh install of kubuntu 8.04 gave me no icons in upper right corner to close, minimize or maximize, am unable to move the open field by moving the mouse pointer over the title bar.  Actually there is no title bar.  Can't resize open window by dragging boarder.  Pointer must be on some open fields like login and terminal to input text.
```

sudo metacity --replace
``` should sort you out.

---

### Post by GeneralZod on 2008-05-05
> **Oldsoldier2003 said:**
> ```

sudo metacity --replace
``` should sort you out.

a) Metacity is unlikely to be present on a fresh install of Kubuntu ;)

b) A window manager should *not* be run as root.

```

kwin --replace

```

would be a better choice.

---

### Post by johnnyhop on 2008-05-05
GZ, FYI it was necessary to sudo to make the fix permanent.  The command without sudo kept the problem corrected as long as the terminal was kept open.  That shell in the terminal wouldn't return to the home prompt or execute commands.  Opening a new shell would show the home prompt and run commands but as soon as the terminal was closed the gui problem would return.

---

### Post by Oldsoldier2003 on 2008-05-05
> **GeneralZod said:**
> a) Metacity is unlikely to be present on a fresh install of Kubuntu ;)

b) A window manager should *not* be run as root.

```

kwin --replace

```

would be a better choice.

oops i had a gnome moment, but yes you must sudo when you replace the window manager or it doesn't work

---

### Post by UpsideDownFace on 2008-05-10
My laptop suddenly lost these icons - after working correctly for 5 years.
I think I accidentally deleted the "Applications  Places System" from the Gnome title bar, and lost the window title bar as well.

sudo metacity --replace       :- worked OK for me,
but sudo kwin --replace       :- didn't work

so I tried
sudo which kwin
sudo which metacity

and got back
/usr/bin/metacity

so -always try :- which command 
to see if you have it installed

---

### Post by Xiong Chiamiov on 2008-05-11
Well, kwin --replace wouldn't work for you, since you're using GNOME, not KDE.

---

### Post by arizonagroovejet on 2008-05-11
> **johnnyhop said:**
> GZ, FYI it was necessary to sudo to make the fix permanent.  The command without sudo kept the problem corrected as long as the terminal was kept open.  That shell in the terminal wouldn't return to the home prompt or execute commands.  Opening a new shell would show the home prompt and run commands but as soon as the terminal was closed the gui problem would return.

Try putt '&disown' at the end of the command. & puts it in to the background so you get the prompt back. disown means you can close the terminal without killing the process. I.e.
```

kwin --replace & disown

```

---

### Post by omshivaprakash on 2008-12-08
Permanent fix for this issue is here:

1) Get into ~/.kde/env
2) and edit the file kdewm.sh
3) You find the following line

KDEWM=compizmanager

4) Remove compizmanager from it and save the file

5) Logout and login back 

You should be good with it.

---

### Post by johnnyhop on 2008-12-24
This hasn't been an issue with my Kubuntu desktop since upgrading to Intrepid.

---

