---
title: "XFCE without xubuntu"
date: 2006-09-15
forum: Desktop Environments
---

### Post by Onion Avenger on 2006-09-15
I'd better first state that I'm new to Ubuntu, but have been using Linux for a little over a year on other distros.

I enjoy XFCE and installed it on Ubuntu (by installing xubuntu-desktop), but to my dismay noted that it is a heavily Ubuntu-cized xfce4.

Is there a way for me to have a vanilla xfce, just the one you get from installing it from their website?

I assume there are some settings somewhere to delete or change but I just don't know what exactly.

Thanks in advance,
Richie

---

### Post by akshaysrinivasan on 2006-09-15
Well i think there is package called xubuntu-default-settings.Maybe you could remove it.But i still found xfce running the same way after removing it.

---

### Post by aysiu on 2006-09-15
Well, removing Xubuntu may be difficult, depending on how you installed it and what you had installed before.

But to install just vanilla XFCE, you would have done: ```
sudo aptitude update && sudo aptitude install xfce4
```

---

### Post by Onion Avenger on 2006-09-15
Yes, I've tried removing xubuntu-default-settings and that didn't do the trick.  I'll try removing all things xfce4 (because I have xfce4 and all the panel plugins and whatnow installed too) and then installing it as you suggested, aysiu.

Thanks for the replies!

---

### Post by brucevangeorge on 2006-09-15
You mean reinstalling XFCE (the new version) in place of what you have already?

Or a complete overhaul with formatting involved?

---

### Post by Onion Avenger on 2006-09-16
> **aysiu said:**
> But to install just vanilla XFCE, you would have done: ```
sudo aptitude update && sudo aptitude install xfce4
```

Hm, aptitude install xfce4 pulled in xubuntu-default-settings as well.  apt-get install xfce4 did NOT pull in xubuntu-default-settings but they both still looked like xubuntu rather than xfce4.

---

### Post by brucevangeorge on 2006-09-16
Well, duh.

That's because Xubuntu uses XFCE. So of course it looks the same.

just change the theme if you want it to look different.

---

### Post by Onion Avenger on 2006-09-16
brucevangeorge: Yes, I know that xubuntu uses XFCE, my issue is that I don't want xfce xubuntu-ized as it is.  For instance it has xfdesktop4 running and the panels set on top and bottom and lots of changes in the settings dialog (like where did xfce4-iconbox go?) and a dozen other things that xubuntu has done to modify xfce4 into xubuntu.  It's a little more involved than just "changing the theme".  I suppose I could go through and change all the settings so xfce4 is vanilla, but I was wondering if there was some command to do this or some config files somewhere that make xfce4 into xubuntu that I could delete.

Perhaps a quicker way (though not necessarily better) would be to strip all traces of xfce4 off my system, go to xfce.org and download and install it from there.

Regardless, thanks for your help.

---

### Post by Onion Avenger on 2006-09-16
> **brucevangeorge said:**
> You mean reinstalling XFCE (the new version) in place of what you have already?

Or a complete overhaul with formatting involved?

I guess it would be the second option.  I'm trying to "overhaul" it by undoing to xfce4 what xubuntu did to it.  I didn't think that it would be this complicated to do...

---

### Post by brucevangeorge on 2006-09-16
Not sure you can do much to it in that sense. You can set the setting sin the window manager and themes and such to make it look like xfce originally.

Like installing and using the rodent theme icons.
Selecting the XFCE4 theme in the window manager.
XFCE wallpaper.
Changing how the panels look and behave.

etc.

It in the system spanel somewhere.

---

### Post by grim4593 on 2006-09-25
What I did to get just xfce was to do a server install so I started out with a minimal system. I tried the xubuntu-desktop and it was installing all the crap that regular ubuntu had, which was not desired. So after the server install I enabled the universe repositories and...
```
sudo apt-get update
sudo apt-get install gdm xterm xfce4-terminal menu x-window-system-core xfce4 synaptic thunar firefox
```
You can substutute xdm for gdm, and firefox/thunar are not really necessary but you will need a filemanager and webbrowser anyway.
From that point you should be able to log right into the xfce desktop, which is rather empty. If you can't get into the desktop you can still access synaptic by typing 
```
xinit
``` at terminal and after X starts type 
```
sudo synaptic
``` to access the package manager to install the wanted programs.
Then you can use synaptic to install the rest of the stuff you want by searching for xubuntu and xfce. (xfce files, mousepad/gedit, archive tools, etc...)
I guess it is more of a hassle than doing a full xubuntu-desktop install but I wanted to start out with nothing and choose what I want instead of starting with a cluttered system with programs I would never use.

---

