---
title: "Compiz quitting on it's own for no reason.  Any ideas?"
date: 2007-10-16
forum: Desktop Effects &amp; Customization
---

### Post by Mavtech on 2007-10-16
I have 7.04 installed on my work computer with Compiz 0.5.2.  I have successfully installed Compiz on 3 computers of mine.  But, on my Optiplex 745 with a GeForce 7300GT, it just quits on it's own.  This is the 2nd time this week.  Yesterday, it was turned off when I got back from lunch.  Today, it was in the middle of using it.  I have to restart GDM to get it started again. That wouldn't be much of a problem at home.  But, that's a big task here at work.  I have "compiz --replace" and "emerald --replace" in my start up.  Any ideas?  Thanks.

---

### Post by smartboyathome on 2007-10-16
First off, you can combine the commands into one using && between them, so you can just have one entry for both and have it be compiz --replace && emerald --replace. Anyway, would you run compiz --replace in a terminal and give the output?

---

### Post by Mavtech on 2007-10-17
> **smartboyathome said:**
> First off, you can combine the commands into one using && between them, so you can just have one entry for both and have it be compiz --replace && emerald --replace. Anyway, would you run compiz --replace in a terminal and give the output?

Ok.  That re-enabled Compiz.  But, I got a lot of warnings in the output.  I also want to add that I never did figure out how to use Emerald.  I have it installed.  But, I have no idea how to change the themes.  It does nothing when I click on a theme in Emerald.  Thanks for your help.

```
mike@D001524Ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29609): Wnck-WARNING **: Unhandled action type (nil)
```

---

### Post by bromix on 2007-10-17
I had this same problem sporadically with 7.04 as well.  To the point that I just made a desktop shortcut with the compiz --replace command.  Just cuz I wasn't all about figuring out why it happened.    So, i can't help you as to why.  I can tell you this, I have downloaded the Gutsy Beta and have used it for almost 2 weeks, and it's only happened once.  Might not help ya,  but at least you know it's not only you!  :)  Also, I never needed to restart emerald.  It usually stayed running.

---

### Post by Mavtech on 2007-10-17
Darn.  This time, my borders just disappeared in the middle of usage.  However, in troubleshooting this, I got Emerald to work somehow.  I put Emerald --replace in the command line in the settings for "Windows Decorations" in the Compiz Settings Manager.  Now, when I click on a theme in Emerald, it changes.

---

