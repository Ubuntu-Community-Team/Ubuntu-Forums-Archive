---
title: "Inspiron CP turns Feisty Fawn into Roadkill"
date: 2007-07-08
forum: Dell  Ubuntu Support
---

### Post by Michael Barna on 2007-07-08
1)  Burned ISO disc of 7.04 following MD5 Sumcheck, all went well
2)  Updated BIOS to A16 (post 2000 cutoff BIOS) on Inspiron machine
3)  Boot Inspiron from CD, when loading Ubuntu the Linux kernel loads then I get a black screen with a flashing underscore.  No keys or key combinations work.
4)  Remove CD, restart Inspiron with Win 95 and all is well.

Man...I am stumped...HELP!!!!!!!!!!!!!!!!

Kind regards,

Mike

---

### Post by vwbeamer on 2007-07-08
Hmmm, are you sure your computer meets min requirements?

You need at least 256 ram.

You may want to try a lighter version of Linux

---

### Post by Arrdee on 2007-07-08
Yeah. Xubuntu?

Post specs for your computer.

---

### Post by Michael Barna on 2007-07-08
32 MB RAM

Pentium - 166

256 KB L2

Neo Magic 2160 Video controller, 2 MB video memory

3 GB HD

It is an elderly laptop that runs Win 95 just fine.

Thank you,

MIke

---

### Post by Arrdee on 2007-07-08
Oy. That's a very, very old laptop. The Live CD install requires at *least* 128MB of RAM, if I recall, and even in alternate installs 32MB isn't going to hold up well. Definitely go with Xubuntu, if that would even work.

Might want to wait around for someone else's advice, but I'd say the best you're going to get on that is Damn Small Linux: [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Michael Barna on 2007-07-08
Dells database states that 128 MB is maximum for my old machine. 

[http://support.dell.com/support/edocs/systems/pmojav/specs.htm](http://support.dell.com/support/edocs/systems/pmojav/specs.htm)

Does anyone know if 128 MB will work for my installation?

Is there a "system requirements" document for Ubuntu 7.04?

Kind regards,

Mike

---

### Post by kadath on 2007-07-08
> **Michael Barna said:**
> Dells database states that 128 MB is maximum for my old machine. 

[http://support.dell.com/support/edocs/systems/pmojav/specs.htm](http://support.dell.com/support/edocs/systems/pmojav/specs.htm)

Does anyone know if 128 MB will work for my installation?

Is there a "system requirements" document for Ubuntu 7.04?

Kind regards,

Mike

Ubuntu really needs 256 MB absolute minimum, in my experience. It's much better to have 512 MB+.

Even Xubuntu would be a little slow on 128 MB, never mind 32 MB! For 32 MB, I'd recommend something extremely light, like Damn Small Linux, Puppy Linux, or Feather Linux. They're made for very old computers.

---

### Post by neptho on 2007-07-08
> **Michael Barna said:**
> Dells database states that 128 MB is maximum for my old machine. 

[http://support.dell.com/support/edocs/systems/pmojav/specs.htm](http://support.dell.com/support/edocs/systems/pmojav/specs.htm)

Does anyone know if 128 MB will work for my installation?

Is there a "system requirements" document for Ubuntu 7.04?

Kind regards,

Mike

Basic system requirements are [here](https://help.ubuntu.com/community/Installation/SystemRequirements).

To be brutally honest, it'd be worth more of your effort saving a few more dollars and getting a new machine; You can buy a new Dell Inspiron 1501 for $450 right now, which is not only 10 years newer, but light speeds faster.  Your machine is at the same specifications I was running in 1998, and while a Linux distribution from 1998 *could* run on that, or you *could* run a severely stripped down system, you don't really want to do that.

---

### Post by Michael Barna on 2007-07-08
Sighhh..

Well OK then.  Ill purchase an updated machine.  My only problem is that I am a cheapskate with a taste for the exotic and best who dosn't know what he is doing:lolflag:

I'm gonna put one of those micro Linuxs on my elderly laptop though.  Thanks for listing their names so I can get to the downloads!

Kindest regards,

Mike

---

### Post by Dragonbite on 2007-10-29
> **Michael Barna said:**
> Sighhh..

Well OK then.  Ill purchase an updated machine.  My only problem is that I am a cheapskate with a taste for the exotic and best who dosn't know what he is doing:lolflag:

I'm gonna put one of those micro Linuxs on my elderly laptop though.  Thanks for listing their names so I can get to the downloads!

Kindest regards,

Mike
I'm cheap too.

I've got an Inspiron CP (233MHz, 64MB Ram) and Damn Small Linux (DSL) runs very well.  If you can max it out to 128MB ram you will find more options, but still slim pickings.

DSL and Puppy are the most common/popular of the lite Linux distros. You can try installing Ubuntu Alternate and go with Fluxbox or Openbox and bare minimum apps but I'm not sure how well that will work anyway.

Currently I'm looking at Fluxbuntu I've heard 300MHz being recommended for it so I don't know how it will work.

I'm also looking at TinyMe, a mini-version of PCLinuxOS.  Don't know what the specs are, but they use (I believe) the Enlightnement Windows manager which is supposed to be pretty good on resources.

If you have a reasonable desktop computer, you can also look at using the laptop as a thin client. Then all of the processing occurs on the more powerful server and the laptop just provides the "interface".  I don't think it'll work wirelessly but with a long chord you can still sit in the lazy-boy and have it on your lap ;)

---

