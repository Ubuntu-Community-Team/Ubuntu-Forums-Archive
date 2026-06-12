---
title: "Slow reponse"
date: 2019-12-05
forum: Desktop Environments
---

### Post by Dave67 on 2019-12-05
When I click on any icon or the menu the response is slow for the DE is this an issue? Never seen this before

---

### Post by TheFu on 2019-12-05
Could be anything.
* check the system log files for problems.
* look for a failing disk drive, bad cable, failing controller
* look at memory use.  When RAM is almost fully used, the system gets slower as feedback to the user that they need to close a few applications.
* look at swap use.  Swap extended RAM and is much slower. 

All system logs should be in /var/log/ .... and subdirectories there-of.
**free -hm** will show used, buffered, and swap use.
**top** is a handy command that sorts running processes by CPU use. There are columns for RAM use.

Slowdowns can also be caused by overheating the CPU.  To relieve CPU heat, most will throttle back to slower performance.
Also, having the wrong or incorrect GPU drivers can make for slow GUI response.  If using X11, there's a /var/log/X*g file which will say which drivers are being used.  I don't know where to look for Wayland.

These days, it is always useful to say which Ubuntu version and release you are running, since so many people use different DEs and there are 4 supported releases, each popular, currently available.

---

### Post by Dave67 on 2019-12-05
I re-read my original post and I should have mentioned that this does not occur on ubuntu 1804 gnome only on mate. 

Most of the troubleshooting above I have done the logs do not shed any light. Since the pc this is on is a evaluation pc for distributions I will see how linux mint cinnamon acts I may even install  LM mate and login to it see if the same thing occurs. 

This is my desktop project  which I am adding another desktop to an existing install of a distrbution. 

Currently the install is ubuntu gnome with mate as the addon.  Its really remarkable the ram usage between the DE. Though adding cinnamon DE to ubuntu 18.04 only knocked down the ram from 1.49GB gnome to 1.3GB cinnamon. 

I have a friend in which I installed LM 18.3 cinnamon and it only used 600 to 700 MB on his HP 23 all in one.

---

### Post by TheFu on 2019-12-05
More information is always helpful.  We have to guess otherwise.

Are you using different userids for each different DE being tested?  Some DE settings can conflict between DEs.

Different DEs (all of which are optional), have different memory use.  If you want something lighter, don't use any DE, run a minimal openbox or fvwm window-manager-only setup.

---

### Post by Dave67 on 2019-12-05
No I am using the same one for all the DE's. I did try LXDE and lubuntu only with the core installed. Though I could not install software through the GUI unless I had the desktop package installed in lubuntu I  could install through the command line only LXDE would not let me either way. 

My goal is to find the most pleasant DE to use for systems that have 2Gb ram just in case a client as such a computer.  I will have to look at openbox. I really do not like xfce.

---

### Post by TheFu on 2019-12-06
Really should use different userids for each different DE.  I cannot stress this enough.  Conflicting settings is a terrible thing. At best, it wastes RAM. At worse, it breaks things and can prevent userids from being able to login at all.

LXDE uses openbox as the window manager.

fvwm is very light, but with a little customization, can create beautiful, light, desktops. There are some pre-created fvwm themes - check out fvwm-crystal, for example. [https://fvwm-crystal.sourceforge.io/screenshots.html](https://fvwm-crystal.sourceforge.io/screenshots.html)  It is in the Canonical repos. fvwm goes back to the days when everything in the GUI was configurable.  EVERYTHING.

---

### Post by Dave67 on 2019-12-06
I had no idea that different DE's needed a new user account though it makes since that I would not use a Ubuntu gnome user.  Fvwm never heard of it I will check it out maybe be its before my time using Linux in general.

---

### Post by TheFu on 2019-12-06
> **Dave67 said:**
> I had no idea that different DE's needed a new user account though it makes since that I would not use a Ubuntu gnome user.  Fvwm never heard of it I will check it out maybe be its before my time using Linux in general.

"need" is a strong word, but think a little about it.  DEs that use Gnome are likely to have settings that use the same config files, same config DB, and since different programmers are on each DE team, but need similar controls, they might come up with the same names for settings.
  
Perhaps "safer" is the better term?

OTOH, Unix will allow users to try things that might be brilliant ... or stupid.  The programs cannot tell which, so anything is allowed. It is a different philosophy than other OSes.

---

