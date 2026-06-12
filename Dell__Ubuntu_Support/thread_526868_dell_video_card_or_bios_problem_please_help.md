---
title: "dell video card or bios problem? please help"
date: 2007-08-16
forum: Dell  Ubuntu Support
---

### Post by doogiekd on 2007-08-16
hi all. I have installed feisty on a dell dimension destop. (i am re-posting this with more information now.)

there are several problems which i think are related to the video card configuration:

1. Display on monitor is garbage on boot up. 

i have to "re-boot" the monitor by turning it off and on again after ubuntu loads to the login screen. doing this fixes the problem but is annoying.

2. shutting down system stops.

satus bar emties and computer "clicks" as though shutting down but reamins on with ubuntu logo on monitor. holding down the power button on computer then shuts computer off completely. (again, annoying.)

3. WINE forces reboot of computer loading winecfg (with problem #1.) and will not run.

brings user back to login screen. Big Problem not being able to use my Final Draft screenplay writing software!

4. The following message is displayed when ubuntu loads from grub (not exactly but it only displays for a second but here is the gist of it):

"acpi force required to enable bios 1999 fails cutoff acpi mem failed to locate: mem resource #6 pci"

notes on computer:

dell dimension
pentium 3 498mhz
256 ram
phoenix bios 4.0 1985-1999

video card:
voodoo3

in bios video is:
agp enabled (with choice of selecting pci
agp aperature 64mb enabled (with choice of selecting 256mb)

dual system (two hard drives) running windows xp with no problems at all except slow
ubuntu is on second (slave) hard drive with adequate memory.

worried about changing bios video settings and damaging video card :(

any help would be helpful :) thanks

---

### Post by ridgeland on 2007-08-16
Since it's been a day with no reply, I'll venture a some guesses.
Does the PC have both video on the mother board and a video card?  Two possible places to plug in the monitor?  If so then the BIOS setting might not be using the same plug you're using.  May not be an issue but is worth checking.  With mother board video Dell takes part of the precious RAM and uses it for the video.

Can you put more RAM in the PC?  256 is border line too little.  I recently upgraded a friend's Dell with 128 MB running XP.  She could launch Word then go fix a cup of coffee while the PC trashed about loading the program.  I added 512 of RAM for $50 and she couldn't believe the difference.  She clicks on a program and in just a couple of seconds it's loaded, while she waits!  My old Gateway (P5 - 200MHz) has a max of 256MB.  On it I run Xubuntu not Ubuntu.

Incomplete shutdown is a common problem with old PCs.  My old Gateway has the same problem.  One thread's solutions:
[http://ubuntuforums.org/showthread.php?t=359190](http://ubuntuforums.org/showthread.php?t=359190)
This thread talks about acpi I think.

---

### Post by jacob01 on 2007-08-17
if there is an internal video and a card the internal should be dissabled since you are not using it so plug the monitor into the card
also are you using the correct drivers for the video card ?

---

### Post by Paulmd on 2007-08-18
> **doogiekd said:**
> hi all. I have installed feisty on a dell dimension destop. (i am re-posting this with more information now.)

there are several problems which i think are related to the video card configuration:

1. Display on monitor is garbage on boot up. 

i have to "re-boot" the monitor by turning it off and on again after ubuntu loads to the login screen. doing this fixes the problem but is annoying.

2. shutting down system stops.

satus bar emties and computer "clicks" as though shutting down but reamins on with ubuntu logo on monitor. holding down the power button on computer then shuts computer off completely. (again, annoying.)

3. WINE forces reboot of computer loading winecfg (with problem #1.) and will not run.

brings user back to login screen. Big Problem not being able to use my Final Draft screenplay writing software!

4. The following message is displayed when ubuntu loads from grub (not exactly but it only displays for a second but here is the gist of it):

"acpi force required to enable bios 1999 fails cutoff acpi mem failed to locate: mem resource #6 pci"

notes on computer:

dell dimension
pentium 3 498mhz
256 ram
phoenix bios 4.0 1985-1999

video card:
voodoo3

in bios video is:
agp enabled (with choice of selecting pci
agp aperature 64mb enabled (with choice of selecting 256mb)

dual system (two hard drives) running windows xp with no problems at all except slow
ubuntu is on second (slave) hard drive with adequate memory.

worried about changing bios video settings and damaging video card :(

any help would be helpful :) thanks


Dell Bios revisions are in the format A01, A02, etc, you can find out what bios revision you really have by hitting f1 at POST.

Dell computers often benifit from bios updates. look at support.dell.com and see if a newer revision is available.

If it new your model number, i'd be able to check the revision history for changes to acpi.

---

