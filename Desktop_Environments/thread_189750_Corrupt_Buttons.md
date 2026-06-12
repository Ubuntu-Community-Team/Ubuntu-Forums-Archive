---
title: "Corrupt Buttons"
date: 2006-06-05
forum: Desktop Environments
---

### Post by HeavyAl on 2006-06-05
Hey all,

Just did a fresh install of Dapper after botching the upgrade from breezy due to my own wackiness. 

Now to the problem at hand. 

When viewing various applications that have buttons in them like 'ok', 'cancel', 'close' or the like there is often image corruption on the buttons in the form of vertical or horizontal lines and/or dots that obscure the button text.

I've noticed there are a couple threads that mention this in passing but none that I could get any useful infromation from which is why I am asking about this problem specifically here.

Possibly useful machine specs:

IBM T40
Radeon 9700 using the ATI driver in xorg.conf (I tried updgrading to the fglrx but apparently I must be doing something wrong because replacing 'ati' with 'fglrx' just makes the GDM die forcing me to a CL)
Intel Pentium Mobility (Using the i686 kernel)

---edit---

Forgot to mention that this is what fglrx shows:

display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Which indicates that I'm not getting any acceleration which might be part of the problem. Not sure why this is though since I installed the fglrx drivers. I seem to remember a howto on this being around here but I cant find it now.

---edit---

As I said, this is a fresh install of Dapper so everything else besides the stuff mentioned above is default. 

Any ideas?

-- edit (again) -- 

Well, crud. I guess its not a 9700 even! Its a 7500!! I dont know how I got those switched around but its monday so please forgive me. glxinfo | grep render shows that I'm not getting any direct rendering so thats likely a part of the issue .. going to try and fix this .. 

-- edit --

-- UPDATE --

Ok, I was able to get acceleration working by downloading some dri updates and installing them by hand. So now my X server is fully accelerated. Unfortunately this DOES NOT FIX the CORRUPT BUTTONS problem!

If anyone has any thoughts on this I would greatly appreciate it .. I love my ubuntu but these buttons are just annoying!

---

### Post by Capbri on 2006-06-27
Hi Al,

I'm afraid I can't offer much in the way of suggestions, but I can tell you that I'm running Dapper on a ThinkPad T40 with an ATI mobility 7500 and I experience the same problem of lines of horizontal or vertical image interference over certain buttons. I had originally thought it was just a problem with my LiveCD so when I installed Ubuntu I used the alternate install disc. Sadly, I still have the problem.

I would like to try enabling 3d acceleration on my system but I'm still rather new to Linux and I was wondering whether you knew of any good how-tos for configuring an ATI mobility 7500?

Thanks very much,

Brian

---

### Post by HeavyAl on 2006-06-27
Hey Brian,

Yeah, it turns out that for some reason the buttons from just this release are corrupt with the ati card. It doesnt happen with any of the other themes built in and only a couple other themes that I've downloaded.

Ok, as far as getting you up n runnin with hardware acceleration: It sounds like you have the same rig as me, but wouldn't you know, I dont have mine in front of me right now. But from memory, I recall that I searched for the 'driconf' in the package repository - use synaptic .. you might have to turn on the universe or other unsupported repos but once you find and install driconf just run it from a command line and follow the prompts - its relatively self explanatory.

---

### Post by GeneW on 2006-06-29
Seeing the same thing on my Thinkpad T42 but only on the default "Human" theme.  Changing to the "clearlooks" theme seems to have fixed the issue.

---

### Post by bruce89 on 2006-06-29
I noticed that GeneW has created a bug - [https://launchpad.net/distros/ubuntu/+source/gnome-themes/+bug/51324](https://launchpad.net/distros/ubuntu/+source/gnome-themes/+bug/51324), which I think is a duplicate of [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/38198](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/38198).  Could you confirm this?

---

### Post by GeneW on 2006-06-29
[QUOTE=bruce89]I noticed that GeneW has created a bug - [https://launchpad.net/distros/ubuntu/+source/gnome-themes/+bug/51324](https://launchpad.net/distros/ubuntu/+source/gnome-themes/+bug/51324), which I think is a duplicate of [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/38198](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/38198).  Could you confirm this?[/QUOTE]

Yea, it looks like mine is a duplicate.  I did a search before I submitted it but didn't see that one.  Sorry about that.

---

### Post by bruce89 on 2006-06-29
It's quite a common bug, I'll mark it as a dupe.

---

### Post by HeavyAl on 2006-06-29
Not that its a show-stopper or anything, but is there some easy way to get notified of when bugs like this are updated or (hopefully) fixed?

---

