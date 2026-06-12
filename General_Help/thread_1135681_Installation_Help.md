---
title: "Installation Help"
date: 2009-04-24
forum: General Help
---

### Post by CoffeyLover on 2009-04-24
Ok guys, help me out on this one. I am going to partition my hard drive (Currently running XP) and install ubuntu. I've done it before, and it is fairly easy. However, I have a problem. Other people occasionally use my computer. But when they turn it on, and it comes up with the boot loader, they flip out. Is there any way to make it so XP boots automatically except when a key on the keyboard is held down or something? (I know this is the way mac does it) Basically I want it to seem like ubuntu is not there (So others will not be confused). Thanks!

---

### Post by maheshasolkar on 2009-04-24
In /boot/grub/menu.lst, there should be a line like 'default=<number>'. The <number> indicates the item number that will boot by default. Use the entry number that corresponds to windows in that line. The numbering starts at 0. So the first entry is 0, second is 1 and so on. An entry typically starts with 'title ....'

---

### Post by maheshasolkar on 2009-04-24
You can also reduce the timeout in 'timeout=10' line. That is the number of seconds Grub waits before it boots the default entry.

But if the timeout is too short, you will have to be quick on the keyboard when the Grub menu shows up.

I am not aware of a way to completely hide the Grub menu.

---

### Post by jamessnell on 2009-04-24
Well, one option is to beat the stupid ignorance-fear driven people in to silent cowardice.

But failing that "highly reasonable" approach, Here's a few ideas:

1. Perhaps you could set the default target in grub to being Windows and have a very short timeout? If the grub menu is only up for a second, then they'd have to have an IQ > 65 to notice. Here's a link to [free online IQ testing]("http://www.free-iqtest.net/"). ;)

2. Some BIOSes let you specify what hard drive to consider as the primary one (the one it'll boot from first). So, if you have a spare hard drive, you could add it, then make it the primary boot device, install Ubuntu, reset the primary device to the original drive and then when you're using the machine, you can just manually set it to boot from that..

3. Another option is to put an instance of grub on a flash drive and when the flash drive is in the system, it could provide you with the boot options to get Ubuntu going, else the Windows bootloader will kick in. 
I think the Ubuntu installer provides a means of not installing a bootloader, though I've never goofed with it.

3b. Maybe you could just put [SGD]("http://http://www.supergrubdisk.org/") on a flash drive or CD and then use that, like with suggestion #3, but less custom.

4. What about Wubi? Maybe you can use that gracefully for this purpose, I'm not totally sure there though.

5. (a joke) Perhaps if you change the boot splash to being the windows logo and then pick a windows-like window manager theme, they'd never notice? You may also need an Internet Explorer icon to use for Firefox and be sure to setup their key tools of moronity through wine, mainly being paint, solitare & minesweaper. Also, I'd suggest you burn copies of OpenSolaris and tell them they're lucky as they get to try the latest version of Windows - then maybe they'll hate change so much more that they'll just cower in the corner and leave doing actual work to someone like yourself.

(*dusts off hands*) Well, I think we got that one covered now ;)

Cheers!

---

### Post by _Purple_ on 2009-04-24
> **CoffeyLover said:**
> Ok guys, help me out on this one. I am going to partition my hard drive (Currently running XP) and install ubuntu. I've done it before, and it is fairly easy. However, I have a problem. Other people occasionally use my computer. But when they turn it on, and it comes up with the boot loader, they flip out. Is there any way to make it so XP boots automatically except when a key on the keyboard is held down or something? (I know this is the way mac does it) Basically I want it to seem like ubuntu is not there (So others will not be confused). Thanks!

Please backup your /boot/grub/menu.lst before you edit it.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

---

