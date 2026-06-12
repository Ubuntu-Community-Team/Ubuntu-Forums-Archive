---
title: "Is there any way I can get rid of the left dock on activities?"
date: 2021-10-23
forum: Desktop Environments
---

### Post by justjeff-999 on 2021-10-23
Hello!

I recently decided to try customize Ubuntu's appearance, and I relied mainly on Gnome Tweaks to accomplish this, installing the following extensions:
- Dash-to-dock
- Transparent topbar

However, one quite annoying thing is the fact that when activating the activites, 2 application bars show up, one on the left, and the other at the bottom. I want to get rid of the bottom one. Here are some attachments of what I mean.

Is there any way to do this? Thanks!

---

### Post by TheFu on 2021-10-23
> **justjeff-999 said:**
> Is there any way to do this? Thanks! 

Any way? Sure, but you probably should wait for a Gnome3 or Gnome4 answer for a few days to avoid a huge GUI change.

Use a different DE or no DE at all.  There must be 50 choices for the different GUIs.  They are just an apt-get install away.  3 minutes even on my slow cable connection.  Look in the package manager tool that you use for "*-desktop" to see the DEs.

But you don't actually need to use a DE at all.  DEs sit on top of WMs (Window Managers).  For many years, WMs are what we used and they still work. Some are highly customizable, while some others are tightly coupled to only work with a specific DE.  Gnome3+ have a tightly-coupled DE-->WM setup.  Mate and other DEs typically use an existing WM - like openbox or fluxbox.  These aren't bad.  WMs typically end in "wm" for their package names.

If you want total control and extensibility with some light-scripting (perl), then check out fvwm. Here's a link for fvwm-crystal, which is full of "eye candy".
[https://www.fvwm.org/img/fvwm-crystal.jpg]("https://www.fvwm.org/img/fvwm-crystal.jpg")
When DEs, then WMs, became too bloated for my wishes, I moved back to fvwm, which I first started using in 1994-ish. The configuration is all through text files and honestly, fvwm isn't something anyone but a perl dev would likely want.  

Openbox is a reasonable half-way point. The only bad part of openbox is that it uses XML for configuration/customization, but there is a GUI overall openbox WM configuration tool and it will find all the .desktop files your userid can access.  Just right-click anywhere empty on the desktop to see a menu.  That's something many of the DEs have broken - AND it is broken!  They want to have a menu only in the corners, not where my mouse already is.  I can only guess it is for consistency, rather than efficiency.

Should also mention that having multiple GUIs installed on a single system isn't usually bad, but using different GUIs under the same userid/account can lead to configuration conflicts.  This can happen when the different GUIs are built using the same family of GUI - so if you use xfce4 which is based on gnome2, but also use the Gnome3 (or in 21.10 Gnome4) libraries, some of the settings have changed their meaning.  So, if both DEs use the same dconf DB, it is possible that running Gnome3 will update the meaning and the values for some settings. Upgrades are to be expected and handled.  But programmers seldom make things backwards compatible - at least not with much effort/testing.  This means if we run Gnome3, then run XFCE4, under the same userid, it is likely that some settings will conflict.  Those conflicts can be gracefully handled or simply cause a DE crash.  The safest thing is to create a new userid for each different DE you plan to try out - see which ones you like and when you do finally decide, look for a migration method. After all, we all prefer the userid we use today, not the 5 others we'll create to check out 5 other DEs.
Best of all, when you are done with those temporary accounts, delete them from the system and remove the HOME directory for each - that's it.  Then you can use the package manager to remove the unwanted "desktop" packages - very little fuss over trying out a completely new GUI.

---

### Post by Dennis N on 2021-10-24
What version of Ubuntu have you installed? That's important for someone else to investigate your problem.

---

### Post by VMC on 2021-10-24
Tweaks doesn't do top bar transparency , Gnome-Extensions does.

---

### Post by tea for one on 2021-10-24
Show Applications > Extensions > Toggle extensions on/off

In the screen shot, you will see
Dash to Panel [COLOR="#0000FF"]Active[/COLOR]
Ubuntu Dock [COLOR="#0000FF"]Inactive[/COLOR]

---

### Post by mIk3_08 on 2021-10-24
> **justjeff-999 said:**
> Hello!
I recently decided to try customize Ubuntu's appearance, and I relied mainly on Gnome Tweaks to accomplish this, installing the following extensions:
- Dash-to-dock
- Transparent topbar
However, one quite annoying thing is the fact that when activating the activites, 2 application bars show up, one on the left, and the other at the bottom. I want to get rid of the bottom one. Here are some attachments of what I mean.
Is there any way to do this? Thanks! I think you can easily hide this side bar dock. There is an option on Ubuntu settings behavior. I think you can auto hide the dock in your system. just enable the auto hide in your Ubuntu System settings. Good Luck and Regards.

---

### Post by Dennis N on 2021-10-24
I for one can't duplicate the OPs situation, but based on what I can tell from my Ubuntu 20.04, in the screenshot of post #1, it appears that dash-to-dock is at the bottom, with opacity set to 0% (transparent). On the left, is the gnome dash, which should only appear when all docks are off. It is never transparent. It shouldn't be there now. You can find reports of both appearing with a web search. They seem to be years old, but may offer something useful.

Suggestion: You want the dock on the left, so what is the situation when you set dash-to-dock at the left side?

---

