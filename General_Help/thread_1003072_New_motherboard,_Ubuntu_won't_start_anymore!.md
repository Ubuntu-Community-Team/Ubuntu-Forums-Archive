---
title: "New motherboard, Ubuntu won't start anymore!"
date: 2008-12-05
forum: General Help
---

### Post by reydempto on 2008-12-05
So I was given a used MSI 845 Ultra-C Motherboard. It's nothing too amazing, but better than my OEM board. I put my P4, 1024 MB RAM and ATI Radeon X1300 inside. Then I added my 40gb main HDD and my 320Gb slave HDD. I triple-checked that everything was seated properly, like a good boy.

Finally I start 'er up. Everything is going fine, GRUB loads as usual, but when it comes to starting up Ubuntu 8.10, everything goes significantly slower. Even the orange loading bar underneath the logo moves slow as molasses.  also, the desktop never loads. it never leaves the boot screen. I decided to put everything back into my Dell mobo, and it still did the same thing. Here's the weird thing--I put all my guts into my girlfriend's dell (we both have former Dimension 2400's) and everything worked properly. I took that opportunity to do a clean format/install of ubuntu 8.10, then threw everything back into my original motherboard. still no dice. 

NOW it's back in my NEW motherboard, since it seems to make no difference. 

I managed to boot the live disk, and access a Terminal, but I am not sure where to go from here, as I am still learning.

The thing that really confuses me is that somehow my old mobo stopped working, as has my new one, yet my cpu, ram, dvd drive, and both HDD's have been tested successfully in another computer.    O.o


Anyone have any ideas?

---

### Post by dexter on 2008-12-05
You could try booting up without the splash screen. This should give you an idea what is taking so long.

- When grub shows up, select you kernel and press 'e' (edit), 
- Navigate to the line that start with kernel and press 'e'
- Remove "quiet splash" and hit enter
- Press 'b' to boot the kernel

---

### Post by 6205 on 2008-12-05
linux is not windows, so forget working plug and play.

i you have changed motherboard, you have to format and reinstall entire system to get normal, stable system...
btw. stablility not linux strong side anyway..

---

### Post by reydempto on 2008-12-05
Well, it spit out quite a lot of information, as expected, but towards the end i get this:

"Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/8de63332-9ba0-4947-89ad-70d0cac26ecd does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of commands

(initramfs)"

Is there any way to straighten this out?

---

### Post by kthakore on 2008-12-05
ALERT! /dev/disk/by-uuid/8de63332-9ba0-4947-89ad-70d0cac26ecd does not exist. Dropping to a shell! 

means that ur devices are mapped differently now. uuid is unique for different motherboards. You can reinstall ubuntu (which I would recommenced). Another alternative is to only reinstall the root directory. To do this copy ur /home directory to a temp storage and reinstall ubuntu with the same user name as ur old system and copy back the home folder. 

If these are inapplicable you can load boot cds and edit /etc/fstab and regenerate uuids for each /dev devices in there. This can be done using 
```
 ls -lh /dev/disk/by-uuid/ 
``` 

form here [http://ubuntuforums.org/showthread.php?t=425057](http://ubuntuforums.org/showthread.php?t=425057)

---

### Post by caljohnsmith on 2008-12-05
How about on start up when you get the Grub menu, select Ubuntu, press "e" to edit it, select the "kernel" line, press "e" to edit it, then add the following at the end of the kernel line:
```
acpi=off all_generic_ide rootdelay=120
```
Then press enter to save the change, and finally "b" to boot. See if that makes any difference, and if so, let me know exactly what what new errors you get if any.

---

### Post by reydempto on 2008-12-05
i would love to do a clean install, but for whatever reason, it takes forever to read anything off of my dvd drive, whereas it used to run very smoothly. In fact, when i put in the install disc and selevt "Install", it goes to a black screen with a flashing " _ " and eventually it leads to the same initramfs shell thing....   O.o


although i AM able to "run w/o any changes to your computer" and access the terminal, i just have no idea what i can do..

---

### Post by reydempto on 2008-12-05
> **caljohnsmith said:**
> How about on start up when you get the Grub menu, select Ubuntu, press "e" to edit it, select the "kernel" line, press "e" to edit it, then add the following at the end of the kernel line:
```
acpi=off all_generic_ide rootdelay=120
```
Then press enter to save the change, and finally "b" to boot. See if that makes any difference, and if so, let me know exactly what what new errors you get if any.

will do, just gonna warn you it will take a while...this pc is running unusually slow.

---

### Post by Grolsche on 2008-12-05
If the entire boot up process is running slower than expected, especially  before it goes into boot, I would recommend going in to bios and selecting it to run default settings. It might be possible that the motherboard bios has different settings for another computer and something in  your computer isn't compatible with the settigns selected. By selecting default settings this should clear that issue.

If it still runs slow after that, try pulling out the memory, oh and are you sure the memory is the correct speed for the motherboard. 

Your memory for that msi board needs to be  DDR PC2700 or DDR PC3200. If it's not then that might be your problem.

---

### Post by reydempto on 2008-12-05
> **Grolsche said:**
> If the entire boot up process is running slower than expected, especially  before it goes into boot, I would recommend going in to bios and selecting it to run default settings. It might be possible that the motherboard bios has different settings for another computer and something in  your computer isn't compatible with the settigns selected. By selecting default settings this should clear that issue.

If it still runs slow after that, try pulling out the memory, oh and are you sure the memory is the correct speed for the motherboard. 

Your memory for that msi board needs to be  DDR PC2700 or DDR PC3200. If it's not then that might be your problem.

My ram is PC2700, so it should be good. I will try doing the bios defaulting in a bit....


caljohnsmith, i did what you said. after a bit of loading, I reached my login screen, and now am on my desktop. the problem now is everything is running amazingly slow....would that bios settings trick mentioned above affect this?


EDIT: actually that didn't make any difference....it still boots slower than slow..it's been sitting here for ten minutes... "Starting up ... "

---

### Post by LateNiteTV on 2008-12-05
> **6205 said:**
> linux is not windows, so forget working plug and play.
 
i you have changed motherboard, you have to format and reinstall entire system to get normal, stable system...
btw. **stablility not linux strong side anyway**..
 
i take it youve never used anything but ubuntu huh? ;)

---

### Post by caljohnsmith on 2008-12-05
> **reydempto said:**
> 
caljohnsmith, i did what you said. after a bit of loading, I reached my login screen, and now am on my desktop. the problem now is everything is running amazingly slow....would that bios settings trick mentioned above affect this?
Since Ubuntu on both your HDD and your DVD drive both run slow, and also since Ubuntu on your HDD works OK in your girlfriend's computer, then I agree with Grolsche that you should look at resetting your BIOS settings; if that doesn't work, then I would play around with the BIOS settings to see what makes a difference with your booting problems. Good luck and let us know how it goes. :)

---

### Post by Grolsche on 2008-12-05
Also, just try reinstalling your ram. It's amazing just what it might do if all else fails. I installed ubuntu on my laptop and it was running very slow, i found that swapping the ram from 1 slot to the other worked for me too.

---

### Post by reydempto on 2008-12-05
I tried switching my ram around, also tried a messing with the bios settings a little. no noticeable difference to report..

My roommate suggested updating my new motherboard's bios, since it is a few years old..before i go through the trouble, does anyone think that'll help?

---

### Post by Grolsche on 2008-12-05
I take it you tried the default bios settings?

You could try updating it, but to be honest I aint sure that's gonna make much of a difference.

---

### Post by reydempto on 2008-12-05
yeah i set them to default settings and also "default high-end settings" to no avail...

---

### Post by Grolsche on 2008-12-05
Does your motherboard have inbuilt video? If it does just try taking out your graphics card and see if it boots normally without that. If it boots normally without it then we can start on ideas about the graphics. It's just a last minute thought with the results seen so far.

---

### Post by Zorael on 2008-12-05
> **6205 said:**
> linux is not windows, so forget working plug and play.

i you have changed motherboard, you have to format and reinstall entire system to get normal, stable system...
btw. stablility not linux strong side anyway..
What

---

### Post by reydempto on 2008-12-05
> **Grolsche said:**
> Does your motherboard have inbuilt video? If it does just try taking out your graphics card and see if it boots normally without that. If it boots normally without it then we can start on ideas about the graphics. It's just a last minute thought with the results seen so far.

nope ... no onboard graphics card :(

i could cry at this point

---

### Post by Grolsche on 2008-12-05
ok, just try this then go in to the bios and ensure its recognising the graphics card size and config correctly.

Also, you could try reinstalling the graphics card again.

Apart from that, i'm afraid its coming to the end of my knowledge.

---

### Post by caljohnsmith on 2008-12-05
Have you checked that your power supply can meet the power requirements of your new mother board? If you have an electronic multimeter, I would check all the power supply voltages with the motherboard connected and see if any of the voltages are getting pulled down from too heavy of a load.

---

### Post by reydempto on 2008-12-05
> **caljohnsmith said:**
> Have you checked that your power supply can meet the power requirements of your new mother board? If you have an electronic multimeter, I would check all the power supply voltages with the motherboard connected and see if any of the voltages are getting pulled down from too heavy of a load.

if that were the case, wouldn't everything be fine once i put my original mobo back? everything runs slowly on my original dell board now too.

---

### Post by Grolsche on 2008-12-05
did u try my other suggestion? on page 2?

---

### Post by reydempto on 2008-12-05
> **Grolsche said:**
> ok, just try this then go in to the bios and ensure its recognising the graphics card size and config correctly.

Also, you could try reinstalling the graphics card again.

Apart from that, i'm afraid its coming to the end of my knowledge.



Yeah i couldn't find ANYTHING video resolution related in my bios settings, so i figured my bios just didn't have the option. Sorry i didn't report, i'm a little flustered (to say the least)

---

### Post by caljohnsmith on 2008-12-05
If you overstress the power supply, it could be it has low voltages now for any motherboard you plug into it; that might explain why your old motherboard also has problems when you swap it back in. It seems like you've eliminated many other possible causes of the problem, so I think that a power supply problem is a possibility at this point.

---

### Post by Grolsche on 2008-12-05
You need to look for a option to do with agp, providing its an agp graphics card.

Normally its something like AGP APERATURE SIZE: With options like 128mb, 256mb etc.

If you find that, then your int he right place to check all the other settings are reporting correctly.

---

### Post by reydempto on 2008-12-05
Oh, computers.


man, maybe that's what it is. After all, its the only thing that i haven't tested...i'm gonna look in my pile of computer parts to see if i have a supply that would make a difference :P

by the way i found the AGP APERTURE option. it was in the DRAM timing section.

but would a power supply failure really result in this every time i boot?  :

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/8de63332-9ba0-4947-89ad-70d0cac26ecd does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of commands

(initramfs)

---

### Post by reydempto on 2008-12-05
i give up lol. i'm all about fixing things for oneself, but i think i'm just going to buy a new computer.

that is if nobody knows what the heck is going on...i switched to another power supply with the same results...

---

### Post by Grolsche on 2008-12-06
and i take it you looked again in the bios for the agp aperature size?

---

### Post by reydempto on 2008-12-06
Yes, yes i did. Also last night, i decided to try booting the live disc, then installing from there. it took most of the night, but i managed to do a clean install with my new motherboard, but it still didn't make any difference. i still get the same message, but this time with a different uuid for my hdd:

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/55163086-8dd7-45018688-207a58607265 does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of commands

(initramfs)

---

