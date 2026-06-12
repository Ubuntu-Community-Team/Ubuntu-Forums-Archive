---
title: "My Lucid not booting after hibernate."
date: 2012-02-01
forum: Desktop Environments
---

### Post by alexsirb on 2012-02-01
Hi all! I installed ubuntu 10.04 with wubi, because i did not want to create a linux partition at the moment. After working all night at a personal project, i decided to put it to hibernate, cuz i had a lot of windows open. I got an error at the end: not enough swap, or something like that. Problem is that i get a GRUB console. I wrote just for curiosity "root" in the console. Said something about Filesystem is NTFS. How do i restore my grub config? I really need to get going on my project. What should i write to boot? It's a generic configuration, i think. The basic kernel arguments for an ubuntu on ntfs inside a squashfs. It's been a long time since i played with GRUB, and i don't remember how to boot a system, especially this one. I just need it to boot, no matter what. I'll take care of the rest.
Thank you.

---

### Post by bcbc on 2012-02-01
So hibernate failed - which means you were still running Ubuntu. Then you shutdown normally after that, and then whenever you reboot you get a grub prompt? Is that correct? 

Because normally a grub prompt at boot time means that there's a problem with the root.disk: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

But attempting to hibernate shouldn't cause corruption (hibernation is not supported on a wubi install, but should just give you an error and resume - as if you'd suspended and resumed). 
Or did you hard power off?

---

### Post by alexsirb on 2012-02-01
Well... i think the system was halted.  The screen was cleared and there were 2 or 3 lines... and one of them saying that there is not enough swap space for hibernation. I pressed the reset button. What else should I do? As far as I remember, I tested NumLock, and it didn't do anything... just stood green at me. Now I'm running Gates, because GRUB doesn't load the kernel. I'll check that link and I'll post back. Thanks

Edit: True. Files were missing. No "disks" folder. I didn't get to read it all, but was something with chkdsk. I remembered that I started Gates XP from another hard drive, and was checking drive G: and i went to G:\ubuntu. No "disks" folder. Look! a "found.000" on root of G:! Could it be "disks"? - i said to myself. A little attention from members of this forum, and my problem is solved!

Thank you bcbc!
Now i can continue my project on getting a linux GUI onto my Eten G500+

---

### Post by bcbc on 2012-02-01
You can always safely reboot using Alt+SysRq R-E-I-S-U-B

This is recommended for any install instead of powering off, but Wubi is more sensitive to this because the virtual disk is stored as a single file.

---

### Post by Paddy Landau on 2012-02-01
WUBI has some restrictions, one of which is that hibernate does not work.

This used to be documented on the WUBI page, but now I don't see it there.

---

### Post by alexsirb on 2012-02-01
I didn't know about this restriction and it's not something i use everyday, but i was very tired and that's what came in mind. Now it's ok. I think. I found the missing files, but i didn't test it. It should work though. I'm busy with something else now, related to my project. When i need to connect my ETEN G500+ to linux, i will reboot and see the results

---

### Post by alexsirb on 2012-02-01
> **bcbc said:**
> You can always safely reboot using Alt+SysRq R-E-I-S-U-B

This is recommended for any install instead of powering off, but Wubi is more sensitive to this because the virtual disk is stored as a single file.

Alt+SysRq R-E-I-S-U-B? What is that?

---

### Post by bcbc on 2012-02-01
> **alexsirb said:**
> Alt+SysRq R-E-I-S-U-B? What is that?

[http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot](http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot)

---

### Post by Paddy Landau on 2012-02-01
> **alexsirb said:**
> Alt+SysRq R-E-I-S-U-B? What is that?
REISUB (which reads BUSIER backwards) is an emergency reboot when nothing else seems to work, not even Ctrl-Alt-Delete.

SysRq is usually the PrintScreen button on your keyboard, so *Alt**-SysRq-R* would be *Alt-PrintScreen-R*.

This is how it works:

```
Alt-SysRq-R   [FONT=Verdana]Tells Linux to **R**elinquish control to your keyboard.[/FONT]
Alt-SysRq-E   [FONT=Verdana]Sends a terminate command ("please **E**nd nicely") to all running applications.[/FONT]
              [FONT=Verdana]Wait about 90 seconds before proceeding.[/FONT]
Alt-SysRq-I   [FONT=Verdana]Sends a forced **I**mmediate terminate command ("OK, if you won't terminate nicely, I'll[/FONT]
              [FONT=Verdana]force you to end!") to the those applications that haven't responded.[/FONT]
              [FONT=Verdana]Wait about 10 seconds before proceeding.[/FONT]
Alt-SysRq-S   [FONT=Verdana]**S**ynchronises (writes all outstanding) data on all disks to reduce data loss.[/FONT]
Alt-SysRq-U   [FONT=Verdana]Remounts all disks read-only to prevent any further writes.[/FONT]
              [FONT=Verdana](I don't know what the **U** stands for.)
[/FONT]Alt-SysRq-B   [FONT=Verdana]Re**B**oots the computer.[/FONT]
```There is often no feedback to any of the commands except for the last one; if it doesn't reboot immediately, your only recourse is the power button.

EDIT: bcbc's link shows what the letters stand for.

---

### Post by alexsirb on 2012-02-01
Thank you guys for sharing info. Experience isn't done by snapping fingers. It takes time, and it is consuming. You knew what to search for. Thank you.

---

### Post by Paddy Landau on 2012-02-02
It's a pleasure. If this has answered your problem, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by alexsirb on 2012-02-02
I booted Lucid totay and it works like it should. Thank you

---

