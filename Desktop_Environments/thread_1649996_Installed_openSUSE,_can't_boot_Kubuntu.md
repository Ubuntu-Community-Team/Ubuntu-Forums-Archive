---
title: "Installed openSUSE, can't boot Kubuntu"
date: 2010-12-20
forum: Desktop Environments
---

### Post by armware on 2010-12-20
I have Win7, Kubuntu and a third OS (and home) partition for trying out others. I did Arch, Debian and Chakra without problems with triple booting. I skipped the bootloader installation/configuration step when installing those, booted into Kubuntu and ran update-grub to get the new one added to the boot list.

I used a separate partition for /boot (sda6), and have only one hard drive in this machine.

Following the same procedure (skip bootloader install) with openSUSE 10.3, I managed to loose the ability to boot Kubuntu.

I know the Kubuntu partition is fine (or at least still intact) and have since been able to get Windows added to the grub menu after a few attempts with grub-install and update-grub, which boots.

So I guess my question is 'now what'?

---

### Post by armware on 2010-12-21
I guess I'll do a reinstall if no one has any suggestions. Does anyone have anything at all for this?

---

### Post by inobe on 2010-12-21
i haven't dual booted in years but i will try.

the home partition sharing could go wrong, i know that from experience, that's besides the point.

during the suse install it's grub loader should have been directed at installing itself into suse root partition and not the mbr, then you just edit kubuntu's menu.lst to chainload to your suse installation.

this will give you an idea for similar to various scenarios

[http://ubuntu.swerdna.org/ububootsuse.html](http://ubuntu.swerdna.org/ububootsuse.html) 

like i stated, i stopped the dual/triple boot stuff since suse 9.3, i hope i offered a little here :lol:

---

### Post by inobe on 2010-12-21
> **armware said:**
> 

Following the same procedure (skip bootloader install) with openSUSE 10.3, I managed to loose the ability to boot Kubuntu.



whoa 10.3 ?

didn't notice till now, a 11.3 fully supported version is out !

---

### Post by armware on 2010-12-21
thank you, inobe, for your time.

i realize now my typo - i did install opensuse 11.3, not 10.3. originally i tried 11.4 (in the spirit of experimental os's and all), and i could not find some of the more basic documentation (like installing mp3 support) so i reverted to 11.3.

after some time poking around (opensuse is actually doing well for me overall) i think my question is, what would be installed in the boot partition and can i reinstall it without reinstalling the os?

---

### Post by adam22 on 2010-12-22
Just to clarify a few things, you are using two linux operating systems, and 1 Windows, correct? Do you have two boot partitions? I do not believe this is necessary, but if it is, it's still irrelevant, I don't think this has anything to do with the problem.

From what I'm understanding, you don't see Kubuntu listed under Grub2 when you turn the machine on? Or do you see it and nothing happens?

Since I'm a tad confused, I'll direct you towards this link which should provide an answer for you: [http://www.dedoimedo.com/computers/grub-2.html#mozTocId514088](http://www.dedoimedo.com/computers/grub-2.html#mozTocId514088)

Updating grub through the terminal isn't going to work, so don't waste your time trying.

---

### Post by armware on 2010-12-22
I have two linux os's as well as a windows install. using a single boot partition managed in kubuntu.

it seems all the files are missing from the boot partition except a 'grub' folder.

---

### Post by Chame_Wizard on 2010-12-23
You have to fix it in grub.cfg

---

### Post by armware on 2011-05-11
not to revive an old thread, but to complete it with the solution and mark it as solved.

ultimately i just reinstalled kubuntu. a fresh install is nice from time to time anyways, right?

---

