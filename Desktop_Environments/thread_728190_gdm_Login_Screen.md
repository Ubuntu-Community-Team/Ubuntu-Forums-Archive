---
title: "gdm Login Screen"
date: 2008-03-18
forum: Desktop Environments
---

### Post by mike.oldfield on 2008-03-18
Hello,


I am new to Linux, but I seem to have most things working at the moment, however I have a little bit of an issue with the login screen.

I have successfully setup a dual screen system using fglrx, however the login screen insists on being on my second screen.

I have been advised by one of the guys at work that this is due to the fact that the X server picks up the screen with the highest resolution as the primary screen, regardless of how it is plugged into the graphics card. As my TV is running at the equivalent of 1990x1080 (I think, something like that), and my monitor is running at 1280x1024, it is picking my TV as the primary monitor. Unfortunately, because of this, GDM displays things in a STUPIDLY tiny font. It looks like a string of slightly different shaped dots.

Is there any reason why it would be showing this size font and how I can either rectify the font, or move the login screen to my 19" monitor? I'm not too bothered about which screen the login screen picks. I'd rather it be the 19" monitor, but if it must be the TV, I would like to be able to read what it says. It is perfectly fine once logged in. I can read everything on it perfectly well, it's just when using the login manager.

This brings me to my next issue. When logging in, I get a message pop up, but unfortunately, I cannot read what this message says due to the above issue. Whatever it says, it has a tickbox & one button. I haven't tried ticking the box, because I don't know what I'm ticking, but when I click the OK button, it takes me to the login screen again. It does this three times before allowing me to log into the system. If anyone knows what this could be & how to resolve it, I would be very grateful. Otherwise, I'll give more information if someone is able to resolve my first issue.

Thanks for your help,
Mike.

---

### Post by Cybergod on 2008-03-18
Go to the terminal and type:
```
sudo displayconfig-gtk
```

Set the correct monitor as default.  If this doesn't work then maybe you should post your xorg.conf file.

---

### Post by mike.oldfield on 2008-03-19
I took a look at displayconfig-gtk, but it only displays the one screen. I think it's due to the way that I've got my FGLRX driver setup to work with BigDesktop.

I'll grab my xorg.conf the next time I'm near that computer.

Thanks

---

