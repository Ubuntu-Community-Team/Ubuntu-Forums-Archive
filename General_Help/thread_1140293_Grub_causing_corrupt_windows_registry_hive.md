---
title: "Grub causing corrupt windows registry hive?"
date: 2009-04-27
forum: General Help
---

### Post by DakotaMalamute on 2009-04-27
This problem has happened twice in a few days.

I am dual booting Ubuntu 8.10 and WinXP Pro through GRUB. Everything was working fine for several days after setting up the dual boot, then one day when I tried to boot Windows, I was presented with a message right after Grub, saying that ...SYSTEM32\CONFIG\SYSTEM is corrupt or missing.

I went into my Windows partition to check, and the file is there. So, this means that for some reason the Windows System registry hive was corrupt. I thought it was a Windows problem, so I used my XP disk to perform an automated repair, and this fixed the hive.

Then today, two days later, the same problem has happened. This leads me to believe that the problem is not necessarily Windows related.

One of my friends who works for ITS here at the university says that Grub has a tendency to cause registry errors with Windows. My search online has yielded only suggestions for fixing the registry, not for fixing the source of the problem.

Can anyone confirm the cause of this problem?


I am dual booting the OSs on a single SATA drive.
System stats report:
[http://www.personal.psu.edu/cwf5034/hardinfo_report.html](http://www.personal.psu.edu/cwf5034/hardinfo_report.html)

I should also note that the windows partition is visible (but not mounted) in Ubuntu. I wanted to hide it, but I can only find mediocre information on how to do that. i.e. most information is how to hide ALL drives.

---

### Post by buck2825 on 2009-04-27
my wife is having this issue on her laptop as well, with 8.10/vista i just thought it was windows being windows.

---

### Post by Niniel on 2009-04-27
I fail to see how Grub could possibly have any interaction at all with anything, particularly the Windoze registry.
It's a boot manager, it only loads the OS, it doesn't touch any files. 
Or did you install Grub for Windows?

---

### Post by coffeecat on 2009-04-27
I fail to see how on Earth grub could affect the Windows registry. In four years' use of Linux, dual-booting with Windows on more than one machine, and as a member of a few Linux forums, I've never encountered or heard of this.

I don't dispute that the registry is getting corrupted - it's the weak point in Windows. But I would interested to know where your friend has heard of this "tendency of grub".

---

### Post by DakotaMalamute on 2009-04-27
> **Niniel said:**
> I fail to see how Grub could possibly have any interaction at all with anything, particularly the Windoze registry.
It's a boot manager, it only loads the OS, it doesn't touch any files. 
Or did you install Grub for Windows?

Just regular Grub that ships with the Ubuntu distro.

I should note, too, that I had Windows installed by itself for a few months before I reinstalled Ubuntu, and these problems did not start happening until after Ubuntu was installed.

---

### Post by DakotaMalamute on 2009-04-27
I was just talking to previously-mentioned ITS friend. I misinterpreted what he said.

His thought is not that Grub is directly corrupting the registry. His thought is that the errors are occuring due to the fact that Grub is displacing the Microsoft boot protocol.

I'm not sure what effect this has, but I wanted to put this information here in case it helps someone diagnose the issue.

Thanks again for all the input so far!

---

### Post by coffeecat on 2009-04-27
Grub stage 1 replaces the mbr, which is only about 400 bytes in length. The Microsoft "boot protocol" is a fairly complex bunch of files and executables that live in C:\Windows and, no, grub doesn't replace that. The function of the Windows mbr is to call ntldr (I believe, but I'm happy to be corrected). All that happens with grub is that if you choose Windows from your grub menu, grub stage 2 calls the same process as the Windows mbr would have done.

But ask your friend this question: seeing as grub cannot write to a Linux filesystem, let alone a Windows one, how can it corrupt the registry?

---

### Post by lisati on 2009-04-27
In addition to the previous posters' musings wondering how Grub could mess with Windows, I'm wondering if it's a symptom of something else that coincidentally showed up about the time Grub was installed.

---

### Post by Niniel on 2009-04-27
Yes, the only problem people "tend to have" with Grub and Windows is when Windows overwrites the MBR wiping out the boot manager. 

So what you did, Dakota, was actually the best scenario - install Windows first, and Linux second. 

I recommend you start looking at your Windows disk - run a scandisk/cchkdsk to see if there are disk errors.

---

### Post by DakotaMalamute on 2009-04-27
> **lisati said:**
> In addition to the previous posters' musings wondering how Grub could mess with Windows, I'm wondering if it's a symptom of something else that coincidentally showed up about the time Grub was installed.

I thought about that, though I have found other people with the same problem around the same circumstances (and no solutions) in a few places on the internet, so it makes me wonder.

> **Niniel said:**
> Yes, the only problem people "tend to have" with Grub and Windows is when Windows overwrites the MBR wiping out the boot manager. 

So what you did, Dakota, was actually the best scenario - install Windows first, and Linux second. 

I recommend you start looking at your Windows disk - run a scandisk/cchkdsk to see if there are disk errors.

I hope to have time this week to spend an hour-or-so to run a Windows auto repair and reconfigure my drivers again. I'll run some scans. I ran chkdsk last time and it uncovered no problems, but I'll do it again.

On a possibly related note, Ubuntu is acting increasingly unstable lately. X keeps glitching and hanging now and then, usually to the point that I cannot restart X nor switch to a bash shell, and I have to reset the machine.

I'm going to run a memtest. I'll report how that goes.

---

### Post by coffeecat on 2009-04-27
> **DakotaMalamute said:**
> On a possibly related note, Ubuntu is acting increasingly unstable lately. X keeps glitching and hanging now and then, usually to the point that I cannot restart X nor switch to a bash shell, and I have to reset the machine.

I'm going to run a memtest. I'll report how that goes.

That's interesting: getting Windows registry problems and Ubuntu becoming unstable. I agree a memtest is a good idea, or perhaps thinking about hardware faults in general. Linux is more likely to uncover a memory fault than Windows because of the different way Linux uses memory. By the way, you need to run memtest for a good long while to be able to be reasonably confident that the RAM is good. I believe some people advocate running it overnight.

---

### Post by DakotaMalamute on 2009-04-27
memtest just ran through two passes and returned 8+ errors.

The thing is, though, the errors were returned in different places and for different test modes for each of the passes. Would this be indicative of an incorrect memory configuration setting on the BIOS rather than a defect with the DIMMs?

I have an XFX nForce 790I Ultra SLI motherboard with DDR3 2000Mhz RAM - not standard, but the board supports it. The board allows me to have pretty much absolute fine control over the memory settings, but I left the board to set it automatically.

---

### Post by DakotaMalamute on 2009-04-27
I'm going to run some more diagnostics on the RAM (taking them out and loading one at a time into single slots), and then I'm going to create a new thread in the Hardware section. I suspect that this is a hardware issue with my RAM, either a defect or bad settings, causing errors that are in turn corrupting my registries and making Ubuntu unstable.

---

### Post by Ericyzfr1 on 2009-04-27
You could also try different hard drive with Windows or Ubuntu only to see if the issue is still present.

---

### Post by coffeecat on 2009-04-28
> **DakotaMalamute said:**
> memtest just ran through two passes and returned 8+ errors.

The thing is, though, the errors were returned in different places and for different test modes for each of the passes. Would this be indicative of an incorrect memory configuration setting on the BIOS rather than a defect with the DIMMs?

The reason for the advice to run memtest for hours if necessary is that bad RAM can pass on some cycles and not reveal defects for some time. So, as far as my understanding goes, the fact that you found errors after only two passes means you've almost certainly got faulty RAM. On another forum I read about someone needing to run memtest for more than 24 hours before revealing a defect.

> **DakotaMalamute said:**
> I'm going to run some more diagnostics on the RAM (taking them out and loading one at a time into single slots), and then I'm going to create a new thread in the Hardware section. I suspect that this is a hardware issue with my RAM, either a defect or bad settings, causing errors that are in turn corrupting my registries and making Ubuntu unstable.

I agree it's a good idea to test the sticks singly, but may I suggest something else to consider? Were the sticks installed in dual configuration? I had a motherboard a year or so ago that just wouldn't run memory sticks in dual-channel configuration, even though they were matched pairs, and passed memtest. I kept getting lockups in both Linux and Windows. Apparently this can be an issue with some motherboards, at least in the past. This was with DDR memory. 

Lastly, my apologies if my posts last night seemed blunt. I was a bit tired. I hope you get this sorted. Good luck.

---

