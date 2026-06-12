---
title: "Converting an old DOS computer to Ubuntu"
date: 2011-08-20
forum: Education &amp; Science
---

### Post by Ferralll on 2011-08-20
So I am trying to figure out if this is even going to be possible, or if it is worth my time and effort to try:

At work, we have an old scientific instrument that was controlled by an old DOS computer and Windows 3.1.  When we went to turn it on, the system's hard-drive crashed (broken, will not work).  We grabbed the hard drive from another old computer, but we need to put a new opperating system on it.  (It had WIN NT, and that will not support the original software)

I am currently in charge of re-installing DOS and WIN 3.1.  But I was wondering if I would be better off just installing a version of linux (Hopefully Ubuntu, but really any version will do) 

The problems: 
* The program that runs the equipment is for WIN 3.1.  I have heard that Wine was developed as a way to run these sorts of programs, so I thought that this might be a good alternative.  (Would this be an easy thing? Or will it be more trouble than it is worth?)

* The hard ware connects to the computer through several cards.  I have no idea what they are, or what they really do.  (One has a 64 wire ribbon cable that plugs in to it. not sure if it actually 64 wire, but it is about 3-4 inches wide) 
--- Will these cards plug and play under any version of linux?  There is little to no chance that I will find the proper drivers for them, so is there any hope for hardware compatibility? 


I would love to hear any suggestions that the community has.  (Even if it is that there is no hope) I just feel dirty trying to install DOS and WIN 3.1.  And I feel like there has got to be a better way. 

I am not that computer savvy, so anything that will require more than the most basic trouble shooting will be out of my league, but I do like new and interesting learning experiences.

---

### Post by pqwoerituytrueiwoq on 2011-08-20
how much ram does it have (64 mb will not cut it by a long shot)
may want to try DSL or puppy

---

### Post by whatthefunk on 2011-08-20
Im thinking that theres no way Ubuntu will run on this.  How much RAM does it have?  You may want to look into a CLI distro...

---

### Post by haqking on 2011-08-20
If you are not computer savvy then stick with Dos and Win3.1 as a re-install.

Your only real option is likely to be an CLI based *nix and so a steep learning curve for you.

It will be quicker and easier and less painful to do a reinstall of Windows.

The hardware is likely to be ancient

---

### Post by ugm6hr on 2011-08-20
> **Ferralll said:**
> The problems: 
* The program that runs the equipment is for WIN 3.1.  I have heard that Wine was developed as a way to run these sorts of programs, so I thought that this might be a good alternative.  (Would this be an easy thing? Or will it be more trouble than it is worth?)

* The hard ware connects to the computer through several cards.  I have no idea what they are, or what they really do.  (One has a 64 wire ribbon cable that plugs in to it. not sure if it actually 64 wire, but it is about 3-4 inches wide) 
--- Will these cards plug and play under any version of linux?  There is little to no chance that I will find the proper drivers for them, so is there any hope for hardware compatibility
These will be insurmountable, even if any alternative OS will install. Particularly if even Win NT won't run the software.

---

### Post by Sef on 2011-08-20
I agree with what has been said. Stick with DOS 3.1 on this computer. GUI is out of the question for your unknown specs (due to the age of your computer), so only a command line would be possible. If you feel like trying a very lightweight CLI Linux, I or someone else here could give you some pointers on what to use.

---

### Post by tommpogg on 2011-08-22
> **Ferralll said:**
> 
--- Will these cards plug and play under any version of linux?  There is little to no chance that I will find the proper drivers for them, so is there any hope for hardware compatibility? 


Maybe it is a silly question: do you have the drivers for DOS/Windows? If not, how are you planning to restore your instruments functionalities?

---

### Post by timlev on 2011-08-29
You could try the [Dosbox emulator]("//www.dosbox.com/information.php?page=0") on newer hardware. Or you could try [FreeDos]("//www.freedos.org") if you can't find a way to install DOS.

Good luck!

---

### Post by VanillaMozilla on 2011-08-30
Forget Linux for that computer.  You may find that a later Windows will work fine.  Windows 95, 98, or 2000 would all be much nicer than 3.1, and are likely to run your programs just fine, especially if you run them in compatibility mode.  But if you don't have immediate success, there's really no substitute for Windows 3.1.  But don't get carried away trying to update it.

---

### Post by Helen McCall on 2012-03-19
This sounds a bit like the computers I used to build out of scrap parts in the mid nineties!

I would need a lot more information onthe old computer before making any recommendations. Do you know what the processor is? If it is a 286 then Linux is not practical. If it is a 386 + 387n coprocessor or else a 486, then things might be possible.

Do you know how much ram is in the machine? If you have less than 128MB then you might have difficulty getting a graphical gui running on any linux distro.

Are the cards old style AT expansion cards or are they the older XT expansion cards. If running Windows 3.1 I doubt if they are PCI because it wasn't around then.

If this is a 486 AT computer with at least 128MB of RAM then you have a fighting chance of doing it. There is a Debian project for a cutdown Debian distro (can't remember links but search on Google or Debian forums) which would be able to run a simple gui along with wine to run your proprietory software to operate the hardware.

My first Debian box I built in 1996 used parts from various types of computers including a Kontron image analyser, and had a 386 processor with 387 maths co-processor and 64MB of RAM. I can't remember the name of the windowing gui I used - but it was a very simple one. With 64MB it had enough RAM to be able to work as a workstation, but could only handle very simple html web pages with no javascipt etc. There was not enough memory to handle wine on top of everything else. But the next machine I built had 128MB and that gave enough resources to run wine on a basic Debian system.

The advantages to you in putting a simple cutdown Debian system with wine on your machine would be that you wuld then have access to modern printing drivers. A search on ebay should allow you to find an old 10base network card such as from 3com which still have drivers available, and would allow you to then network the computer and give access to modern printers and sending the data to your workstations.

I hope this helps.

---

