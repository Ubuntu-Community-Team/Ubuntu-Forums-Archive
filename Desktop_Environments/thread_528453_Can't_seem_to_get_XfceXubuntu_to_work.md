---
title: "Can't seem to get Xfce/Xubuntu to work"
date: 2007-08-17
forum: Desktop Environments
---

### Post by gila_monster on 2007-08-17
Hello, all.

I have been running KDE/Kubuntu on my Gateway laptop (512M, 1500 MHz processor, decent hard drive) for a while, but it seems to get very sluggish when I have a number of applications open. So I thought I'd also install the Xubuntu files and try it for a while to see if using less RAM helped.

Sadly, this is not working well. I can log in to the Xfce session (appears in the KDM menu), but it doesn't work properly. Mainly, there are no panels. Any window minimized vanishes, although it can be re-raised by the middle mouse button being selected on the desktop. None of the menus or desktop selectors appear at all. Everything works when I boot from an Xubuntu live CD.

What am I missing here? Do I need to have GDM as the default login manager rather than KDM? xfce-panel says it's installed, but I'm getting nothing here at all.

Any help appreciated.

gm

---

### Post by merlinus on 2007-08-17
What happens if you logout, and then choose xfce from Options on the login screen?

-merlin

---

### Post by gila_monster on 2007-08-17
> **merlinus said:**
> What happens if you logout, and then choose xfce from Options on the login screen?

-merlin

Pretty much what I described above. No panels, apps occasionally crash.

gm

---

### Post by merlinus on 2007-08-17
How did you install xubuntu?

I did this:

```

  sudo aptitude update && sudo aptitude install xubuntu-desktop

```

I then could choose xfce at the login screen via Options, and everything worked splendidly.

-merlin

---

### Post by ugm6hr on 2007-08-18
In XFCE:
Alt+F2: **xfce4-panel &**

Should give you your panels.

---

### Post by gila_monster on 2007-08-18
> **ugm6hr said:**
> In XFCE:
Alt+F2: **xfce4-panel &**

Should give you your panels.

That worked. Thanks! We'll see if it sticks until the next login.

gm

---

### Post by ugm6hr on 2007-08-18
> **gila_monster said:**
> That worked. Thanks! We'll see if it sticks until the next login.

gm

If it doesn't stick, make sure you tick the "save session" box when you log out.  

If that doesn't work, you can add the command to the autostarted applications list.

---

