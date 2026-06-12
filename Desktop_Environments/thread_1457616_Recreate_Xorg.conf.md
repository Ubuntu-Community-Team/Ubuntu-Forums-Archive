---
title: "Recreate Xorg.conf"
date: 2010-04-18
forum: Desktop Environments
---

### Post by secondsystem on 2010-04-18
Running kernel 2.6 on a Dell Dimension 4700C with intel GMA900 graphics.  For some reason the ubuntu installer did not create an xorg.conf file which is completely annoying.

It looks like it should be possible for me to recreate xorg.conf from a terminal by holding down ctrl+alt+Fxx and running sudo dpkg-reconfigure -phigh xserver-xorg.  This does absolutely nothing, and I can find no other way to start ubuntu without Xwindow.

As it is I can run gnome but I can only run 800x600 resolution through the VGA connection.  I am using a Dell/Sony P1110 CRT.  Strangely, the box is able to detect another LCD monitor and allows that to run 1024x760 through VGA.

I've never seen a linux distro that would run with no display config file.  How the heck does it even work at all?

---

### Post by byStanderone on 2010-04-18
(courtesy of osguides.net)

How to create xorg.conf in Ubuntu 9.10
Monday, 23 November 2009 02:52

One of the changes on the new Ubuntu 9.10 is that xorg.conf is missing. The reason for this is that the configuration to be done on user level. The file xorg.conf will be in use only if it exists. Only the time will show if this new concept is good but I personally think it is.

 

 

Sometimes you do need to have the xorg.conf though. Mainly when you need to use some hidden options of your graphic device or touchpad for example.

 

Firstly we need to create the file xorg.conf. Fortunately there is automatic way of doing this with generating xorg.conf with the detected devices from the X.

 

In order to generate xorg.conf you need to switch to one virtual console using the key combination CTRL + ALT + F1.

Now execute the following commands:

user@ubuntu ~# sudo service gdm stop

This command will stop the X.

Now we need to generate the xorg.conf file:

user@ubuntu ~# sudo Xorg -configure

This has generated the file in ~/xorg.conf.new.

We need to make the X using it so we have to put this file inside /etc/X11/

user@ubuntu ~# sudo mv ~/xorg.conf.new /etc/X11/xorg.conf

After moving this file to the proper location you can start the X again and see what happens:

user@ubuntu ~# sudo service gdm start

 

Good Luck!

---

### Post by asmoore82 on 2010-04-18
> **secondsystem said:**
> I've never seen a linux distro that would run with no display config file.  How the heck does it even work at all?

Linux does not stagnate like other OS's.

Almost all Desktop Linux's from this point forward should be capable of running with no xorg config.

The magic missing link you are looking for is the command line tool `xrandr`
As its name suggests, it was initially a frontend for the "X Resize and Rotate"
extensions but it has grown to be much more.
It can even add VGA modelines on-the-fly that were not auto-detected by X.

That having been said, if you really do have a graphic card and monitor combo
that do not detect the optimal modes automatically, it is understandable that
you will not want to be re-running `xrandr` after ever reboot to fix it.
So, as you make a xorg.conf for a more permanent solution, just remember
to **keep it as sparse as possible**. It will still auto-config the rest.

In other words, let the auto-config do 99% of the work.

---

### Post by byStanderone on 2010-04-18
...thanks asmoore82, that's a great one you gave.

---

### Post by asmoore82 on 2010-04-19
I had to get access to my girlfriend's laptop before I could post this...

As a perfect example, my girlfriend's laptop runs Ubuntu 10.04 Beta with the nonfree nvidia driver.
So xorg has to be told to load this driver instead of the open-source one.

This is her entire xorg.conf as created by Ubuntu:
```
[COLOR="Purple"]**$** cat /etc/X11/xorg.conf[/COLOR]

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

^^only put in the absolute minimum necessary to get the desired effect.
so for the OP, is should be maybe just a couple sparse sections with a couple modelines for 1024x768.

---

