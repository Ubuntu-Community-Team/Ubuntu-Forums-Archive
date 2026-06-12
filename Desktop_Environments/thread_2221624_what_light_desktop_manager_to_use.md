---
title: "what light desktop manager to use"
date: 2014-05-03
forum: Desktop Environments
---

### Post by mastablasta on 2014-05-03
so i've used mini iso and added xfce4, icewm and i3 metapackages. they all use about 107 MB on boot (i do not know why).

anyway first i tried lightDM, but that couldn't launch the XFCE session. i then tried GDM which can launch them all but it is kind of heavy. i then tired LXDM which pulled in a lot of stuff from lxde and crashed the OS and couldn't boot anymore. any other suggestions? i was hoping for something light that could let me choose the desktop on login.

virtualbox install so i have snapshots and was able to recover quickly from crashes.

---

### Post by TheFu on 2014-05-03
Why use a DE at all?  Use a pure WM - Window Manager like openbox, fvwm, heck, twm if you like.

---

### Post by vasa1 on 2014-05-03
> **TheFu said:**
> Why use a DE at all?  Use a pure WM - Window Manager like openbox, fvwm, heck, twm if you like.
OP wants a display manager not desktop manager, if I understood the post correctly.

---

### Post by TheFu on 2014-05-03
Ah ... that's different.

On really low-powered systems, I just connect without any GUI, start a windowless xterm, then run **startx** with the WM/desktop that I want as an arg. No need for a bloated GUI just to start a WM.

---

### Post by ibjsb4 on 2014-05-03
Have you checked out slim?

[https://wiki.archlinux.org/index.php/SLiM](https://wiki.archlinux.org/index.php/SLiM)

---

### Post by walterorlin on 2014-05-04
Display managers are useful if you want to save settings of the WM though. I think slim would be better.

---

### Post by mastablasta on 2014-05-04
oh ok display mangaer that manages desktops. i will try Slim, but does slim have the option of switching desktops?

---

### Post by ibjsb4 on 2014-05-04
Check 'Multiple environments' in my link above.

---

### Post by mastablasta on 2014-05-04
it seems that this

```
# Set directory that contains the xsessions.
# slim reads xsesion from this directory, and be able to select.
sessiondir            /usr/share/xsessions/
```

is missing on default install in the conf file. ive also fixed the desktop list in default file so that fixes is then. slim is not working propperly (before it could only load icewm and occasionally xfce4). hmm perhaps i should add openbox as well. i am ow using i3 to learn it a bit and xfce when i get lost :-)

---

### Post by vasa1 on 2014-05-07
> **mastablasta said:**
> ... slim is not working propperly ...
Some scepticism about sLiM here:
[https://bbs.archlinux.org/viewtopic.php?pid=1114198#p1114198](https://bbs.archlinux.org/viewtopic.php?pid=1114198#p1114198)
and
[https://bbs.archlinux.org/viewtopic.php?pid=1138489#p1138489](https://bbs.archlinux.org/viewtopic.php?pid=1138489#p1138489)

---

### Post by ibjsb4 on 2014-05-08
> [COLOR=#000000]Some scepticism about sLiM here[/COLOR]

I don't know.

When last used it worked for me and 12o4.  Could be the 14o4 package is deprecated.  These days i just use lightdm on my laptop and startx on my testbox (which can also be set up for multiple desktops).  Startx is a good way to test without any bloat from a DM, but then slim was without the bloat (the bloat had to be added).

---

### Post by vasa1 on 2014-05-08
I don't know either, I just came across those comments and thought I'd link here. I've not reached the stage of assessing different DMs. I blindly use the default supplied by Lubuntu, whatever that is.

---

### Post by TheFu on 2014-05-08
I tried slim too - had to ssh in post-install to purge it so any GUI could be started.  I'll be staying with **startx**.

---

### Post by mastablasta on 2014-05-10
yeah cause that part is missing form defautl install. mine also crashed like so only i just had to load a snapshot :P

---

