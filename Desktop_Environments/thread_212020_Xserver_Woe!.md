---
title: "Xserver Woe!"
date: 2006-07-09
forum: Desktop Environments
---

### Post by panrubius on 2006-07-09
I've just installed Ubuntu, and it's really wonderful. I've made a complete switch from Windows and haven't looked back; this is the first major problem I've come across.

I switched on my computer and was greeted with a dialogue box telling me that the Xserver was broken or not configured properly. After some reading on this forum I tried to reconfigure Xserver using the command:

[COLOR="Blue"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

Everything seemed to be going okay until I got to the part of the process that asked me to select the screen resolution, I think. When I selected 24, I was taken out of the reconfigure process and this error message appeared:

[COLOR="Blue"]xserver-xorg postinst warning: overwriting possibly customised configuration file; backup in /etc/x11/xorg.conf .20060709001812[/COLOR]

I then went and looked in /etc/X11 and could not find a file called xorg.conf .

I then went and tried the sudo dpk reconfigure command again and was greeted with this error:

[COLOR="Blue"]GDM: Xserver not found: /usr/bin/Xgl :1 :1 -fullscreen -ac -accel
glx:pbuffer -accel xv:pbuffer -auth /var/lib/gdm/:1.Xauth -nolisten tcp vt7

Error: Command could not be executed!

Please install the X server or correct GDM configuration and restarT GDM[/COLOR]

Please help me! This has taken my wonderful new media server offline and I am full of woe. Anyone have any ideas?

---

### Post by panurge77 on 2006-07-09
Have you tried looking for a xorg.conf backup?
Did you upgrade your kernel?

---

### Post by panrubius on 2006-07-09
I couldn't see a backup and I wouldn't know how to upgrade my kernel.

Will upgrading leave my data intact?

---

### Post by ShiningHolden on 2006-07-09
Upgrading your kernel is just like, In Windows, getting a security fix, except, It is alot more useful.

You realize the problem is XGL don't you?

Remove it from startup and your gdm.conf-custom

Startup:
```

System > Prefrences > Sessions > Start Up Programs > Remove anything that you put to boot up XGL.

```

GDM File:
```

sudo gedit /etc/gdm/gdm.conf-custom
Scroll down to servers, remove anything below
[servers]
Also remove [servers-xgl]

```

Also, once the X Server is running and you get to your login screen, go to sessions and make sure XGL isnt there. If it is, select whatever you use. GNOME or KDE.

Hope this helps.

And thank you for being open minded and calm when seeing a problem with Linux, and not running back, crying to Windows, to in result, Blue screen on you and saying "Care for user not found".

Linux, for the win.

---

### Post by panrubius on 2006-07-09
Thanks for the swift reply, but:

when I enter:
sudo gedit /etc/gdm/gdm.conf-custom

it says

cannot open display: null

did i mention that i can only reach the cli when i boot up.

and yes, ubuntu so far has been amazing!

---

### Post by panrubius on 2006-07-09
Any other ideas?

---

### Post by thetejon on 2006-07-09
I'm having the same problem.  I was trying to configure my video card to display at resolutions beyond 640X480 and now I can't get any sort of graphics to display.  I get the same "cannot open display: (null)" error when I do sudo gedit . . .

EDIT:  Cancel that.  I went into /etc/x11 and renamed the first xorg.conf backup to be the primary and it worked.  I still can't get any resolution better than 640X480, but at least my GUI works again.  

Panrubius, it looks to me like you (as I did) got some bad value in your xorg.conf file, and it's preventing the display from starting up.  You may want to start over with a default xorg.conf.  However, as I'm brand new to Linux and a bit of a clown when it comes to these things, you may want to wait for someone more knowledgeable.

---

### Post by pjbgravely on 2006-07-10
> **panrubius said:**
> Thanks for the swift reply, but:

when I enter:
sudo gedit /etc/gdm/gdm.conf-custom

it says

cannot open display: null

did i mention that i can only reach the cli when i boot up.

and yes, ubuntu so far has been amazing!

Use pico instead of gedit when in command line. You can also use nano or vi, what ever you like best.

so you line would be. 

sudo pico /etc/gdm/gdm.conf-custom


Paul

---

