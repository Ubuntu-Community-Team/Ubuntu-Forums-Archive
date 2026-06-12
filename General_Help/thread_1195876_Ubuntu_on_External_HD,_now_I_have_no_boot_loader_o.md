---
title: "Ubuntu on External HD, now I have no boot loader on my internal"
date: 2009-06-24
forum: General Help
---

### Post by Magres on 2009-06-24
So last night I decided to add a bootup of Kubuntu to my laptop, but my internal HD is only 80gb and I don't have it partitioned(in retrospect I should have partitioned it, I've only used like 20gb of it because I have most everything on my external, with the vital stuff copied to both)

Anyways, installation was fine and dandy (yay for Ubuntu not being aggravating as hell like Fedora, which I tried first because its what's on the machines at work), until I restarted.  After some finagling and a lot of swearing (for a bit I thought Linux had just eaten my machine), I finally realized that in installing Ubuntu to my external harddrive, I had also installed GRUB and over-written my internal boot loader (which, from what I've read, is a POS boot loader anyways.  Personally I know nothing of boot loaders, lol).  The good side is that I have GRUB.  The downside is that it's on my external harddrive, meaning that I can't boot up my laptop without my external, which requires a wall plug.  Even WITH the external, I have to go through bizarre voodoo rituals to get it to boot up.


The tl;dr version is that I would like to find out how to manually load GRUB onto the internal workings of my computer, so I can actually boot the damn thing without having to screw around with my external harddrive.  Preferably with step by step instructions, because I'm definitely not that knowledgeable.  Google has thusfar produced no results, and the search function around here didn't seem to have the answers.

If comp specs are needed, I'll provide them shortly, but it appears to just be an issue of GRUB wanting my external HD around, and me not wanting it around all the time.  When I boot up without my external plugged in, I generally get Error 21, but have gotten Error 5 before, and I've got no idea what either of those are, and I'm having a brief moment of laziness and cant be assed with finding out what they are.

Thanks folks!

---

### Post by james.brantley on 2009-06-24
> So last night I decided to add a bootup of Kubuntu to my laptop, but my internal HD is only 80gb and I don't have it partitioned(in retrospect I should have partitioned it, I've only used like 20gb of it because I have most everything on my external, with the vital stuff copied to both)

[SIZE=2]Hello there, I am by no means an expert on Unbuntu/Kubuntu/Linux but I would suggest shrinking the Windows partitions, on your internal and installing Ubuntu there.[/SIZE]

---

### Post by james.brantley on 2009-06-24
[SIZE=2]You could use disk manager in Windows.[/SIZE]

---

### Post by Magres on 2009-06-24
afaik Windows XP has no way of shrinking a partition without entirely obliterating it (actually this is about the only function of Vista I've heard about that I'm even mildly interested in), and I really don't feel like re-installing windows.  (having to re-enter all of the pertinent registry keys for programs I have on my external is a massive pain, and I finally got around to doing all of it like two weeks ago)

Also, I like the fact that I can plug my external into most any computer I want and boot Linux up, I just want to be able to boot my computer up without having to sit there and restart my computer over and over and flip my HD on and off until I get the timing right such that my harddrive is in its "HEY LOOK OVER HERE GUYS IM A HARDDRIVE" stage of booting up when my BIOS is in its "HEY ANY HARDDRIVES OUT THERE?" stage of booting up.  Usually takes me like 8 tries, and it's really annoying.


Right now the biggest problem I'm trying to solve is figuring out how to unmount the external HD that my Ubuntu is on from within Ubuntu.  Simply shutting down Ubuntu w/o dismounting it seems to lock it to my computer, and I need to be able to write to it from another computer so I can snag like 10 gb of code that I need from someone.  I'm on my windows partition atm burning a fresh LiveCD of Kubuntu in the hopes that I can boot from the disc and then dismount the drive.  Like being able to boot my computer easily is important, but I need to get this damn code running >_<

---

