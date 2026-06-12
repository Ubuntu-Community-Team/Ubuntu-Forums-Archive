---
title: "No desktop icons or wallpaper"
date: 2009-09-03
forum: Desktop Environments
---

### Post by s.fox on 2009-09-03
Hi,

I am having some major problems with XFCE.  I seem to have no desktop icons or wallpaper.  Alt+F2 isn't working either, but I am not sure if that's related.

I can confirm that  xfdesktop is running:

```

[user@localhost ~]$  ps aux | grep xfdesktop
user      1811  0.3  2.2  26368 11448 tty1     S+   23:13   0:02 /usr/bin/xfdesktop-xfce --sm-client-id 117f000001000125198113400000018080000 --display :0.0
user      4743  0.0  0.1   4192   744 pts/0    R+   23:25   0:00 grep xfdesktop

```

I tried doing this to fix the problem but it didn't work:

```
xfdesktop -reload
```

All I seem to have on my desktop is an icon(s) denoting running programs.

Can anyone please assist me getting my desktop back?  I am truly stumped.

Many thanks,

Silver Fox

---

### Post by mrgnash on 2009-09-04
Every time I have tried XFCE in the past, I've had problems like this. It seems to get confused about whether it should be managing the desktop or not. In the end, I gave up using it. But try Settings -> "Desktop Preferences" and set the option "Let XFCE manage the desktop."

---

### Post by kerry_s on 2009-09-04
under your pic there it says your using jaunty, so your xfce4 version is 4.6 right?

first thats start with the easy, alt+f2 is set in menu-> settings-> keyboard-> application shortcuts
make sure that set.

if thats set the alt-f2 is run by the window manager "xfwm4" so make sure thats running in menu-> settings-> session & startup-> session

for the icon, right click the desktop-> desktop settings-> icons
make sure "icon type" is set to "file/launcher icons".

---

### Post by kerry_s on 2009-09-04
> **mrgnash said:**
> Every time I have tried XFCE in the past, I've had problems like this. It seems to get confused about whether it should be managing the desktop or not. In the end, I gave up using it. But try Settings -> "Desktop Preferences" and set the option "Let XFCE manage the desktop."

that options gone in later xfce4 versions.

---

### Post by mrgnash on 2009-09-04
> **kerry_s said:**
> that options gone in later xfce4 versions.

Oh, ok, well that shows you how long ago I stopped using it then :P

---

### Post by s.fox on 2009-09-04
Hello,

Thank you for all the replies.  I tried a few things while I was waiting for responses and actually did more damage.  In the end I decided to completely reinstall.  A little extreme I know,  but it also gave me the chance to try out the Netbook Remix which I have been wanting to do for a few months now.

Many many thanks,

-Silver Fox

---

### Post by kerry_s on 2009-09-04
> **Silver_fox_ said:**
> Hello,

Thank you for all the replies.  I tried a few things while I was waiting for responses and actually did more damage.  In the end I decided to completely reinstall.  A little extreme I know,  but it also gave me the chance to try out the Netbook Remix which I have been wanting to do for a few months now.

Many many thanks,

-Silver Fox

netbook remix is okay, if you disable the fancy effects you can get pretty good speed & resource use out of it.
the thing i really liked was maximus, i spent a few days getting it to work in xfce4, i swapped out xfwm4 for metacity, i turned on reduced_resource in metacity which actually use less then xfwm4.
the hard part was coming up with the close button, i found xautomation that has a program called xte, a little script & i have a close button.
i had to also change a few things under the hood so metacity runs xfce4 programs instead of the gnome ones. it was all worth it works great.

---

### Post by s.fox on 2009-09-04
Hey,

I'm impressed with the remix too.  I have only encountered one problem with it,  namely that the mic doesn't work with Skype.  I am currently researching into the problem before I go and create a thread about it on the forum.  Oh, just in case you were wondering I installed it on the Acer Aspire One. :)

-Silver Fox

---

### Post by kerry_s on 2009-09-04
have you tried running "alsamixer" in terminal make sure its not muted?

---

