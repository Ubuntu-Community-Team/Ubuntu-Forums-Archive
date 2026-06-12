---
title: "I am a idiot and need some help"
date: 2009-06-17
forum: General Help
---

### Post by ben wilson on 2009-06-17
I am a newbee and tried to load Ubuntu on my computer.  I partioned the hard drive and proceded to install Ubuntu everything went fine on the install then went to shut down and get back into windows and no go tried to recover windows with the cd and no go.  So now I have the issue of trying to recover my info from windows through Ubuntu I just got a new Maxtor 750gig external hard drive.  The bad part is that I think I installed the live demo so from what I have been reading I cant recover my info from that.  So just need a little help so I can get my stuff back so I can load windows and then load Ubuntu the correct way so I can learn more about Linux.

---

### Post by lykwydchykyn on 2009-06-17
Open a terminal window, enter the following diagnostic commands, and post back with the output.  This will help us find out what's going on:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

---

### Post by snakeman21 on 2009-06-17
Hmmm... Well, I can tell you that Linux can serve as an excellent data recovery program.  My suggestion for now:  Use the ubuntu live cd to boot your computer.  Using the file browser, you should be able to mount your Windows partition.  From there, you can copy all of your files to some sort of external media (I.E., external HD).  Then, used Gparted (System > Administration > Partition Editor) to format your HD to NTFS.  Then, shut down, remove the Ubuntu CD, insert your Windows CD, and start the computer.  Install Windows, then try partitioning your drive from the Ubuntu live CD for a dual boot again. 

Hope this helps!

---

### Post by ben wilson on 2009-06-17
I am a newbee and tried to load Ubuntu on my computer. I partioned the hard drive and proceded to install Ubuntu everything went fine on the install then went to shut down and get back into windows and no go tried to recover windows with the cd and no go. So now I have the issue of trying to recover my info from windows through Ubuntu I just got a new Maxtor 750gig external hard drive. The bad part is that I think I installed the live demo so from what I have been reading I cant recover my info from that. So just need a little help so I can get my stuff back so I can load windows and then load Ubuntu the correct way so I can learn more about Linux.

---

### Post by ben wilson on 2009-06-17
Thanks as soon as I get home I will try that thanks

---

### Post by lindsay7 on 2009-06-17
You should not post twice on the same basic subject.

[http://ubuntuforums.org/showthread.php?t=1190291](http://ubuntuforums.org/showthread.php?t=1190291)

---

### Post by ben wilson on 2009-06-17
sorry didn't know that it went the first time couldn't find it

---

### Post by raymondh on 2009-06-17
What are you using now to post?  Are you in livesession now? 

You can try using supergrub for boot isues.  YOU can use it to fix your boot set-up issues or even fix the windows loader so you can access those files.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

The 2nd link is a page from Herman (a UF member) that has detailed explanation and instructions with  regard to supergrubdisk.

This link is for trying to rescue stuff (data, etc) as well as tools of value

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Good luck.

EDIT : I see you have great options on your other thread.  Disregard this post.

---

### Post by Hobgoblin on 2009-06-17
> **ben wilson said:**
>  then went to shut down and get back into windows and no go 

A bit more of a description of what happens would help.

Do you have the option to boot into Windows on the Grub menu?

Does it start to boot into Windows?

Do you get any error messages?

---

### Post by ben wilson on 2009-06-17
I do have the option to boot into windows but get an error message I dont get off work till 7:00 eastern time but I will check the error message when I get home I think it said "error boot file" 
Did not defrag before install and took 10gigs when I did the partition

---

### Post by ben wilson on 2009-06-17
How do I delete one of these did not mean to post to of the same message

---

### Post by ben wilson on 2009-06-17
ok I am at home and need some help got the external hard drive hooked up need to know what to do

---

### Post by lindsay7 on 2009-06-17
> **lykwydchykyn said:**
> Open a terminal window, enter the following diagnostic commands, and post back with the output.  This will help us find out what's going on:

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

Do this from the live Ubuntu cd.

By the way, your other post is gone, I think so just stay with this one.

---

### Post by ben wilson on 2009-06-18
Thanks for everyones help I got the external hard hooked up and it was copying files all night long I didn't want to disturb it I am still working on a big project so wont be wiping the hard drive till monday But as soon as I go to wipe everything I will need some help.  Going to go buy and 80gig hard drive and load it on that and reload windows on my 500gig not very good at partitioning or setting up for duel hard drives Thanks again for everyones help I am sure I will need some more help really enjoying Linux and would like to learn a lot more.

---

### Post by ben wilson on 2009-06-18
Lindsay 7  I will get back to you tonight and see what it say so we might be able to determin weather or night I will actualy have to format the hard drive

---

