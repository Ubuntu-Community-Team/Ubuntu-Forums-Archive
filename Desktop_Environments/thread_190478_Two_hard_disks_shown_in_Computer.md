---
title: "Two hard disks shown in Computer?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by kel on 2006-06-06
Hi all, just a quick question, I've recently installed ubuntu 6.06 and I'm curious to know why it shows two HDD/filesystem icons if I click on the Computer icon from the Places menu? 

I only have one Hard disk installed, but when I click on Places/Computer its shows one icon for the floppy, one for the DVD and two for the hard drive, one of the hard drive icons is labelled "35GB Volueme: Root Drive" and the other is labelled "Filesystem". I've noticed they both have different permissions set but i'm puzzled to why its like this as they both hold the same data, I think. 

I'ts been a while since I've used ubuntu but I can't remember earlier versions doing this, I'm sure there was just one icon for the filesystem in the last version I tried (although chances are i'm wrong :D )

thanks.

---

### Post by kb3hkg on 2006-06-06
it sounds like you somehow made 2 partitions on your drive, and installed to both of them, or you have the same drive mounted twice.

---

### Post by engla on 2006-06-06
No, I have the same, two icons for the same thing. One is called "7,7 GB-volym: Rotvolym", the other "Filsystem" and it should be pretty easy for you to see what that would be in english: Root volume and File system.

In addition to this I have one entry each for my other partitions etc.

---

### Post by Denis on 2006-06-06
Ik looks like in Dapper all your mounted partitions are shown in this "computer" directory. In breezy I only had CD, floppy and filesystem. 

The reason that two items refer to the same directory is that "filesystem" is shown and your "root volume" is shown. These two are just the same, resulting in two links to "/". 

I try not to use this "computer" directory, since it is too confusing. I rather just use the directory tree.

---

### Post by bluenova on 2006-06-06
[QUOTE=Denis]Ik looks like in Dapper all your mounted partitions are shown in this "computer" directory. In breezy I only had CD, floppy and filesystem. 
[/QUOTE]

Ditto.
I have hda1, hda2 and filesystem since installing dapper.

I'll be monitoring this thread for a howto to get rid of them.

---

### Post by kel on 2006-06-06
yep, its very confusing, I'll just pretend its not there and never click the Computer icon again :D

I'm sure there is a very good reason behind there being two identifiers, but it is a bit perplexing, epecially to a noob like me. 

I'm just glad its normal though as I originally thought I may have messed up the idiot proof installation.

thanks all

---

### Post by lofty00 on 2006-06-06
I think it's gnome trying to be user-friendly. People converting from windows are used to thinking in terms of drives rather than the filesystem, so they give icons for all the mounted drives. But then they don't want to get rid of the linux way of doing it either, so there is an icon for 'filesystem', which takes you to the root of the filesystem. On my system, I have four drive icons plus one for the filesystem. In the case where you just have one drive, you end up with two icons for the same thing, which is confusing I guess.

It would be better if they had a different icon for the filesystem - maybe a mini tree diagram.

---

### Post by bluenova on 2006-06-06
Yea, I like the idea, but in practice (for me) it doesn't work.

I like having the icons for cd, floppy and my flash drives, but my partitions are my main partition and my home partition, which I don't need to see in 'computer'.

I havn't managed to find a way to get rid of them. Having them is a good idea, there just needs to be a menu option to tick off things you don't want in 'computer' and maybe to add things too.

---

### Post by avantgardaclue on 2006-06-06
yeah... i have got a desktop icon for the cd currently loaded and the flash drive attached, but NO 'Computer' icon... like wot i had on breezy. Irritating!!

---

### Post by yopnono on 2006-06-06
[QUOTE=avantgardaclue]yeah... i have got a desktop icon for the cd currently loaded and the flash drive attached, but NO 'Computer' icon... like wot i had on breezy. Irritating!![/QUOTE]

Well, if you like to have a "computer" icon on the "desktop", just drag it from the "places menu" to the desktop.

---

### Post by ozgur on 2006-06-15
Check this thread:

[http://ubuntuforums.org/showthread.php?t=197468](http://ubuntuforums.org/showthread.php?t=197468)

---

