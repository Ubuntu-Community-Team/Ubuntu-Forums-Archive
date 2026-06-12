---
title: "Skip Logon?  and Virtual Box?"
date: 2008-08-06
forum: Desktop Environments
---

### Post by Bigjake52 on 2008-08-06
Ok Question Number 1,

Can i have ubuntu Log in by it's self?  There is nothing important on my ubuntu computer for me to have a pass word on it,  So is there a way i can skip the pasword?

Question Number 2

How well dos xp emulated in virtual box run I just need a game called war lords2  or is there a better virtual app.  I would like a short cut on porgams from xp in ubuntu?  Also war lords is a dos porgram.  thanks a bunch

:confused:  Im so very new to ubuntu

---

### Post by DaneM on 2008-08-07
Q1: System -> Administration -> Login Window -> Security (tab) -> Enable Automatic Login.

Q2: VirtualBox works very well for most things.  I don't know how well it will work for your game, but I have run Windows XP under it with no problems.  Be sure to install the guest addons once you have booted into Windows, from the menu at the top of the virtual machine's window.  This will give you 3d acceleration, if available, and some other nice features.

I'm not sure what you mean about shortcuts to XP programs.  Are you using a Windows emulator (such as WINE)?  If so, you'll need to follow a wine HOW-TO for the specific programs, if one exists.  Some Windows programs work in Linux, while others do not.

--Dane

---

### Post by evets25 on 2008-08-07
Vitualbox doesn't work for games. If an OS is virtualized, that means that it doesn't have direct access to your video card, which means no 3d acceleration, which means no games. If it's a windows app, you want wine, a progam that allows you to run windows apps under Linux. If it's an old DOS app, not a windows app, then you want DOSbox, a dos emulator. Both are available in the repositories. For running games, virtualbox or any other kind of virtualization isn't really what you want.

---

