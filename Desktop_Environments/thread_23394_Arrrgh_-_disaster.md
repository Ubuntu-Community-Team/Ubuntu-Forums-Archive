---
title: "Arrrgh - disaster"
date: 2005-04-01
forum: Desktop Environments
---

### Post by bailout on 2005-04-01
I had ubuntu and kubuntu installed on seperate partitions. Ubuntu was installed first and then kubuntu with grub on the mbr. I was mainly using kubuntu and just using ubuntu to test things on and seeing which DE I preferred. Ubuntu had developed some major problems with gdm and rather than try and fix them I decided to reinstall ubuntu in the same partition. As I didn't want to risk my kubuntu install in any way I thought I would try installing grub to a floppy. The ubuntu install went fine, then I tried booting into kubuntu. Lots of fatal error messages and it completely failed to load x leaving me in a garbled screen with hardware reset as my only option. 

Why has reinstalling ubuntu onto to one partition and grub onto a floppy wrecked another partition with kubuntu on it????????????

Thankfully and predictably, windows still works - thank god for Bill Gates. But all the tweaking and info I had on my kubuntu partition now seems to have been lost.

---

### Post by alastair on 2005-04-01
[QUOTE=bailout]Why has reinstalling ubuntu onto to one partition and grub onto a floppy wrecked another partition with kubuntu on it????????????[/QUOTE]

It should not have. It is possible that some bug somewhere screwed you up (who knows), but it is perhaps more likely that you screwed something up yourself. Hard to say though. Perhaps you could have another go and take notes? Only kidding ...

It's a learning experience, as they say!

---

### Post by fdoving on 2005-04-01
You really don't need to install both kubuntu and ubuntu.. you can easily install kubuntu in ubuntu and ubuntu in kubuntu directly from the internet.. (k)ubuntu have apt-get, synaptic and kynaptic. great tools.

It's hard to tell why your setup got _ up.. but i guess it's got something to do with partition numbers and the fstab/grub setup.

Try to stick with just one installation of (k)ubuntu.. and install both desktop-systems on  it, you can choose which one to use at login time.

Good luck!

---

