---
title: "Problem scrolling page in Firefox"
date: 2009-04-11
forum: General Help
---

### Post by CMJ Tech on 2009-04-11
I have uBuntu 8.10 installed. When I scroll the webpage in Firefox browser or any window that requires me to scroll up or down, I see the page scrolling at the very bottom or top of the window only.  The middle section of the page does not move.  This problem started after I replaced my motherboard.  My previous motherboard was a Syntax S635MP. I had to change it when my power supply went bad and took it out. I have replace my power supply and motherboard.  My new motherboard is an EPIA ML8000A:
CPU: Via C3
Chipset: VIA CLE266 North Bridge 
         VT8235 South Bridge
Graphics: Integrated UniChrome graphics with MPEG-2 accelerator

After installing the motherboard, the system booted right up. I did not reinstall uBuntu.  Everything else appears to be working fine. I just cannot scroll any windows.

I have tried the following workaround:
[I]Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume[/I]

But the problem did not go away.

Any help would be very much appreciated!

Thanks in advance!

---

### Post by CMJ Tech on 2009-04-16
Decided to update to Jaunty.  Considering I am rather new, I think that was a mistake.  After the update completed and I restarted the system, Jaunty would not load.  I decided to reload 8.10 but ran into the same problem, it would not load.  The system would freeze during boot process.  Decided to try Xubuntu and was successfully able to load onto the system and it boots up.  

But the issue with the scrolling problem still exists.  When I use the arrows on the side of the window to scroll the page, only the very top or bottom portion of the page moves.  I can move the mouse pointer over the page and it will refresh the new position some.

---

### Post by A55umer on 2009-04-16
Sounds like a driver problem. Your graphics card sounds obscure to me, but then again im no guru. do the tutorials in this fedora forum apply to you at all?

[http://forums.fedoraforum.org/showthread.php?t=181262](http://forums.fedoraforum.org/showthread.php?t=181262)

---

### Post by CMJ Tech on 2009-04-16
Thanks for the link A55umer!  It looks very promising.

---

### Post by CMJ Tech on 2009-04-19
Just updating.  
The instructions from the fedora forums was developed for ubuntu 7.10.  I tried to follow them, but was unsuccessful.  After trying to install a few other distros including 7.10 and corrupting the grub, I had to walk away for the computer a few days.  Today I tried install of 7.10 and it work!  I no longer have the scrolling problem in firefox or other windows such as synaptic.  I will be careful doing updates, because I do not want to change something and cause the problem to return.  Maybe as I learn more about working with linux I can  learn to tackle problems like these.

Thanks A55umer for your help!

---

