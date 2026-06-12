---
title: "Blender messed up."
date: 2009-05-13
forum: General Help
---

### Post by kd0afk on 2009-05-13
I have been trying to get help on this problem for some time now. I tried posting in the Blender forums but those arrogant pieces of crap don't want to help a person unless you can prove that you can code well enough to not need thier help.
Blender will not start up right. Here is a screen shot. [http://img152.imageshack.us/img152/2769/screenshot2lfo.png](http://img152.imageshack.us/img152/2769/screenshot2lfo.png)
I have done everything except install the latest video drivers for my graphics card. the card is an integrated video card and frankly I don't understand the directions on how to download and get the file from the intel linux site. I also haven't messed with the color depth because I don't know how in linux. Also, someone recommended that I turn down graphics acceleration but I can't find that adjustment either. Linux is a very confusing thing and I am learning more and more each day but I am still having problems.

---

### Post by jrutila on 2009-05-13
Well, that looks messed up.

Are you running Jaunty? And you said you have intel graphics card, what card?

You can get needed information from following outputs (use Terminal)
```
cat /etc/issue
```
and
```
lspci | grep VGA
```

Do you have UXA acceleration?
```
grep -i acceleration /var/log/Xorg.0.log
```

If you have Jaunty, you have intel (especially GM965/GL960) and you have UXA enabled, please check [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/353763](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/353763)
That bug looks something like yours.

There is fix on its way (or should be), so you have to wait or change your acceleration to EXA. Changing it to EXA might help.

Changing to EXA:
Add something like this to your /etc/X11/xorg.conf and restart X (Logout, Login). If you have already the following "Device" section just add the line "AccelMethod" inside it.
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"EXA"
EndSection


```

---

### Post by kd0afk on 2009-05-13
> **jrutila said:**
> Well, that looks messed up.

Are you running Jaunty? And you said you have intel graphics card, what card?

You can get needed information from following outputs (use Terminal)
```
cat /etc/issue
```and
```
lspci | grep VGA
```Do you have UXA acceleration?
```
grep -i acceleration /var/log/Xorg.0.log
```If you have Jaunty, you have intel (especially GM965/GL960) and you have UXA enabled, please check [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/353763](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/353763)
That bug looks something like yours.

There is fix on its way (or should be), so you have to wait or change your acceleration to EXA. Changing it to EXA might help.

Changing to EXA:
Add something like this to your /etc/X11/xorg.conf and restart X (Logout, Login). If you have already the following "Device" section just add the line "AccelMethod" inside it.
```

Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"            "EXA"
EndSection


```

How do I change the xorg.conf file? I tried and it didn't let me.

---

### Post by kd0afk on 2009-05-13
In order of trying:
Ubuntu 9.04 \n \l

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

(==) intel(0): Using EXA for acceleration
(II)         Composite (RENDER acceleration)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) set acceleration profile 0
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0

---

### Post by kd0afk on 2009-05-13
how in the hell am I supposed to gain access to change that file? I logged on as super user and I still couldn't do it.

---

### Post by jrutila on 2009-05-14
You have EXA enabled so the bug I posted is not the same issue.

Do you have compiz or metacity running? You can get the answer by running following commands
```
ps aux | grep compiz
```
and
```
ps aux | grep metacity
```

If you are running compiz you could try without it. So, you either run compiz (fancy eye-candy and wobbly windows) or metacity (no 3d effects). 

You can start metacity by running
```
metacity --replace &
```
compiz can be started running
```
compiz --replace &
```
After running either command you don't have to restart X.

Editing /etc/X11/xorg.conf should work with super user access. Do you have the file?
Have you tried
```
sudo gedit /etc/X11/xorg.conf
```

I suggest you try to solve your problem with different combinations
EXA + compiz
EXA + metacity
UXA + compiz
UXA + metacity

You can enable UXA by putting 
```

    Option        "AccelMethod"            "UXA"

```
inside the Device section in /etc/X11/xorg.conf (see my previous post) and restarting X.

---

### Post by kd0afk on 2009-05-14
> **jrutila said:**
>  snipped  Thanks for the "gedit" hint, I will give that a shot as well as the other things you mentioned. I have tried switching from metacity to compiz using that command and it works till I reboot. And, when ever I try to go without compiz, I loose my window borders.

---

### Post by kd0afk on 2009-05-14
I tried editing xorg.conf using the terminal using this code:
su -l (asked for a password, gave password)
return: [EMAIL="root@shawn-laptop"]root@shawn-laptop[/EMAIL]:~#
input: gedit /etc/X11/xorg.conf
return: (gedit:4385): Gtk-WARNING **: cannot open display
 
This is baffling.

---

### Post by jrutila on 2009-05-14
You can't actually use the X with root user if you have logged into it with another user. Root can't get the screen, hence the "cannot open display".
Try either one of these
```
as root input: DISPLAY=:0.0 gedit /etc/X11/xorg.conf
```
or
```
sudo pico /etc/X11/xorg.conf
```

Pico is a text editor that doesn't need X. You should learn one of these editors: pico, nano, emacs, vim and use them in Terminal for editing files.

You can make your metacity/compiz selection default by going System->Preferences->Appearanc->Visual Effects and choose "none" for metacity or other choices for compiz. Did running blender with metacity help you?

---

### Post by kd0afk on 2009-05-14
> **jrutila said:**
> You can't actually use the X with root user if you have logged into it with another user. Root can't get the screen, hence the "cannot open display".
Try either one of these
```
as root input: DISPLAY=:0.0 gedit /etc/X11/xorg.conf
```or
```
sudo pico /etc/X11/xorg.conf
```Pico is a text editor that doesn't need X. You should learn one of these editors: pico, nano, emacs, vim and use them in Terminal for editing files.

You can make your metacity/compiz selection default by going System->Preferences->Appearanc->Visual Effects and choose "none" for metacity or other choices for compiz. Did running blender with metacity help you?I am going to try and get Houdin running for my 3d program. I have used it and I like it as well. Blender isn't worth the stress.

---

### Post by djaquay on 2009-05-15
I, too, have the 82852/855GM, Jaunty 9.04, and have tried the EXA/UXA compiz/metacity foursome, to no avail.  Is there anything else to be tried for this?  Blender under 8.04 was working fine, and I really don't want to downgrade...

Dave

---

### Post by jrutila on 2009-05-16
Dave,

how is your Blender messed up? Can you post a screenshot?
Does it look like screenshots in this thread:
[https://bugs.launchpad.net/ubuntu/+source/blender/+bug/360415](https://bugs.launchpad.net/ubuntu/+source/blender/+bug/360415)

If so, updating your mesa (to 7.4.1, I guess) could be the solution (as described in the bug thread).

---

### Post by djaquay on 2009-05-16
Adding:

Option "NoAccel" "true"

to the Configured Video Device section of xorg.conf kinda cleared it up, although with that setting, my mouse was acting strange (mouse buttons wouldn't stay clicked while moving the viewport, etc.)  But it's certainly better than without.  I'll follow the bug reports; hopefully something will turn up soon.

Thanks,
Dave

---

