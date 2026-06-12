---
title: "Uses only half of RAM"
date: 2012-10-22
forum: Desktop Environments
---

### Post by manganganath on 2012-10-22
Hello, I'm using WUBI 12.04 on my pc with core i7 64-bit processor and 4GB RAM. Inside ubuntu, it shows less than half of the RAM (1.8GB). However in windows, it takes full RAM. I want to know how to use full RAM memory inside Ubuntu 12.04. Any help would be appreciated.

Thanks!

---

### Post by mardybear on 2012-10-22
Hi manganganath.

Even when you try to overload your system it still just uses half of your ram?

I use 8.04 and 10.04 (not 12.04), but i believe you should also be able to tweak your /etc/sysctl.conf file to adjust how your system utilizes your ram and swap file. Just forum or google search to find more info. I've pasted the last couple lines of my sysct.conf file for reference below. Note, you'll have to work as the root user, so be careful and backup this file before tweaking. You may also need to reboot your system to activate the changes. Maybe this will help.

vm.swappiness=10
vm.vfs_cache_pressure=50

mardybear

---

### Post by manganganath on 2012-10-22
Hello mardybear,

Thanks for the quick reply. The swappiness on our machine is 60 and vfs_cache_pressure is 100. 

The problem that our laptop has 4Gb of ram (hardware) but in the ubuntu environment we only see 1.8Gb of ram ([see picture]("http://i.imgur.com/EbfKk.png")).

We increased the swap to 4Gb, but the system is still slow from only using half the hardware ram. 

After searching the forums and google, we can't seem to find anyone else with our problem. Yet both my laptop and a desktop in the lab running wubi 12.04 lts show only half the system ram.

Any other ideas for getting our full ram?


Regards,
manganganath

---

### Post by mardybear on 2012-10-22
Hi again...

I believe you're using the default swappiness and vfs_cache_pressure settings. They can easily be tweaked to use all of your RAM and minimize or negate swap use, but that's not your issue...i misunderstood...please disregard my previous post.

Me not sure why Ubuntu is only showing half of your installed RAM. Hopefully someone else on the forum will be able to help. If you run 'top' or 'htop' in terminal, does that also show the wrong amount of RAM installed? It may be related to your BIOS settings but someone else would know better.

FYI: Unrelated to your present issue, i was under the impression that with large RAM systems like yours minimal or no swap was even required.

Good luck,

mardybear

Edit: Sorry i just rechecked your screenshot. Not sure how many processes your running, but you are still only using about 1/4 of your available RAM, so your slow system concern may be another issue altogether.

Another edit: Although this linked thread did not appear to get fully resolved, it may provide a clue. Did you install the 32 or 64 bit version of Ubuntu?

[http://www.linuxquestions.org/questions/linux-newbie-8/incorrect-memory-ubuntu-902907/](http://www.linuxquestions.org/questions/linux-newbie-8/incorrect-memory-ubuntu-902907/)

---

### Post by manganganath on 2012-10-22
Hey mardybear,

when using top is shows us half the ram that we have in the hardware and the screenshot was taken when we weren't running many processes. We did install the 64bit wubi as well. 

If the correct amout of RAM is showing up in windows, can it be the bios that is affecting the ubuntu environment? I thought it would affect both in the same way.

Any other suggestions? :)


Regards,
manganganath

---

### Post by mardybear on 2012-10-22
> **manganganath said:**
> If the correct amout of RAM is showing up in windows, can it be the bios that is affecting the ubuntu environment? I thought it would affect both in the same way.
Me again. I believe you are correct, since your Windows shows correct it's probably not your BIOS but...

As a root user, what happens when you enter 'sudo lshw' into the terminal? Does it show the correct amount of RAM on your system? Check under the memory section. Mine's pasted below and is correct, a whole 512MB ram - yes i'm from the stone age :)

*-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 256MiB
             width: 64 bits

If your system does not have a dedicated graphic chip, then the BIOS may be reserving some of your RAM for video. One last thing i would check is the BIOS (enter BIOS during initial computer boot) to see if you can find a reference to reserving video memory. Long shot but that might explain why your Ubuntu systems aren't showing all of your hardware RAM as being 'available'.

Get back to the group and if no go then someone else will hopefully be able to jump in...

mardybear

---

