---
title: "Dual Monitor - different modes?"
date: 2009-02-11
forum: General Help
---

### Post by mykrob on 2009-02-11
I have a dual head nvidia card. In Windows, i could specify a dual head mode where my taskbar and system tray stayed on the main monitor, and if I opened an application, it stayed on the main monitor as well unless i dragged in over to the one on the right. 

Is it possible to do this in Ubuntu? For example, if i open firefox, i dont want it to span across both monitors. I dont want the panel bars to span all the way across. Basically, I want the second monitor to just show a backgorund and sit there unless i intentionally drag something to it.

Thanks,
-myk

---

### Post by yther on 2009-02-11
I'm not at my home workstation right now, but I only built it over the weekend and set up TwinView on Sunday, so I think I remember a little of it.  ;)

Somewhere in your menus there should be an NVIDIA control panel for X.org.  That's where I activated the second monitor, told the system its relative position (to the right of my wide one), and set the size of the giant desktop.  I'm using KDE, and by default I get the taskbar on the left (widescreen) monitor, and apps I launch from that usually start on the left screen.  However, yesterday I launched GIMP and it opened three windows at once; the window manager seemed to spread them out equally so 2 landed on the left and one was on the very right edge of the right-hand screen.  :confused:  If I maximize a window, it fills up whichever screen it was in, but not both.

That sounds close to what you're wanting.  I think there are window manager settings to control where new windows go, but I haven't twiddled with them yet.

One note regarding this:  When I changed the settings and went to save them, I saved them to a file in my home directory because it couldn't overwrite the main one in /etc/X11.  Then I shut down X, and (using sudo) renamed the original file and replaced it with the new one, giving me a fallback in case my settings got screwed.

So far, the only thing I don't like is that on the login manager screen (KDM), the login screen is on the left and some of the right screen is filled with leftover graphical junk from the memory.  Oh well, annoying as that is, I don't spend much time staring at KDM so I just ignore it.  :P

---

### Post by mykrob on 2009-02-11
if it matters, this is in Gnome. I was unable to get the desired effect using nvidia-settings. I'm pretty sure this can be done, and I am just missing something.

---

### Post by bodhi.zazen on 2009-02-11
I find gnome is behind the times when it comes to multiple monitors.

Both XFCE and KDE are much more multi monitor aware.

---

### Post by mykrob on 2009-02-13
just curious if anyone else had any more input on this..

thanks,
-myk

---

