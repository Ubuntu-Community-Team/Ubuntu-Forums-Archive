---
title: "Login script for desktop environment"
date: 2012-10-12
forum: Desktop Environments
---

### Post by steveheflin on 2012-10-12
I'm running Ubuntu 11.10 and I need to know how to create a script that runs at login time for the Desktop environment.  I know all about .bashrc  for the terminal environment, but I need an equivalent for my desktop.

---

### Post by MG&amp;TL on 2012-10-12
This depends on your desktop environment.

On the default Ubuntu environment (Unity), you can click "Startup applications" in the logout menu, then call a custom script from there.

---

### Post by jerrylamos on 2012-11-24
xrandr: I have to run every it every time I start because Ubuntu doesn't set resolution to  1366x768 TV screen external monitor connected by VGA.

I put an xrandr exec into startup but the resolution does not get set.  
I have to manually issue the exec after the Unity desktop s l o w l y starts.

Yes I've got an .xprofile with the same commands, and /etc/X11/xorg.conf with the 1366x768 resolution but they don't work on Raring or Quetzal.

I looked at the Ubuntu help stuff on Startup which is sorely deficient on examples.

Anything to try?  Thanks.

---

### Post by Lars Noodén on 2012-11-24
I was going to suggest trying ~/.xsession but it does not seem to be recognized by the system in 12.04.  I wonder if that is the same bug you have with .xprofile and if it has been filed already.

---

### Post by jerrylamos on 2012-11-24
Thanks for your suggestion.

My three line exec didn't work from Startup, so I made three entries into startup, one for each line, like so:
```

Title: xrandr line 1
command: xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
Title: xrandr line 2
command: xrandr --addmode VGA1 "1366x768_60.00"
Title: xrandr line 3
command: xrandr --output VGA1 --mode "1366x768_60.00"

```
That worked.
I'll think about a bug for launchpad Raring where a Startup exec does not work but the individual commands within the exec do.  Bug is, Startup doesn't execute the exec.

Now the true bug may be the exec gets issued but Unity is so s l o w that it wipes out the resolution when it f i n a l l y gets the screen up.

Yes, I do use Lubuntu on a notebook after replacing Chromeium with Firefox and adding Libre Office.  I don't like Unity I just run it as a tester on Development.

---

