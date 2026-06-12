---
title: "Borders missing off windows and no minimize, maximize, and close buttons."
date: 2011-11-06
forum: Desktop Environments
---

### Post by Dáire Fagan on 2011-11-06
I have selected the all variants prefix as although I am using Xubuntu 11.04 with Xfce 4.8.0 I recall a similar problem with Ubuntu and Gnome some time before the unity overhaul.

As per the screenshot I logged on today to find the borders of all my windows have vanished along with the minimize, maximize, and close buttons.

Also the bottom Xfce panel which used to pop up on mouseover is no longer 'always on top', although strangely Nautilus and some other windows are, without me selecting that option from their drop down menus.

Is there a fix, or maybe I should just reinstall xfce? If that is the case do I just sudo apt-get remove xfce and then sudo apt-get install xfce? Or maybe X is causing the problem?

[IMG]http://oi40.tinypic.com/14cdu3d.jpg[/IMG]

---

### Post by LinuxFan999 on 2011-11-06
I think it would be a good idea to reinstall XFCE.

---

### Post by Dáire Fagan on 2011-11-06
> **LinuxFan999 said:**
> I think it would be a good idea to reinstall XFCE.

Thanks, but the following seemed to do it:

```
dusf@banshee:~$ xfwm4 --replace
dusf@banshee:~$ sudo rm -rf ~/.cache/xfce*
```

I've once again encountered this problem.

This time:

```
xfwm4 --replace
```

returns:

```
(xfwm4:2528): Gtk-WARNING xx: cannot open display
```

I've tried doing it from a TTY before logging into Xfce, and also from Xubuntu recovery/repair mode after dropping to a terminal with networking support.

From this console I have also tried a: 

```
sudo apt-get remove xfwm4
``` 

and then:

```
sudo apt-get install xfwm4
``` 

but it made no difference.

Any ideas?

---

### Post by Ichido on 2012-07-25
Tanks dusF!
The following fix my laptop:
xfwm4 --replace

---

### Post by Ichido on 2012-07-26
I spoke too soon.
I'm now back to the same problem.

---

### Post by vexorian on 2012-07-26
Does xfwm4 --replace work again?

If that's the case, I'd say something is making the window decorator of xcfe crash one time or the other. Then you will have to report it as a bug. And get used to running it.

It could also be that compiz or some other window manager is running alongside your xcfe stuff. You will have to choose between one of the,.

---

