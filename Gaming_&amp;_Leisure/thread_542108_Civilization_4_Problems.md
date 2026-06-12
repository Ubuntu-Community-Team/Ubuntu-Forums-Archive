---
title: "Civilization 4 Problems"
date: 2007-09-03
forum: Gaming &amp; Leisure
---

### Post by platypuz on 2007-09-03
I would like to appologize in advance if this thread is in the incorrect place as this is a problem concerning Windows XP and not Ububntu. I really couldn't think of where else to go and so here I am. Anyways, heres my problem:

I bought a copy of Sid Meiers Civilization IV Game of the Year
Edition. After installing it I immediately began to play the game, after
approximately 1 hour of gameplay I shutdown the game as well as my
computer. Later, when I wanted to play again I returned and started the
game. This time I clicked around in the startup menu a little bit more to
find out exactly what was there. After exploring the menus for a little
while I found the button that allowed me to check for new patches and
updates. After clicking on the updater and downloading the patch (patch 1.74)
the game restarted itself in order to install the patch.

As the patch was being installed I noticed that a new shortcut was added to
my desktop for launching the game. After noticing this I deleted the old
shortcut immediately, while the patch was still installing. When the patch
was nearly installed a error message popped up saying something along the
lines of not being able to find the game data to install. Once I
acknowledged the error message I looked back to the installer which told me
that it had finished its update. When I tried to start the game once again I
go tthe following error message:

"This application has failed tos tart because D3DX9_32.DLL was not found.
Re-installing the application may fix this problem."

After seeing this message I put the icon I deleted back onto my desktop in
hopes of fixing the problem. It did not work, and when I attempt to
uninstall the game via add and remove programs in the control panel it give
me the following error message:

"An error (-5004 : 0x80041f42) has occurred while running the setup.

Please make sure you have finished any previous setup and closed other
applications.
If the error still occurs, please contact your vendor: Firaxis Games
(##!DS_PRODUCT_URL##)"

When I click the Details tab the following information is displayed:

"Error Code: -5004 : 0x80041f42
Error Information
*C:\Program Files\Common
Files\Install Shield\Professional\Run Time\12\00\Intel32\iKernel.dll
>inc\CoCreate.cpp (44)
>SetupDD\SetupDLL.cpp (1390)
PAPP:Sid Meier's Civilization 4"

Any help would be greatly appreciated 

Platypuz

---

### Post by conjur3r on 2007-09-04
Have a look at your task manager to see if there are any existing civ 4 setup or anything of that nature already running.  If they are, try killing them.

Alternatively, you can just reinstall the game from the CD.  Download the patch manually and apply it.

---

### Post by zorkerz on 2007-10-26
did you ever find a solution?

I would say it looks like a borked install somehow and would try to find a way to reinstall it. The dll file it was missing can be found online if you need it but I like to avoid hacks like that and it seems to have other problems also.

---

