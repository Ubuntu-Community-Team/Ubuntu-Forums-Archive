---
title: "Ubuntu GUI questions (ATI, applications)"
date: 2006-11-23
forum: Desktop Environments
---

### Post by klarre on 2006-11-23
[I]Hi!
I have quite a few ubuntu (linux) GUI questions:
I prefer GNOME but could possible use KDE if you recomend it.[/I]


1. I would like to install Beryl on the following computers, do you think they are sufficient:
[LIST]
[*]P3 733MHz, 896MB RAM, ATI RADEON 9000 Pro 128 MB?
[*]AMD Athlon XP 2800+, 1.5GB RAM, ATI RADEON 9600 256MB?
[/LIST]


2. As an ATI user, should I use xgl or aiglx (I have read about them but don't really understand the difference, I get the feeling that aixgl is better though)?


3. I have clicked (and downloaded) the ati binary driver under Applications in the ubuntu menu (I am not at that computer right now so I can not check all the correct names). But it seems not to have been installed (or perhaps activated). I still can only choose 1280x960 although the optimal resolution is 1440x900 60Hz (and the graphics card can do way beyond that)? 
I know there are guides for this. I have seen many (thats the problem), please send me in the direction of a guide that suits me.


4. What is the "best" dock for linux (as I said; prefer GNOME but other are OK).
I have seen one with great dynamic effects in YouTube videos, you know the name of that one?


5. What is the "best" dashboard/yahoo! widget engine for linux? It should be able to switch to dashboard view with a button (the screen darkends and widgets shows up). If a single widget can be shown on the desktop at all times that is a plus but not a requirement.

*Perhaps dock & dashboards are included in GNOME or Beryl, in wich case I have not yet found them.*


6. For the dashboard in question 5 is there widget for (hopefully with good looks):
[LIST]
[*]CPU temperatures
[*]HDD temperatures (through SMART)
[*]Fan speeds
[*]Other SMART information (or a GUI application for this)
[*]Weather widget
[*]Alarm clock (reccuring alarms and the like)
[/LIST]


7. I really need to be able to switch from my monitor to my tv with a few button presses (I absolutely would like NOT to use the mouse). Is this possible with ATI? I do have this set up right now:
[LIST]
[*]F9 & F10: sets screen to monitor & sets appropriate resolution and refresh rate for monitor.
[*]F11 & F12: set screen to TV & sets appropriate resolution and refresh rate for TV.
[/LIST]


*Your help is most appreciated!*
Thank you.

---

### Post by Jimmey on 2006-11-23
I wouldn't fancy installing Beryl on a processor that's clocking less than 1GHz. It's worth a try, though. Graphics wise, you're fine with anything bigger than 64MB. Probably.

Between AIGLX and XGL, I don't know. I run XGL okay. 

Docks are easily made using Gnome's own panels.
You can change the properties of Gnome's panels so that they're a little taller, and they don't take up with width of the screen. Or, you might want to try one of the many Docks available as a desklet - Try installing gdesklets.

Resolution wise, if you have the right graphics drivers installed, the glxinfo will tell you. If "direct rendering" is a yes, then you're all set. To specify the range of resolutions you'd like your XServer to use, you can either input them manually in /etc/X11/xorg.conf like this:
> gksudo gedit /etc/X11/xorg.conf
Or, you can reconfigure the Xserver, and pick the resolutions from a menu, like this:
> sudo dpkg-reconfigure xserver-xorg
Making sure to select ATI's driver from the list when prompted.

---

### Post by klarre on 2006-11-24
Thanks!
Please, your help is most appreciated! All questions except for 1 & 3 (and I could use more help on them too) are unanswered.

Thank you.

---

