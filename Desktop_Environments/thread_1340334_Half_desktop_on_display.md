---
title: "Half desktop on display"
date: 2009-11-28
forum: Desktop Environments
---

### Post by kjaggu on 2009-11-28
Hi, 

I have no clues how this is happening. However, since today morning there is a strange development on my laptop. I now have two RHS desktops being displayed on my screen. Mind it, this is only the desktop. Applications are running fine and displayed properly. I have no clues how this happened. Please do help me sort this mess. I have attached the screenshot of the same. 

Any help would be really helpful. 

Jagadeesh

---

### Post by routtj on 2010-01-25
I have the exact same issue.
I thought it was a Compiz problem. Disabling Compiz allowed the left half to refresh again (the problem is visible in OP screenshot), but it still divides my desktop into half, and doesn't seem to recognize the left half as part of the desktop at all, i.e. desktop icons automatically go to the top-left corner of the right half of the screen. Screenshot attached for clarity's sake.

---

### Post by SE_Sleepy on 2010-01-25
What happens when you try and switch workplaces?

---

### Post by routtj on 2010-01-25
> **SE_Sleepy said:**
> What happens when you try and switch workplaces?

Nothing at all. It switches fine, but it switches to a workplace with the exact same problem.

---

### Post by SE_Sleepy on 2010-01-25
And are you dual monitoring by any chance? :)

---

### Post by routtj on 2010-01-25
Negative, I'm on a laptop.

---

### Post by SE_Sleepy on 2010-01-25
Maybe you want to try reinstalling your video drivers. But I don't know. I read somewhere that nvidia drivers sometimes mess up with silly bugs like this, but I'm not sure if that will fix it.

---

### Post by routtj on 2010-01-25
I don't have nVidia drivers. And to be honest, I'm not sure how to reinstall my video drivers...
But I'll give it a shot. :D

---

### Post by SE_Sleepy on 2010-01-25
You can reinstall your video drivers trough synaptic or the apt-get command in the terminal :)

---

### Post by routtj on 2010-01-25
Ah, okay, I think I've got it. It's xserver-xorg-video-intel. Reinstalling now. Wish me luck. ;)

---

### Post by routtj on 2010-01-25
Reinstalling the driver (xserver-xorg-video-intel) and rebooting did nothing. I even rebooted once into the .16-generic kernel, just to be sure. Nothing. :(

---

### Post by routtj on 2010-01-25
For some reason, when I disable desktop effects, after I log out and log in, they're turned back on.

---

### Post by routtj on 2010-01-25
Bump.

---

### Post by routtj on 2010-01-26
It randomly went back to normal while I was moving a window.

---

### Post by routtj on 2010-01-26
And after a reboot, it's back again.

---

### Post by routtj on 2010-01-26
Okay, really? Nobody can help? :(

---

### Post by realzippy on 2010-01-26
..there was an updade of xserver-xorg-video-intel....maybe it messed up something?

---

### Post by Jake R. on 2010-01-26
routtj, can you post the contents of "/etc/X11/xorg.conf"?

If you're not sure how to do that, "gedit /etc/X11/xorg.conf" would bring it up, then just copy and paste from there.

---

### Post by routtj on 2010-01-27
/etc/X11 contains:

[folder] app-defaults
[folder] cursors
[folder] fonts
[folder] xinit
[folder] xkb
[folder] Xresources
[folder] Xsession.d
default-display-manager
rgb.txt
X
Xsession
Xsession.options
XvMCConfig
Xwrapper.config

No xorg.conf.

EDIT: Okay, I've figured out the problem. I had made a config file called ~/.gtkrc-2.0 (which is only one line, "gtk-recent-files-max-age=0") to stop "Recent Documents" from functioning, since it's a pain to me. That's what's causing it. If I delete the file and run "nautilus -q" everything's fine again.

---

### Post by lwhitmore on 2011-02-07
I have exactly the same problem - but I'm using Nvidia drivers.

---

### Post by lwhitmore on 2011-02-07
> **lwhitmore said:**
> I have exactly the same problem - but I'm using Nvidia drivers.

Spoke too soon -> solved: [http://guide.ubuntuforums.org/showthread.php?t=1533037](http://guide.ubuntuforums.org/showthread.php?t=1533037)

---

