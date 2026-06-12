---
title: "How do I change my desktop resolution"
date: 2006-11-13
forum: Desktop Environments
---

### Post by Cbotron on 2006-11-13
How do I change my resolution?

---

### Post by an.echte.trilingue on 2006-11-13
Open a terminal.

Type this command:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure xserver-xorg

```
be prepared to answer some questions about your video card, keyboard, and mouse.  During the section on your monitor, select the sizes you want to be available.  When the configuration wizard is done, restart the X server with CTRL+ALT+BACKSPACE.  You will have to log in again.  Now, the resolutions you selected will be available under the preferences menu.


If you find that this messes up your screen configuration, log into a failsafe session and type:

```
sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

to undo what you did.

Take care,
-mat

---

### Post by Cbotron on 2006-11-13
Isn't there an easier way to change it?:(

---

### Post by an.echte.trilingue on 2006-11-13
That depends.  If you go to desktop-->preferences-->screen resolution, you will see the resolutions that your computer is configured to handle, but since the Ubuntu detection script is pretty conservative to avoid breaking people's hardware, you probably have to configure the available resolutions yourself, which is what the steps I outlined above do.

This is actually pretty easy already, once you begin to understand what you are doing.  There is a learning curve involved in linux, but once you get over that first bump it is really easy and nice.

And we are here to help you.

Good Luck!

-mat

---

### Post by senior on 2006-11-13
Hi Cbotron,

When the  Ubuntu version is running use the Tabs:

Ctr+Alt   and + or -.

to alter the resulution of the screen.
This is the easiest way and will work.
Senior.

---

### Post by an.echte.trilingue on 2006-11-13
> **senior said:**
> Hi Cbotron,

When the  Ubuntu version is running use the Tabs:

Ctr+Alt   and + or -.

to alter the resulution of the screen.
This is the easiest way and will work.
Senior.

True, but the problem remains that if you have a 1600x1200 screen and xorg is only configured to go up to 800x600, then that is the best you're gonna get.

---

### Post by wojoe2k6 on 2006-11-13
I used the reconfigure to change from 640x480 to 800x600 which is what is designated in the specifications. The display still exceeds the screen. Ctl+Alt - does not do anything. Thanks.

---

### Post by wojoe2k6 on 2006-11-13
You forgot to tell me I had to restart. The display is fine now. Thanks again.

---

### Post by an.echte.trilingue on 2006-11-13
> **wojoe2k6 said:**
> You forgot to tell me I had to restart. The display is fine now. Thanks again.

Oops, sorry about that.  I do that alot...

Glad things are working for you now.

Take care,
-mat

---

