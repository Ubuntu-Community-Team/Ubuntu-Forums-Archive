---
title: "[Q][Problem]Cannot Change Unity settings (IE icon size) in CCSM or anything else"
date: 2012-02-29
forum: Desktop Environments
---

### Post by mtotho on 2012-02-29
Hello,

I am new to Ubuntu/Linux (Have a Dual Boot with Windows 7 and this), but I consider myself a pretty smart user.. but this issue is baffling me.

One of the first things I have noticed is that the dock Icons are WAY to large and I cannot fit nearly the amount of things I would like on it. 

Did some google searches, and I found that CompizConfig Settings manager was one of the tools I could use to edit the Unity Settings.

I have the Unity plugin enabled in CCSM, go over to 'experimental' tab, and drag the slider for 'Icon Size' down all the way, but it has absolutely no affect. Additionally, none of the other settings do anything.

I have tried other tools such as "Confity" but that has the same issue as above.

Any help would be appreciate. Perhaps I am missing a step. 


Asus U35JC Laptop
(Intel GMA and Nvidia Graphics==> Nvidia disabled for power save)
Fresh Ubuntu 11.10 32bit.

I don't think my intel graphics have opengl yet, am working on that.

Thanks in advance,
mike

---

### Post by Krytarik on 2012-02-29
Apparently, you are being logged in to Unity 2D, as a matter of fallback, because your current graphics setup, that is, Intel, doesn't support the regular Unity; you can check that by running:
```
/usr/lib/nux/unity_support_test -p
```You can also check if Unity 2D is actually running by checking System Monitor for a couple of "unity-2d-*" processes, or on the command line:
```
ps ax |grep unity-2d
```If the Intel graphics actually turns out to be not sufficient for running the regular Unity, you'll need to enable your Nvidia graphics, obviously.

Regards.

---

### Post by mtotho on 2012-02-29
> **Krytarik said:**
> Apparently, you are being logged in to Unity 2D, as a matter of fallback, because your current graphics setup, that is, Intel, doesn't support the regular Unity; you can check that by running:
```
/usr/lib/nux/unity_support_test -p
```You can also check if Unity 2D is actually running by checking System Monitor for a couple of "unity-2d-*" processes, or on the command line:
```
ps ax |grep unity-2d
```If the Intel graphics actually turns out to be not sufficient for running the regular Unity, you'll need to enable your Nvidia graphics, obviously.

Regards.
Thanks, your first command yielded

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context

```

After re-enabling the Nvidia (and just to be sure)
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2) (prog-if 00 [VGA controller])
```

I get the same output from your first command.. which is not unexpected, I cant expect everything to just switch graphics.

I'll try rebooting to see what happens. 
(This thread has my graphics setup => [http://ubuntuforums.org/showthread.php?p=11728533#post11728533](http://ubuntuforums.org/showthread.php?p=11728533#post11728533) )

If it works, know of anyway to disable the intel graphics?

thanks,

mike

---

### Post by Krytarik on 2012-02-29
> **mtotho said:**
> (This thread has my graphics setup => [http://ubuntuforums.org/showthread.php?p=11728533#post11728533](http://ubuntuforums.org/showthread.php?p=11728533#post11728533) )

If it works, know of anyway to disable the intel graphics?
Well, given what you said over there:
> **mtotho said:**
> At first I had installed the nvidia drivers. I  soon realize that my battery was dying EXTREMELY quickly.
..., I'd rather focus on getting the Intel graphics working somehow; sorry, I can't really help you with that, particularly not with Intel graphics and a hybrid graphics setup.

If that fails too, here is a guide on how to tweak Unity 2D as much as possible - unfortunately, the icon size of the Launcher items is not tweakable there:

[http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html](http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html)

Good luck with your Intel graphics over there in the other thread!

---

### Post by mtotho on 2012-02-29
> **Krytarik said:**
> Well, given what said over there:

..., I'd rather focus on getting the Intel graphics working somehow; sorry, I can't really help you with that, particularly not with Intel graphics and a hybrid graphics setup.

If that fails too, here is a guide on how to tweak Unity 2D as much as possible - unfortunately, the icon size of the Launcher items is not tweakable there:

[http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html](http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html)

Good luck with your Intel graphics over there in the other thread!

Hmm that icon size is a deal breaker for me. And yea going to keep Nvidia disabled.

Thanks for all the help.

Is there an alternative Dock I can use?

---

### Post by Krytarik on 2012-02-29
> **mtotho said:**
> Is there an alternative Dock I can use?
Well, there are a number of alternatives, these are the most popular ones (listed in the order of my own preference/experience):

[LIST]
[*]Avant Window Navigator (AWN)
[*]Cairo Dock
[*]Docky
[/LIST]

---

### Post by mtotho on 2012-03-01
> **Krytarik said:**
> Well, there are a number of alternatives, these are the most popular ones (listed in the order of my own preference/experience):

[LIST]
[*]Avant Window Navigator (AWN)
[*]Cairo Dock
[*]Docky
[/LIST]

Thank you. I have gotten rid of Unity by switching to Gnome Classic, I then installed AWN. Everything is a bit better now. Just hope some day i can figure out a way to get OpenGL support on the intel.

Thanks will mark this as Solved

---

### Post by Krytarik on 2012-03-01
> **mtotho said:**
> ... Gnome Classic, I then installed AWN. Everything is a bit better now.
That's the same setup I'm using, although in Lucid 10.04; and I'm still loving it! :D

Two tips for that:

[LIST]
[*]Replace Gnome Panel with AWN completely; basing the instructions from this earlier guide on the current "gnome-classic.session":

[http://www.tuxgarage.com/2011/05/run-awn-dock-in-natty-narwhal.html](http://www.tuxgarage.com/2011/05/run-awn-dock-in-natty-narwhal.html)
[/LIST]

[LIST]
[*]Replace Gnome Panel's Alt+F2 dialog with Synapse; it's also in the official repos:

[http://www.tuxgarage.com/2011/05/synapse-alternative-to-run-dialog-dash.html](http://www.tuxgarage.com/2011/05/synapse-alternative-to-run-dialog-dash.html)
[/LIST]
Have fun with AWN and Synapse! :D

---

