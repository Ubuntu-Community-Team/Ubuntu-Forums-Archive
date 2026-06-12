---
title: "Dell 1420 - Resoring on a Dual-Boot setup, please help?"
date: 2008-03-29
forum: Dell  Ubuntu Support
---

### Post by Dodger USMC on 2008-03-29
Basic Question: 
How can I use the Dell reinstall image to restore the system to default if I have changed the partition table and installed XP Pro *WITHOUT* it affecting the XP Pro install?

Detailed Quesiton:
I have a Dell 1420 purchased in March of 2008, and it is currently dual-booting Ubuntu 7.10 and XP Pro. My odyssey of how I got the system to dual boot with Linux installed first can be found here: [http://ubuntuforums.org/showthread.php?t=732492]("http://ubuntuforums.org/showthread.php?t=732492")

Well, Now I am having problems with the Ubuntu system causing DNS problems on every computer in my house whenever it connects to my home network. When the Ubuntu system connects, every URL I type in goes to google. period. My hosts file is fine, lmhosts is fine... I've looked all over and cannot find anyone that shares this problem, or a fix, so I want to restore to factory settings and try again. I haven't been using Linux very long so I'm fairly sure its something I did. 

So, I want to restore to factory settings, and I have a DVD burned with the Dell re-installation image, BUT I do NOT want to mess up my XP Pro partition. Why you ask? Bascially because of the heartache I went through just to get it installed and working with Linux installed first. 

Is this possible?

Any help is GREATLY appreciated! :)

---

### Post by ElTimo on 2008-03-29
I'm confused: do you want to keep Ubuntu? or are you trying to get rid of everything? or what?

I have a Latitude and I have used the Dell image several times to reinstall. Just make sure you make a separate partition for the new install. The best way to do this is to use the Ubuntu Live CD and go to System->Administration->Partition Editor. If you end up having to do that, let me know and I'll help you from there.

---

### Post by Dodger USMC on 2008-03-29
Ok, I have three partitions on my hard drive. The first is the Ubuntu partition, the second is the XP Pro partition, and the third is the Linux Swap partition. 

I and having a lot of trouble with the Ubuntu partition, and I want to reinstall. Problem is I do NOT want to have to deal with the hassle of finding and installing all of my system drivers, especially when Dell already has them together in a neat little package. 

I want to use the restore image to restore ONLY the active Ubuntu partition and/or the Swap, WITHOUT affecting or touching the XP partition. I want my XP install to still work.

Is this possible?

---

### Post by ElTimo on 2008-03-30
yes it's very possible

in fact, I just did it the other day :P

All you have to do when reinstalling Ubuntu is select the old ubuntu partition as the one to install to.

Now, if what you mean is that you want to get rid of Ubuntu, I'm afraid I'm not at liberty to disclose that information ;-)

Just be careful, don't do anything (too) stupid, and for the love of Christ MAKE A BACKUP!!!

---

### Post by Dodger USMC on 2008-03-31
Thanks ElTimo, I appreciate the help on this one!

---

### Post by ElTimo on 2008-03-31
No problem! That's what these forums are for, aren't they? ;)

---

