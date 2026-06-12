---
title: "Paragon Disk Partitioner problem ate Ubuntu partition"
date: 2009-02-23
forum: General Help
---

### Post by hacksaw1340 on 2009-02-23
just bought this to shrink my C partition. I also had, "key word, had" two linux partitions.

Booted Grub for OS choice.
C: 80 gig - Vista 32 bit Sp1
Linux Ext:16 gig
Ext:384 swap

I wanted to shrink my C windows drive down from 80g to 50g so I would have more room on the Linux (unbuntu 8.04 LTS). 

I found this product and purchased it. I ran the product against the C drive which was 80 gig and it stated a reboot was needed to do the work. I rebooted and the conversion failed. The error was Cross linked files. no problem I can fix this. Rebooted and Grub reported error 17. 

I reboot the system to find this product hammered my boot manager from ubuntu, Then after getting grub super disk I found my lunix ext: partition corrupted and missing data. wont boot from Super grub disk (cd). This linux install and configs took months. cant do a restore at this point. Yea, know I am rather ticked off. can you blame me? I do have a backup, but what a pain huh? 

After reading all I can find,  paragon disk manager reads and uses the last partition, or file space ( in my case the linux partition) and uses it for space. ??  

This product does not state (that I can find) anything about a previous install of Windows and linux using grub as a bootloader.. Please use with caution is all I can say at this point.

**if you are a user of both OS's with Grub bootloader, please post it here and let me know if you had the same issue. **(before I try this again on another dual boot system).


I am discouraged to read in the paragon user agreement, this statement:

Although the administrators and moderators of Paragon Community Discussion Forums will attempt to keep all objectionable messages off this forum, it is impossible for us to review all messages."

Seem they don't want us to discuss problems with the product as well on their support site.

Any thoughts?

---

### Post by rasmus91 on 2009-02-23
> Any thoughts? i Have never heard of the partitioner you used. Did you use it from linux? 

I would have used Gparted, either by installing or doing a ubuntu live cd boot.

(But maybe it couldn't do the trick for you?)

---

### Post by hacksaw1340 on 2009-02-23
> **rasmus91 said:**
> i Have never heard of the partitioner you used. Did you use it from linux? 

I would have used Gparted, either by installing or doing a ubuntu live cd boot.

(But maybe it couldn't do the trick for you?)

I never thought about using gparted, Would have handled the NTFS parttions..  bet it would have worked just fine..  ;)  

Where is the "slap myself on the forehead" smilie!  LOL

---

### Post by rasmus91 on 2009-02-23
> Where is the "slap myself on the forehead" smilie! LOL

I don't know, but i can check it for you... to sek

---

### Post by rasmus91 on 2009-02-23
It won't format to Nfts by deault, but it can resize NTFS partitions... (then you can make vista format partitions, but still if you resize a partition with vista on it, it won't delete Vista... Or it shouldn't, there, i didn't promise anything :P )

---

### Post by hacksaw1340 on 2009-02-23
> **rasmus91 said:**
> It won't format to Nfts by deault, but it can resize NTFS partitions... (then you can make vista format partitions, but still if you resize a partition with vista on it, it won't delete Vista... Or it shouldn't, there, i didn't promise anything :P )

A resize of NTFS would of been all that I needed, and retained the linux partions would of been great! LOL  I understand the  no promises! :D    have you used Gpart before?  (i am downloading ubuntu 8.10 and will do gpart and see how I do.  i will in no way hold you responsible :D   

Thanks!!

#-o   < found it!

---

### Post by caljohnsmith on 2009-02-23
Actually, gparted can create NTFS partitions just fine, and it can resize them too. You can access gparted from the Live CD by going to System > Admin > Partition Editor. Sorry to hear of your problems with the Paragon partitioner though.

---

### Post by hacksaw1340 on 2009-02-23
Thanks for the message, caljohnsmith.

I was experimenting with gparted and found this.  very cool. I should have stopped in to this forum before I got carried away!

Now I have a new question but I will search for it first.  I expanded a ext3 partition / mount with Gparted but the system still reports the original size. I am having fun now that I reinstalled ubuntu.  

:lolflag:

---

### Post by caljohnsmith on 2009-02-24
Where are you seeing the size of your root Ubuntu partition being reported incorrectly? From your Ubuntu install, how about posting:
```
sudo fdisk -lu
df -h
```

---

