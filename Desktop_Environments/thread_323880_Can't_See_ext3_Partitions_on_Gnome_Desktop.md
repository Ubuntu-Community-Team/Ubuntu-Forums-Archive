---
title: "Can't See ext3 Partitions on Gnome Desktop"
date: 2006-12-22
forum: Desktop Environments
---

### Post by ReapeX on 2006-12-22
Hello,

I'm completely new to Ubuntu 6.10 well new to Linux in general.  
I bought a new hard drive and was successfully with dual booting windows and Ubuntu 6.10.
I was able to get my video card operating and wireless (this is my 3rd Day of using Ubuntu).

But now I am stump, why is it that I can not see my other ext3 partitions on Ubuntu? 
I am able to see the Fat32 partitions just fine but not any of the ext3 partitions.

My \user directory is on one of the ext3 partitions and I will like to view the files associated with it.   

I want the ext3 partition (80GB) to be the shared partition for both Operating Systems.

Am I totally out of luck and have to reinstall for the 9th time or is there way for me to see ext3 partitions on Ubuntu's desktop?

Thanks for your time,

ReapeX

---

### Post by kidders on 2006-12-22
Hi there,

If the filesystems you're looking for are mounted somplace, just navigate to that location. If they're not, mount them first. In order to access a filesystem, you need to mount it.

By the way, you should only ever need to install Ubuntu once! :-? What went wrong?!

---

### Post by ReapeX on 2006-12-23
Was working with 6 partitions, I had to learn a lot about extend partitions and logical partitions.

My goal was to have Windows and Ubuntu use the same partition for virtual memory.

Right now they each have their separate partition (I decided to just leave it like that) for virtual ram.

I also had another goal, install all programs through Ubuntu so I wouldn't have to deal with Window's Registry.  Never got to that because Ubuntu doesn't install exe programs right out the box, I had to learn about "packages" (which I'm still learning about).  The test exe program I was trying to install was Ad-Adware 6.0.  I wouldn't mind leaving windows behind and moving on to LInux but if I can't find an easy way to install exe programs...Windows is going to stay on my hard drive.  I'm still learning how to use Wine, I tried installing Ad-Adware using that program but it kept saying it couldn't find the installation exe file  (even though it is on my Ubuntu desktop).

Another time I formated, my wireless just wouldn't work when I place the home directory on a separate partition.  I read an article saying it was a good idea to put it on a separate partition >>.   Right now, my user directory is on a separate partition and Ubuntu seems to be working fine.

I'm an expert Windows Operating System Analysts but a newbie Linux user, I think I was just trying to jump the gun on my non-existant linux skills.

So now, I need to officially learn how to mount drives which I know is simple just have to read about doing it.   Man, sorry I didn't proofread this message...getting use to Ubuntu is more time consuming than I originally thought but I am also learning a lot.  Troubleshooting Ubuntu...is somewhat "fun" to me...don't know why hehe.

---

### Post by kidders on 2006-12-23
> **ReapeX said:**
> My goal was to have Windows and Ubuntu use the same partition for virtual memory.Oh hell... don't even try it! :-? You *could* do that with OSX and Windows perhaps, but Linux is ... well ... different, hehe.

> **ReapeX said:**
> I also had another goal, install all programs through Ubuntu so I wouldn't have to deal with Window's Registry.You mean you were hoping to use the same installation of the same application in both environments? That's something else not to try, I'm afraid ... it's not even recommended when dual booting two versions of the same OS family!

> **ReapeX said:**
> ...I place the home directory on a separate partition. I read an article saying it was a good idea to put it on a separate partitionYep :-) That's true of any operating system.

> **ReapeX said:**
> So now, I need to officially learn how to mount drives which I know is simple just have to read about doing it.I don't suppose there's much difference between the way Windows and Linux do that, except that you're more exposed to the technical whatnot in Linux, giving you more control over what happens. The one big change is that Linux dispenses with that odd "drive" abstraction that Microsoft seems to cling to. In virtually all non-Microsoft environments in the world, filesystems are attached at points within a single directory tree, so you can wander seamlessly from local hard drives to shared volumes or CDs/etc.

Once you've figured out Linux's device naming conventions, you can mount anything you want to with something like **sudo mount /dev/sdd5 /mnt/someplace**. The trick then is to use /etc/fstab to record information about common mount points, like network filesystems, etc., or maybe perform some of them automatically.

**Edit:** I suppose the key is to forget about the concept of a "drive" altogether, although having said that, some of the more modern additions to Linux make some attempts to emulate the idea.

---

### Post by ReapeX on 2006-12-23
Thanks, I just ran into another problem and this time I will have to reformat Ubuntu.

What happen is I need to resize a logical partition but there doesn't seem to be any sure fire way of doing that.  First I'm going to back up my user directory which is on the logical partition and then install Ubuntu one final time.

*Sigh*

---

### Post by ReapeX on 2006-12-23
I found an awesome guide to help me with Ubuntu, everything is going great now thanks Kidder!

---

### Post by kidders on 2006-12-23
> **ReapeX said:**
> I need to resize a logical partition but there doesn't seem to be any sure fire way of doing that.  First I'm going to back up my user directory which is on the logical partition and then install Ubuntu one final time.

There's no problem with moving your user directory around ... you don't need to reinstall anything. Reinstalling Linux is something you should almost never have to do!

Feel free to move it temporarily to a DVD, a USB flash drive, etc., and fiddle around with your partitioning scheme.

---

### Post by ReapeX on 2006-12-24
So formatting LInux is a last resort like Windows, I understand.
But I haven't learned how to change to tell Ubuntu that I changed the location of a specific directory.  I know it will be easy, after the break I'll be back at work and I can ask my "Ubuntu Guru" friends all the newbie questions that I have hehe.

I'm done with formatting now.

Right now I'm reading this article,
[http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition)

About how to run Windows through Ubuntu on a physical partition.

However, I 'm stuck at the post by exitdoor:

"In the ‘Create the virtual machine’ section there is no 6th step, but it is not a serious problem. But after choosing the individual partitions I got the error message: Failed to load partitions for device /dev/hda: Insufficient permission to access file. I gave myself to the disk group (Ubuntu Dapper),as requested."

He found a solution to the problem:

"I played a little bit, and it came to light, that if I make the VM run with my primary group, it’s not working. First I have to change group using the newgrp command, and make the VM run this way."

So, I'm trying to figure out how he used the newgrp command.
Really I'm trying to prove a friend and a professor wrong because they both stated it was impossible for two Operating Systems (on physical partitions) to co-exist at the same time.

---

### Post by kidders on 2006-12-24
> **ReapeX said:**
> Really I'm trying to prove a friend and a professor wrong because they both stated it was impossible for two Operating Systems (on physical partitions) to co-exist at the same time.Strictly speaking, that _is_ impossible, as at some level, one of them will always wind up being emulated by the other.

If you were to take a more pedantic interpretation of what you described, you could say that two OSs can *coexist* on the same partition, but you won't be able to *run* them both natively.

---

### Post by ReapeX on 2006-12-27
I'll see if I can find the link but according to the site you can run both natively on separate partitions.

Using VMServer you can run Windows XP (which is on a physical partition) natively inside of Ubuntu  Dapper or Edgy Eft.

---

### Post by 3rdalbum on 2006-12-27
> **kidders said:**
> Strictly speaking, that _is_ impossible, as at some level, one of them will always wind up being emulated by the other.

If you were to take a more pedantic interpretation of what you described, you could say that two OSs can *coexist* on the same partition, but you won't be able to *run* them both natively.

I'm not entirely sure what's being argued. All I know is, you can install two versions of the classic Mac OS onto the same partition, and boot natively into them both (one at a time, of course). I've done that before - many Mac users have. I hope that settles the bet.

---

### Post by ReapeX on 2006-12-27
> **ReapeX said:**
> Was working with 6 partitions, I had to learn a lot about extend partitions and logical partitions.
So now, I need to officially learn how to mount drives which I know is simple just have to read about doing it.   Man, sorry I didn't proofread this message...getting use to Ubuntu is more time consuming than I originally thought but I am also learning a lot.  Troubleshooting Ubuntu...is somewhat "fun" to me...don't know why hehe.

I didn't know you replied to my entire section, I thought it was just a quote of what I previously said...sorry about that.

"You mean you were hoping to use the same installation of the same application in both environments? That's something else not to try, I'm afraid ... it's not even recommended when dual booting two versions of the same OS family!"

Yes I was, I thought it was stupid to have applications such as Visual Studio 2005 to run on Windows and then install a completely different complier on Ubuntu.   But I should be able to get that particular application to work with Wine, plus I know there are tutorial sites stating how to get Visual Studio 2005 to work with Wine.

---

### Post by ReapeX on 2006-12-27
> **3rdalbum said:**
> I'm not entirely sure what's being argued. All I know is, you can install two versions of the classic Mac OS onto the same partition, and boot natively into them both (one at a time, of course). I've done that before - many Mac users have. I hope that settles the bet.

It was really a bet stating that this,

[http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition](http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition)

Could not be done.

I almost accomplished it but ran into a problem with group permissions that I could not correct.
It's fine though, I'm just glad that this experience has allowed me to become a Ubuntu user.
I'm going to do my best never to boot Windows XP again hehe.

---

### Post by ReapeX on 2006-12-27
But I suppose, even in that link, Windows XP is still being somewhat emulated as stated by Kidders

---

### Post by ReapeX on 2006-12-29
If you guys want to stop me from doing another reload, check out:

[http://www.ubuntuforums.org/showthread.php?p=1945311](http://www.ubuntuforums.org/showthread.php?p=1945311)

o_o, [I do understand mounting and editing the fstab file now, thank you!]

---

