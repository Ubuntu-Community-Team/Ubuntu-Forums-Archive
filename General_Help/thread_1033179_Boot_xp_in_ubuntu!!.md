---
title: "Boot xp in ubuntu!?!"
date: 2009-01-07
forum: General Help
---

### Post by metz80 on 2009-01-07
Hi..

First off, I have Ubuntu, and XP installed on my hdd, Grub at boot.

I am using XP for misc software that do not run i Ubuntu/linux, and some work related.

So.. you see, I boot win xp when I need to do some work related stuff, and use ubuntu for everything else.

My question!

Is it possible to boot the windows xp partition in a virtual environment ? 

I would like to have access to my work email, and minor things from the XP partition without having to reboot the computer to windows xp all the time.

I know I could install a seperate xp virtual in Linux, but I can not do this, because I am using misc software sometimes that require alot of power.

so simply have the xp running paralell with ubuntu for the minor things, and reboot whole thing for bigger operations.

Is this possible ?

Regards!
-Tom-

---

### Post by mikewhatever on 2009-01-07
Yes it's possible and just a google search away. Done that for you.
[http://www.google.co.il/search?q=vmware+existing+windows&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.il/search?q=vmware+existing+windows&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by hyper_ch on 2009-01-07
I'd rather advise to make a virtual partition for an xp that you run in vbox or vmware and not using a real partition.

---

### Post by metz80 on 2009-01-07
> **hyper_ch said:**
> I'd rather advise to make a virtual partition for an xp that you run in vbox or vmware and not using a real partition.

Why ? 

I need to have power available when I am running some misc programs, and I doubt I will be able to do this if using a virtual environment!?!

Thanks for the google search btw ;p

---

### Post by HunterK on 2009-01-07
I have to assume there is risk involved in possibly damaging/corrupting the data on the "real" partition if you do it that way?

---

### Post by hyper_ch on 2009-01-07
there are a few issues with running it from a real installed windows... as said, it's my advise :)

---

### Post by linux_paul on 2009-01-07
> **metz80 said:**
> Why ? 

I need to have power available when I am running some misc programs, and I doubt I will be able to do this if using a virtual environment!?!

Thanks for the google search btw ;p

What are your system specs? I use VirtualBox to cross-compile windows apps and it runs just fine on 1Gig of ram.

---

### Post by metz80 on 2009-01-07
Specs are no trouble, dual core cpu, 64bit system, 4GB Ram ++... Was running virtualbox before, with windows virtual image file thingy.. But.. I did not like the lack of performance when using some of the software I need to use.. Tried to tweek the performance, providing more RAM and such, but.. Not the same as running on a separate install.

Thing is,, I really wanted all work related stuff (emails, docs and such) on the windows part, and private on linux, however,, It would be nice to not have to reboot the comp each time to check work rel emails ++.

And I do not want to break the windows install... 

Anyone tried to run this using virtualbox? or VMware? or perhaps anything else?

Regards!
-Tom-

---

### Post by weblordpepe on 2009-01-07
I have successfully used QEMU to run Windows 95 in a virtual machine, but directly off a hard drive.
It was as simple as specifying /dev/sdb1 or whatever it was as the virtual disk. Qemu may not be the fastest ot there but that simple feature provided an amazing flexibility.

---

### Post by jocko on 2009-01-07
It is possible with the instructions [on this page]("http://ubuntuforums.org/showthread.php?t=769883").
But: Realize that you may have to reactivate your copy of XP. The windows license does not permit running the same install on a new machine (even if it's a virtual machine in the same physical hardware), and microsoft have put some safeguards to prevent this. So it's up to you if you want to risk it...

---

### Post by blazemore on 2009-01-07
DON'T DO IT
It buggered up activation, the performance was dire, and it made my XP unbootable on bare metal.

---

### Post by metz80 on 2009-01-07
LoL... Sounds like it will crash my xp partition ;)
Perhaps I shall setup a dual boot ubuntu and xp system (with no stuff that could be lost), and give it a go... 

What do you recommend to use? Virtualbox (possible to do this?), some other app?

-Tom-

---

### Post by blazemore on 2009-01-08
Just use a virtual hard disk. The performance won't be much different. In fact, the performance may even be better!
There are three ways to make your virtual hard disk faster:

1. Make it Fixed Size, not Dynamic
2. Save it on its own dedicated hard-drive (different partition wont make a difference)
3. FORMAT WITH NTFS, NOT NTFS (QUICK) in XP setup <--- Really helps

---

### Post by blazemore on 2009-01-09
> **metz80 said:**
> Why ? 

I need to have power available when I am running some misc programs, and I doubt I will be able to do this if using a virtual environment!?!

Thanks for the google search btw ;p

You're misunderstanding.
It will still be a virtual environment!
CPU: Virtual
GPU: Virtual
RAM: Virtual
Audio: Virtual
Hard disk: Virtual (It doesn't matter where the files are stored, its still virtual)

---

### Post by sendblink23 on 2009-01-09
All that "blazemore" is saying..

Is Exactly TRUE, Virtual Enviroment is much better.. and Please follow his Suggestion of both of his Last Posts

---

### Post by blazemore on 2009-01-09
Thanks Sendblink. :-)

Have you tried "Windows XP Performance Edition September 2008"?
I use it for virtual machines, it doesn't come with all crap like games and the like. The iso is only about 300mb!
I'm afraid I can't tell you where to get it.

---

### Post by weblordpepe on 2009-01-26
> **blazemore said:**
> it made my XP unbootable on **bare metal**.Thats an awesome term. We should all use that to describe a real system :P:)

---

