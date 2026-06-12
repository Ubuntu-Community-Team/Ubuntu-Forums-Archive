---
title: "[SOLVED] GParted - Partition Table Question"
date: 2008-12-02
forum: General Help
---

### Post by Gujuunit on 2008-12-02
ok so I had a Sata WD 160GB hard drive.
I've thrown it in an enclosure and connected it to linux. It's NTFS. I tried to connect it to my desktop which is windows, but no luck. I try to throw it in a desktop and install windows, bios detects it, but windows installer says no hard drive detected.

My question is how do I format it properly and create a partition so that I can install windows on it. I know I know, but this isn't my hard drive it's my uncles, so I have to put windows on it.

*edit*

Sorry if it's in the wrong section.

---

### Post by SomeGayDude on 2008-12-02
What version of winders are you installing.

---

### Post by Gujuunit on 2008-12-02
Windows XP Pro, I believe Service Pack 2

---

### Post by SomeGayDude on 2008-12-02
OK.  The only one this that I can think of is that it may be hooked up wrong.  Is it the same computer that you originally took it out off?

---

### Post by Gujuunit on 2008-12-02
Yes it was originally hooked up to the desktop. I pulled it out put it in my external. Transfered the data to another computer(Windows Vista). Formated it. Put it back in the desktop, and tried to install windows XP. I kept getting the error. So I connected it to my linux laptop. It was able to detect it and it had a windows folder with like a few files. I reformated it, but it linux to NTFS.

Original Desktop (bios detects, windows installer undetectable)
My Desktop Windows XP Pro SP2 (undetectable in enclosure, I haven't tried hooking it up internally yet)
My laptop Ubuntu 8.10 (detectable, able to transfer and everything)
Uncles laptop Vista Home Premium (detectable, able to transfer and everything)

---

### Post by SomeGayDude on 2008-12-02
If I remember right, linux still has issues with ntfs.  But, this sounds like a partition error.  Hook it up to the vista machine and delete the ntfs partition.  Then create a new partition and format it in FAT32.  Hopefully this should allow the installation to recognize the HD.  During the installation you should have the option then to reformat it in ntfs.  Unfortunately, I have to clue when it comes to vista so I cant tell you how to do this.

---

### Post by Gujuunit on 2008-12-02
Thank You I'll give that a shot. Granted I don't really use Vista so I'll have to figure out a way, but I'm sure I'll find something that can help me do that.

---

### Post by SomeGayDude on 2008-12-02
I will be going to bed.  Let me know what happens and I will check up in the morning.  I wish you good luck.  I know this must be frustrating.

---

### Post by Gujuunit on 2008-12-02
kk, thank you for your time. I def will update this and hopefully this fixes the problem. Found out how to delete the partition and recreating it as we speak.

yeah it is a little frustrating, but nothing I can do about it.

sigh wish I could just convince my uncle to switch to Ubuntu.

---

### Post by SomeGayDude on 2008-12-03
Any updates???

---

### Post by Gujuunit on 2008-12-03
Was up till 8am honestly working on this a little bit, but still no luck.

I'm currently trying to install it in my desktop to see if I can recognize it that way. If so I'll try to format it with XP and see if anything good comes out of it.

Any other suggestions would still be appreciated.

---

### Post by SomeGayDude on 2008-12-03
Call me an idiot!! XP doesn't come with drivers to handle sata drives.  here is a site that has the instructions.

[http://xphelpandsupport.mvps.org/how_do_i_install_windows_xp_on_a.htm](http://xphelpandsupport.mvps.org/how_do_i_install_windows_xp_on_a.htm)

---

### Post by Gujuunit on 2008-12-03
ah, Thank You that is always good to know

The hard drive did have a bad partition. 
I guess it's good to know that Linux can't create a good NTFS partition that will work everywhere. Awkwardly enough Vista was still able to read it.

Well I now have to do what you said, but only problem is my uncles desktop doesn't have a floppy. :-( I'll have to find a copy of Windows with Sata drivers integrated. 

*edit* Found one, hopefully it works with my uncles Key

Again thank you for all your help **SomeGayDude**.

---

### Post by SomeGayDude on 2008-12-03
Thanks and best of luck.  Let us know what the outcome is.  Tell your Uncle see ubuntu is soo much cooler.
I think NTSF is still under development with Linux.  It can read it fine, just has issues writing.  Have fun...

---

### Post by Gujuunit on 2008-12-04
hmm weird the post if your link and my post afterwards seem to have been deleted.

but the gist of the message was.

The problem was with the partition Table.

I popped the drive in my desktop. found a program to wipe the table, then recreate it. popped it in my uncles computer, it found it.

so the partition problem is fixed, but since my uncles desktop doesn't have a floppy disk. I created a sata integrated windows xp disk, but after the initial setup from the disk it keeps BSODing on me.

---

### Post by Gujuunit on 2008-12-04
no clue why, but my replies keep getting deleted.

I'm having trouble making a sata integrated windows xp cd though since it's not an Ubuntu problem I'll try to find another forum to figure it out.

---

### Post by SomeGayDude on 2008-12-04
Its on two pages now.  Under the last message listed you will see:
Page 1 of 2   1 2 >

You can try this.  Put the drive in your XP desktop.  Use the drivers so you can access the drive.  Then format the drive with the system files and copy all the contents of the CD to the drive under an i386 directory.  You should get a DOS prompt on you uncles pc after you put the drive back.  From the prompt you should be able to install window.  This is a long shot.  I know this works for machines that cant boot from the CD drive.

---

