---
title: "Trying to play ANYTHING- and it's not working!"
date: 2007-10-29
forum: Gaming &amp; Leisure
---

### Post by variableenigma on 2007-10-29
I've been trying to find games to play on my Dell Latitude D620 running Ubuntu 7.10, but I'm having a lot of trouble.

I've installed Adonthell, Attal, Balazar, EgoBoo, (GNOME, Qt, X) NetHack, KQ, LostLabyrinth, The Mana World, and Widelands using the Add/Remove Application. I've also installed Regnum Online and PlaneShift using the downloads from their respective websites.

Now. The only game that SORT OF works is KQ, which is nice, but I was hoping for something a little more complex.

Here are the problems I'm having:

Adonthell, Attal, Balazar, EgoBoo, (GNOME, Qt) NetHack, LostLabyrinth, The Mana World, and Widelands simply won't open when I click on them in the Applications/Games menu. Nothing happens at all, actually.

X NetHack opens a window, but then it freezes before anything shows up inside it.

Regnum Online allows me to log in, but then it gives me a "Unsupported video card!" window that says:
"There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version"

PlaneShift seems to have been installed, but I do not have permission to access it (even when I run as root). I had to install it as root just to get it to install at all, but now I can't play it.

I've looked all over the internet to figure out my graphics card and driver situation, but I honestly can't find anything beyond this:
I have an Intel 945GM graphics card and the i810 driver (or at least that's what I think that information means). 
I have no idea if this is the latest driver for my graphics card or not. I also have no idea where to get the latest one if this isn't it.

I'm so frustrated and I'm really at my wit's end here. I need serious help figuring this stuff out.. Any tips would be appreciated!!

---

### Post by Achetar on 2007-11-01
Try using the Restricted Drivers Manager, that may do it for you (System->Restricted Drivers manager)

---

### Post by cogadh on 2007-11-01
The Intel driver is not all that good at doing much more than displaying your desktop. AFAIK, the i810 driver is the latest available for that card.

---

### Post by acoustibop on 2007-11-02
If you're having problems starting an application, variableenigma, always try starting it from a terminal.  This should get you more information in the terminal output as to why your application won't start.

---

### Post by ikkefc3 on 2007-11-02
> **variableenigma said:**
> 
Regnum Online allows me to log in, but then it gives me a "Unsupported video card!" window that says:
"There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version"

PlaneShift seems to have been installed, but I do not have permission to access it (even when I run as root). I had to install it as root just to get it to install at all, but now I can't play it.

This is because it are Windows only games.
You don't have DirectX, because that's a Windows only 3D API.

You cannot run planeShift, because it you haven't gave it the permission to run.
For Windows games (like your planeshift) you could try Wine (Free) or Cedega ($15).

---

### Post by cogadh on 2007-11-02
Actually, Regnum produces that error regardless of the OS used, it is a generic error common to all versions of the client. Both Regnum and PlaneShift have Linux native clients and do not require Wine or Cedega to run.

---

### Post by hikaricore on 2007-11-02
I've tried Regnum on an intel card before and had about the same trouble.

It may just not be possible to play with said video hardware.

---

### Post by mysticmatrix on 2007-11-02
> **hikaricore said:**
> I've tried Regnum on an intel card before and had about the same trouble.

It may just not be possible to play with said video hardware.

+1. Only hope for you may be to try experimental 'intel' driver. I have a Intel X3000, and I was able to play games only after Gutsy updated my video drivers.

---

### Post by trash on 2007-11-13
> **cogadh said:**
> The Intel driver is not all that good at doing much more than displaying your desktop. AFAIK, the i810 driver is the latest available for that card.

Intels site says that the intel driver is the recommended... I tried the i810 and actually got the same poor fps... 0-1.5 fps runing Balazar... how sad:(

I have also read somewhere that the newer intel driver replaces i810

---

