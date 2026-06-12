---
title: "Serious booting problems"
date: 2009-04-26
forum: General Help
---

### Post by coffee yogurt on 2009-04-26
just yesterday I installed jaunty through a burned CD (used to be a windows/fedora box, now just ubuntu). after installing I successfully rebooted and proceeded to apply the simple visual changes that one does when a new OS is installed (themes, backgrounds, various programs, etc.) nothing that would affect the kernel or anything, no tweaking code.

i then shut the computer down. This is when things went south.

when i tried to boot the computer up again i got stuck with grub trying to load but failing with an error 17. after trying the prescribed methods and not having any luck i reset my BIOS settings to setup defaults (where they were yesterday) and tried the ubuntu install CD again.

upon trying this i got the language select screen and then the screen giving you the option to try ubuntu without installing, install, check memory, if i try to install or use the trial OS it simply starts spitting garbled error code at me and im stuck (though once i somehow enabled typing, though it didnt do any good)

now it seems as if my hard drive is not even recognized any more. my windows CD claims there isnt one. Ive adjusted the IDE and power cable and the drive appears to be spinning but I got nothing.

regular boot w/o CD tells me to reboot with a device attached or to insert boot media into seleced device. which i assume means it sees no hard drive so it want me to put in a boot disk.

so my best conclusion is that my hard drive is screwed, my motherboad is screwed or its just the IDE cable, or some combination of the above.

I really hope someone can look at this and tell me theres a simple software fix and i dont need to get a new HDD or something.

motherboard: asus k8v se deluxe
hard drive: seagate barracuda 250gb 7200rpm

thanks in advance.

---

### Post by ripken204 on 2009-04-26
i am having a very similar issue.
error 17 was only one of my issues.
at other times i got error 18, inode not being found, and more crap.

i am running hdd checks right now in hopes of this being sorted out.

---

### Post by coffee yogurt on 2009-04-26
yeah well my current problem is that i dont even get to the error 17 message any more, my computer wont even acknowledge my HDD. I just tryed it with another IDE cable and it still didnt work so i think i might be screwed royally.

---

### Post by nandemonai on 2009-04-26
Certainly sounds hardware related to me.

---

### Post by ripken204 on 2009-04-26
> **coffee yogurt said:**
> yeah well my current problem is that i dont even get to the error 17 message any more, my computer wont even acknowledge my HDD. I just tryed it with another IDE cable and it still didnt work so i think i might be screwed royally.

mine was doing that too. and same as you i would have to go and into the bios and change my boot config and hope that it would even boot to my hdd.

all of this started happening the day after i updated to 9.04

---

### Post by bladeswords on 2009-04-26
The live CD should still work even if you don't have a hard drive.  Also if you are getting grub boot menu, it means that you hard drive is atleast somewhat working.  A guy at work had a similar issue when he installed 9.04 and it ended up been RAM.  Try run a memcheck, a disk check.

---

### Post by coffee yogurt on 2009-04-26
> **bladeswords said:**
> The live CD should still work even if you don't have a hard drive.  Also if you are getting grub boot menu, it means that you hard drive is atleast somewhat working.  A guy at work had a similar issue when he installed 9.04 and it ended up been RAM.  Try run a memcheck, a disk check.

well first of all the live CD doesnt work, the first two options, try ubuntu and install ubuntu, just show a loading screen and then spit out some crazy code. secondlyl i could never even get to the grub boot menu, it error 17'd before it even showed up.

now, however, id love to even get to an error 17 message, i cant even get an attempted boot from the HDD, it simply does not register anywhere but the BIOS itself, elsewhere it simply claims that "no disk is attached to the fasttrack controller" and then tells me to reboot and fix my boot priorities or insert media into boot device.

according to most of my computer my HDD does not exist and no matter how many times I try to change my IDE cable or anything else in there it wont change its opinion.

---

### Post by ripken204 on 2009-04-26
what is the crazy code that you get from the live cd?

my "live cd" i am using is actually from me usb key and that at least works for me.

---

### Post by bladeswords on 2009-04-26
It sounds very much hardware based if this is your problems...

Have you done the memory check?  Many modern bios has this as an option in them.  Also there are other great small linux distros that are aimed at fixing these kind of problems.  Try download RIP linux ([http://www.tux.org/pub/people/kent-robotti/looplinux/rip/]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/")) Do some hardware checks in that, then you should be more on the track.  If that even fails to boot, try removing one stick of RAM, if it still fails, replace that one you just took out and put in the other one.  Hopefully you have two sticks of RAM.  This should atleast narrow down the problem.

---

