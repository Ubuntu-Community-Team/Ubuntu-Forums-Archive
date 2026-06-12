---
title: "No Programs Open!!! Even after a reinstall."
date: 2009-06-22
forum: General Help
---

### Post by wittsend on 2009-06-22
Hello,
 
OK, I had 9.04 running fine for about  two - three days.  Now no programs open - at all.  The OS will boot and the cursor moves. The harddrive churns, but nothing opens.
 
Today, in desperation, I **again** completely partitioned and formatted the drive and reinstalled 9.04.  **Again** it all worked fine for about an hour.  I kept the computer on, but turned the monitor off.  About 3 hours later I had a blank screen when I turned the monitor back on.
 
 A reboot brought the OS back, but then it reverted to the "no programs open" mode.
 
All the hardware is the same.  The only change was a BIOS update on the Motherboard.  That was to resolve a shutdown issue (and that did work).  Why did it work fine for 2-3 days then go "no programs open."  Reinstalled and fine for an hour or so, the go "no programs open" again.  Reboots do not solve the problem.
 
What the .... is going on???
 
Tom

---

### Post by The Cog on 2009-06-22
Does the desktop background get displayed?
Do you see the top and bottom panels?
Can you click the Ubuntu logo and get a menu of programs?
Can you use Ctrl-Alt-F1 to get a text login prompt?

---

### Post by wittsend on 2009-06-22
**Does the desktop background get displayed?**
 
Yes, it displays the background all the time.
   The one exception was when I turned the monitor back on after about 3 hours while leaving the computer powered up. I'm not sure at what point the screen went blank in that 3 hours.
 
**Do you see the top and bottom panels?**
 
Sometimes yes, sometimes no. See next answer.
 
**Can you click the Ubuntu logo and get a menu of programs?**
 
  I just tried that (click Ubuntu logo) on a fresh boot. The panels were there on the boot up. However, the top and bottom panels disappeared when I clicked on the Ubunu logo -  and nothing opened. This occurs most often regardless of what I try to open.
 
  Once I reach this state the ONLY thing I can do is right click and get a prompt for:
"Create folder, launcher, document, Clean up by name, Keep aligned, Change desktop background."
 
**Can you use Ctrl-Alt-F1 to get a text login prompt?**
 
Yes.  I'll be somewhat abriviated regarding drive I.D., but this is what I get:
 
[    4.956504] IO  APIC resources could not be allocated.
 
19+0 records in
19+0 records out
 
kinit: name_to_dev_t(/dev/disk/by-uuid/ (*then a long drive ID number*) =d
 
ev(8,5)
 
kinit: trying to resume from dev/disk/by-uuid/ (*then a long drive ID number*)
 
kinit: no resume image, doing normal boot...
 
Ubuntu 9.04 tom-desktop tty1
 
*When I do the log in and password I get get log on information then:*
 
malloc: ../bash/parse.y2748: assertion botched
malloc: block on free list cobbled.
Aborting....
Ubuntu 9.04 tom-desktop tty1
 
*Then I get the log in prompt again.*
 
*Thanks, Tom*

---

### Post by ibuclaw on 2009-06-22
Have you tried a memtest on the machine?

To run, you reboot and select "memtest86" in the boot options menu.

Regards
Iain

---

### Post by wittsend on 2009-06-22
Not sure how to get to a "Boot Option" as I turn it on and Ubuntu loads by itself. Is there a boot option (like F-8 in Windows)? Can I run "Memtest86" once Ubuntu loads?
 
Interesting. I just booted it up and surprize! Everything is working right (for now). Does this sound like a hardware related issue? I'll reseat everything and see what happens the next time it goes wiggy.
Tom

---

### Post by CatKiller on 2009-06-22
> **wittsend said:**
> Not sure how to get to a "Boot Option" as I turn it on and Ubuntu loads by itself. Is there a boot option (like F-8 in Windows)?

It's one of the GRUB menu options. At the start of the boot sequence you'll get a message displaying for a short while (I believe the default is 3 seconds) that says "Press Esc to enter GRUB menu." Press Escape at this point. The Memtest option should be at the bottom.

---

### Post by wittsend on 2009-06-22
VERY INTERESTING.  The computer has run for hours and not had any of the issues I stated above (programs not opening).  HOWEVER, the Display, Network, Sound and Log on/off controls in the Upper Panel are missing.  I recall at some point I got a prompt that they weren't doing something right and did I want to delete them.  Desperate for any solution I did.  Could they have been causing the problem?  
 
Anyway, I re-added these functions to the panel with "add to panel" and everything still seems well - other than why did the problem start in the first place???
Tom

---

### Post by Steelmourne on 2009-06-22
That ASPCI resources error sounds like a BIOS error. If memtest didn't bring anything up, it might be the update wasn't properly applied to the BIOS.

---

### Post by The Cog on 2009-06-23
The fact that it has now worked reliably for hours makes me wonder it it's a temperature related issue. Perhaps it only plays up when it's cold. I lived for months with a machime like that.

---

### Post by terdon on 2009-06-23
Could this be a suspend/resume problem? And are you running KDE? I had a similar problem under KDE when the computer resumed from a suspend. 

Can you reproduce the error if you suspend the computer? That is, if you go into suspend and then resume is the desktop broken like you describe?

And do you have an ATI graphics card? There are various bugs posted about the new ati drivers and resume problems similar to what you describe.

See for example : [https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/361587]("https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/361587")

---

