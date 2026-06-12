---
title: "Running without GUI"
date: 2005-09-17
forum: Desktop Environments
---

### Post by zugvogel on 2005-09-17
Hello. I want to run ubuntu with just the vtwm window manager and specific programs I choose. For this reason I don't always want the x server and gdm manager to start automatically upon boot. The aim of this is to get maximum battery life / maximum dedication out of the laptop, dedicating all resources to the one or two programs I am using.

I've tried killing the existing Xorg and gdmanager services from the command line, but this just causes them to start again automatically. So my question is:

How can I start Ubuntu without starting the graphical interface? Or failing that, how do I kill it once it's started, to enable me to start from scratch?

Many thanks!

edit: I've just realised I've posted this in the Warty section by accident, instead of Hoary... I guess the answer will be the same anyway, whatever version of ubuntu I'm using...

---

### Post by tonym on 2005-09-17
Remove the gdm package.

Or once booted run /etc/init.d/gdm stop

---

### Post by zugvogel on 2005-09-18
Thanks for the quick reply. I tried that but it seemed to start "gdmgreeter" in it's place, which wouldn't kill, so in the end I tried Ctrl-Alt-Backspace which killed everything in one go. I'm not sure whether that's healthy or not, but it does the trick.

---

### Post by FLeiXiuS on 2005-09-18
The easiest and foremost beneficial way to do this would be to enable Ubuntu to default to a different init level.

1.) Editing the inittab.
```

$ sudo nano -w /etc/inittab/

```

2.) Editing w00t..You'll see something like this near the top of the file.
```

id:2:initdefault:

```
Change the number 2 to a 3.
```

id:3:initdefault:

```

3.) Save and exit.

4.) Now lets remvoe the symbolic links which will tell gdm to start up under runlevel 3.
```

$ sudo rm /etc/init.d/rc3.d/S13gdm

```

Then you could reboot your machine if you please.  But when changing runlevels I just type:
```

$ sudo telinit #
// In your case...
$ sudo telinit 3

```

Things should work out smoothly from there.  If you have any problems let me know. 

NOTE: You could also remove a few more services in that runlevel that you may not need.  There's serveral of them which for most users have no effect.

---

### Post by zoobave on 2007-08-27
Its Very Simple. Just remove all the entries in 
**/etc/X11/default-display-manager** file

Now, reboot your machine, it automatically  boots without GUI(Without starting X server).
If you want to start the X server, just give 
```
#gdm
```

regards,
zoobave
[http://zoobave.blogspot.com]("http://zoobave.blogspot.com")

---

