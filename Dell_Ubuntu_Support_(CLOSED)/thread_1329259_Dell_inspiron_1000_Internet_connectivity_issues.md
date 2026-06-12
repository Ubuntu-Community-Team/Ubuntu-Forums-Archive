---
title: "Dell inspiron 1000 Internet connectivity issues"
date: 2009-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mrfarmer2u on 2009-11-17
I have a Dell inspiron 1000 that I'm trying to rebuild for my family.  The install went fine but now the laptop will not connect to the Internet.  I don't think the os is recognizing the nic card nor the wireless card (1350).  The wireless card shows deem light but doesn't light fully.  How do I get the os to read the nic cards contents?

Thanks!

---

### Post by teward on 2009-11-17
it won't recognize it unless you install the drivers for it.  What specific cards are you using?

Or, you didn't connect the cards correctly when you were rebuilding it.

Or you didn't use compatible hardware.

Or other problems.

---

### Post by Mrfarmer2u on 2009-11-18
It uses a pci 1350 external card for wireless.  I want to at least get it working with the internal nic card.  I was thinking that ubuntu 9.10 requires some type of activation of a windows captiable driver.  I can't find the Linux version of my Dell network driver.  Do you think that might be the problem?

---

### Post by teward on 2009-11-18
did you install an internal wireless NIC card?  If you did, can you tell me the name of the device (company that made it and what model)?


***SUPER EDIT:

Okay, first, let me say that I don't use 9.10 much, it sits on my desktop box doing nothing because GRUB doesn't work right.  

Second, this works for me in in Jaunty (9.04), but I don't know if these options exist in 9.10.  You should be able to go to System -> Administration -> Hardware Drivers and if the drivers are proprietary (as in non-Ubuntu made), it will show up.

***END SUPER EDIT

***SUPER EDIT 2:

Please tell me the exact cards you installed, that is the company that made it, its model number, etc.

[off-topic] wow, I fail at remembering to type things into my posts.[/off-topic]

Anyways, Dell doesn't necessarily create Linux versions of their drivers.  I have a Dell Latitude E6500 laptop with an Intel wifi card, and it doesn't have problems, never had to install drivers for it, it just worked.

**END SUPER EDIT 2

---

### Post by Mrfarmer2u on 2009-11-19
That's where I think my problem lies.  I need to get my hands on a Dell Linux compatible driver.  After installing 9.10, I never figured out how to install te LAN driver nor the wireless card (pci 1350) driver.  Also, when I go to the installed drivers nothing shows up.  So I guess I'm SOL then huh?

Thanks,

So do you think it's a matter of making ubuntu notice the drivers already preinstalled or do they need to be installed manuallly?

---

### Post by teward on 2009-11-19
It all depends on your system.  If the generic drivers weren't installed, then that's a problem.  If the drivers are there, but not working, then I don't know how to fix it, however someone else might.  Did you try reinstalling Ubuntu onto it?

Final thought:  If you're using Dell's Ubuntu, don't.  Use the full, normal, regular Ubuntu.  That's what I use, and it works **perfectly**.

---

### Post by Mrfarmer2u on 2009-11-19
I've tried installling the os twice but there is no difference.  It's like everything on the os works fine but the internet.  I guess its b/c of the old machine I have.  There has to be some type of way to get ubuntu to accept those drivers.  When I initially installed it I partitioned the entire hdd and loaded 9.10 on it.  From there I didn't do anything extra except let the install run and configure the time, date, etc...

---

### Post by teward on 2009-11-19
It should just work automatically if any of it's internal.  But if it's external, perhaps the devices you're using are not compatible with Linux.  I found this to be the case with numerous pieces of hardware I use, including microphones, lol.

---

