---
title: "Changing from Ubuntu to dual booting"
date: 2009-03-16
forum: General Help
---

### Post by lewis595959 on 2009-03-16
Ok, currently I have Intrepid installed on my computer, taking up the full HDD.

I've experimented with Wine and VirtualBox for running games, but neither of these quite cut it. I've decided to switch from running just Intrepid to dual booting Vista and Intrepid. I've gathered that It's a LOT easier to install Windows first, but as you can see, this isn't an option.

I don't mind backing stuff up and wiping the system clean, but I have a few questions first.



It seems I have two options:
A) Completely formatting the HDD and  installing Vista, followed by Ubuntu.
B) Finding a way to create a new partition through Ubuntu and Installing Windows on that.


First, A is a problem because I have Ubuntu set up the exact way I like it with apps, updates and interface tweaks. (The same is true for Windows on my virtual box, but this is a secondary concern)

Second, B would be ideal, but after reading articles concerning this online, I'm not sure if it's possible. I haven't found any articles on exactly how to do this, and every article tells me that Installing Windows first is far superior to installing Ubuntu first.

What should I do? Is there a way to format the HDD, but back up my entire user interface and such in Ubuntu?



Many thanks,
Lew.

---

### Post by Zimmer on 2009-03-16
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

I used this site and EasyBCD to dual boot Vista, although I used the instructions for Vista loaded first....

I recommend EasyBCD though...

There are links at the bottom of that page tp APC magazine's step by step instructions for installing Vista after Linux, too.

---

### Post by namegame on 2009-03-16
An Ubuntu liveCD contains a program called Gparted, which is a partition manager. You should be able to use it shrink your Ubuntu partition, then install Windows in the newly created space.

As a warning, I don't know how Vista reacts to being installed in a separate partition. I also don't know if it will recognize your Ubuntu partition in the boot manager. As Zimmer said, EasyBCD is great for managing the Vista boot loader.

---

### Post by greywolf238 on 2009-03-16
As NameGame said, Use GParted to partition the hd and then install Vista, which will probably mess up Grub but grub is easy to reinstall.

---

### Post by lewis595959 on 2009-03-17
Thanks very much for the fast responses.

I've successfully switched from Ubuntu to Ubuntu + Windows, but I have one more question.

Is there any software that lets me view my windows environment from within Ubuntu? (I'm thinking something akin to a Remote Desktop Connection; so I can stay logged in to Ubuntu and access my windows files / download stuff, etc)

I know I'm pushing my luck here, but it sucks having to stay in Windows while my machine updates and downloads stuff.

Thanks again,
Lew.

---

### Post by blazemore on 2009-03-17
You CAN set up a virtual machine to boot from a "real" partition, but I wouldn't recommend it. The best thing would be to mount your windows drive as /windows or something.

---

### Post by lewis595959 on 2009-03-17
Two things:

Why isn't it advisable to set up a VM to boot from a real partition?

Also, Is it somehow possible to download system updates and such just by mounting the windows drive? I understand that I can download files in Ubuntu and copy them over, but that doesn't mean I can run updating programs and the like.

---

### Post by philinux on 2009-03-17
> **lewis595959 said:**
> Two things:

Why isn't it advisable to set up a VM to boot from a real partition?

Also, Is it somehow possible to download system updates and such just by mounting the windows drive? I understand that I can download files in Ubuntu and copy them over, but that doesn't mean I can run updating programs and the like.

I laughed reading the first post of this thread.
[http://ubuntuforums.org/showthread.php?t=664692](http://ubuntuforums.org/showthread.php?t=664692)

---

### Post by lewis595959 on 2009-03-17
Ok, new problem.

I hadn't tried booting into Ubuntu yet, but I assumed it worked (Reason being that I had to do windows updates and such.. bleh)

Turns out that I can't boot into Ubuntu. (Something about hd(0,0))

I'm assuming this is because I forgot to install GRUB in /dev/sda1 instead of hd(0,0)

I tried to remedy this by booting the LiveCD and opening up a terminal.. here's what I did:

sudo grub
grub> setup (/dev/sda1)
(also tried install (/dev/sda1)

This gives me an error: "Error 23: Error while parsing number"

How can I correct my mistakes?

---

### Post by blazemore on 2009-03-18
Grub doesn't use actual /dev thingies.
I think instead of /dev/sda1, you want (hd0,0)
Grub starts numbering from 0

---

### Post by lewis595959 on 2009-03-18
Ok. I read somewhere that I need to install GRUB in my Ubuntu partition so EasyBCD can find it (since Vista gets rid of it)

---

### Post by philinux on 2009-03-18
Ok just to find out exactly whats going on do this.

Boot the live cd.

Download this boot info script to the live cd Desktop.
[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Open a terminal and use this command.
sudo bash ~/Desktop/boot_info_script*.sh

This creates a results.txt file.

Attach it to a post.

---

### Post by lewis595959 on 2009-03-19
Ok, I'm attaching my results.txt to this post.

---

### Post by Zimmer on 2009-03-19
> **lewis595959 said:**
> Ok. I read somewhere that I need to install GRUB in my Ubuntu partition so EasyBCD can find it (since Vista gets rid of it)

Yes, do not install GRUB to the MBR..

---

### Post by lewis595959 on 2009-03-19
Okay, GRUB was in the MBR when I installed Vista, meaning it was over-written by Vista's booter, right? How can I go about installing GRUB so I can boot Ubuntu again?

---

### Post by Zimmer on 2009-03-19
> **lewis595959 said:**
> Okay, GRUB was in the MBR when I installed Vista, meaning it was over-written by Vista's booter, right? How can I go about installing GRUB so I can boot Ubuntu again?

[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

I recommend you then install EasyBCD to your Vista partition and add an entry for Ubuntu....

---

### Post by lewis595959 on 2009-03-19
> **Zimmer said:**
> 
I recommend you then install EasyBCD to your Vista partition and add an entry for Ubuntu....

I have EasyBCD installed under Vista, but I can't get it to work. If I add a Linux entry and then restart and choose it, I get a message saying "Try hd(0,0)" and nothing loads.


When I do this EasyBCD tells me the following details about the linux partition (obviously something is wrong):

Name:  Ubuntu 8.10 Intrepid (note: I set this name myself)
BCD ID:  {7f50ce7b-1288-11de-83ac-00219b074ae6}
Drive:  C:\
Bootloader Path:  \NST\NeoGrub.mbr

---

### Post by Zimmer on 2009-03-21
So, if I understand correctly, you can boot Vista?
You have Ubuntu installed on the first partition? You have re installed GRUB to that first partition? 

IF the above are all TRUE, then judging by the file results.txt you posted earlier it appears to me that the main problem is that partition sda1 (with Ubuntu on it) does not have the bootflag set.  you should be able to do that with gparted from the live cd.

If you have not installed GRUB to sda1 (GRUB recognises this as hd(0,0)  -- sda3 would be hd(0,2)  ) then EasyBCD will have a problem finding GRUB.

If you have not pointed EasyBCD to the correct location for GRUB then it will have a problem.(the error message try hd(0,0) could be an indicator that this is a problem).


Regards
Zimmer

ps. life was so much easier for me when I installed Ubuntu and it asked me where I wanted GRUB and I replied 'NOT ON THE MBR' and put it on the same partition as the Ubuntu root.... :)

---

### Post by lewis595959 on 2009-03-22
Ok, I'm fairly new to this. Please bear with me.

I'm not sure where GRUB is installed at the moment. I installed it to the MBR, but Vista has overwritten that.

I've tried a few separate options in EasyBCD so far:

First, Linux > Type: Grub > Drive: Partition 0(Linux Native) 
Second, Linux > Type: Grub > Drive: Drive 0
Third, Linux > Type: Grub > 'GRUB isn't installed to the bootsector'


When I restart and try to boot into the Ubuntu partition, It gives me the 'Error: Try hd(0,0)' message... I still don't understand what's going on >.<

---

### Post by Zimmer on 2009-03-22
So, it appears you need to reinstall GRUb.

[http://users.bigpond.net.au/hermanzo...#reinstallgrub](http://users.bigpond.net.au/hermanzo...#reinstallgrub)

OK, Herman is still notating drives in Ubuntu as hda1 etc.. , whereas nowadays they are named sda1 etc. but  the GRUB instructions are still ok.



Do you have an alternate install CD ?

---

### Post by lewis595959 on 2009-03-22
Zimmer, that link is giving me a 404 error.. Would you mind relinking it?

I don't have an alternate install CD, either.. just the LiveCD that I used to install Ubuntu.

---

### Post by Ms_Angel_D on 2009-03-22
[How to dual-boot Vista with Linux (with Linux installed first) -- the step-by-step guide with screenshots]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")

---

### Post by lewis595959 on 2009-03-22
Ok, thanks guys.. I just managed to find the article that Zimmer linked with some experimentation.. and I managed to get Ubuntu working.. Thanks for bearing with me, everyone :)

---

### Post by Zimmer on 2009-03-22
Sorry, I was away from the computer just now. Glad you have things up and running... and Vista (just in case) too..

:)

---

### Post by lewis595959 on 2009-03-22
Haha, no worries. Everything is working great. Thanks again guys :)

---

