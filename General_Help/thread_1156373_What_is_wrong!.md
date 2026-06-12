---
title: "What is wrong?!"
date: 2009-05-11
forum: General Help
---

### Post by gmantt on 2009-05-11
I've encountered so many problems with ubuntu 9.04 desktop edition in just the passed 20 minutes. Everything was working fine up until I did a restart about 20 minutes ago. I tried going on myspace, just by googling it and it wouldn't accept me pressing enter so I had to type it in manually in the address bar. I got there and tried to log in, it didn't let me. I was pressing enter, clicking login like 20 times, nothing.

I go to login to pidgin and type my password in, it shuts off. I try to configure my evolution email it shuts off. 

I change my backround, theme, and appearence all is well until I reboot and it goes back to stock settings. 

I can't download any pictures from the web. This is probably due to the fact that I have 0 bytes of memory in all of my linux folder, I don't know how that happened. 

It won't remember my wifi WEP key. 


I'm just soo frustrated, I really wanted my first linux experience to be good, but I don't know what happened I don't know what I did wrong.

Please guys could you help a newbie out?

---

### Post by gmantt on 2009-05-11
sorry to bump but i really need to fix this

---

### Post by rifak on 2009-05-11
this might be a ridiculous question but have you actually installed it on your computer? or are you starting it with the disk every time? those problems about having 0 byte folders and not remembering your background and passwords sounds like you might be using the CD to run ubuntu...it was just the first thing that came to mind.

---

### Post by gmantt on 2009-05-11
No I can't be booting from the cd the cd is out of my drive. Though that did make me think. I thought I followed the directions correctly, I installed it side by side with my XP, now I have this nightmare to deal with.

---

### Post by gmantt on 2009-05-11
I honestly do not get this at all. I have another parition drive that has about 2 gigs, that's called filesystem in my ubuntu.

---

### Post by rifak on 2009-05-11
how many gigs is your computer as a whole?

---

### Post by gmantt on 2009-05-11
80 gigs. I'm on a laptop. Dell partitioned my HDD to be a recovery drive so that's basically 9.92 minus the 80.

---

### Post by rifak on 2009-05-11
if its possible, give ubuntu as much as possible, but definitely more than 5 gigs. heres an example:

you want to give ubuntu 50 gigs and you currently have 2 gigs of ram..you would want something like this:

a "/" partition of 50 gigs (that where ubuntu as a whole is installed)
also a 2 gig "linux swap" partition

when you are on the partition editor portion of installation, you will see a "manual partition" opten, click that and press next. in there you will see a bunch of space called free space. click on that and to "edit partition". there you have options to pick the "/" and "linux swap". go from there with what i said earlier. just be sure to read EVERYTHING and read it very carefully...think about what you are doing and just be careful haha ill help later tonight if you still need it. post back if there are problems. i gotta make dinner. hope this helped

---

### Post by gmantt on 2009-05-11
Alright now you've completely lost me. I thought that I had already gave the option of enough disk space. I don't even know what I formatted it at. =\ man this is horrible. And I'm reading that I'm gonna have even more of a trouble uninstalling this thing aren't I?

---

### Post by oldos2er on 2009-05-11
Can you please copy and paste this command into a terminal
```
sudo fdisk -l
```
and post the output here?

---

### Post by gmantt on 2009-05-11
alright i did that

i got 

Disk /dev/sda: 80.0 gb, 80026361856 bytes
255 heads, 63 sectors/ track, 9729 cylinders
Units = Cylinders of 16065 * 512 = 8225280
Disk Identifier: 0xe8000000

Device        boot                      Start                         End                   Blocks      Id     System
/dev/sda1                                     1                           10                  80293+     de     Dell Utility
/dev/sda2     *                             11                        1316            10485760       7       HPFS/NTFS
/dev/sda3                                1317                        9076           62332200         7      HPFS/NTFS
/dev/sda4                                9077                        9730            5246600          f   W95 Ext'd(LBA)
/dev/sda5                                9403                        9730             2620416       dd   Unknown
/dev/sda6                                9077                        9381            2449849        83    Linux
/dev/sda7                                9382                        9402             168651        82    linux
swap/solaris

---

### Post by Ericyzfr1 on 2009-05-11
> **gmantt said:**
> I honestly do not get this at all. I have another parition drive that has about 2 gigs, that's called filesystem in my ubuntu.

What you call file system is also the root partition, mine is 2.3Gb out of a fresh installation. Then I also have a separate 5gb /home partition for user settings.
I keep all my personal files on a separate partition.

---

### Post by gmantt on 2009-05-11
So whats causing my linux partition to say that I have 0 bytes in certain folders. I'm pretty sure this is causing my problem in which I cannot save my theme or save anything for that matter. 

Also it seems my internet drops but doesn't. I can't really explain it, but I couldn't even log onto this site. It seems if I go to a site that requires me to log in or perform some sort of search (besides google) I cannot log in. It just will NOT allow me.

---

### Post by gmantt on 2009-05-11
Oh I also found something else out, I went to my system monitor and it has only one device and 

/dev/sda6 ext3 2.3 GiB free 21.0 MiB available 0 bytes used 100%

---

### Post by gmantt on 2009-05-11
To add to that under system monitor> system is shows system status available disk space 0 bytes

---

### Post by gmantt on 2009-05-12
Bump

Sorry but this is really annoying I really want this to start working, I now have a useless operating system that is taking 2 gigs of my much needed space.

Thanks.

---

### Post by oldos2er on 2009-05-12
What you should do depends on whether or not you want to keep Ubuntu. If you want to keep it, you'll need to boot from the LiveCD and run gparted to enlarge Ubuntu's partition. If you do this, you should backup any files you don't want to lose first.

---

