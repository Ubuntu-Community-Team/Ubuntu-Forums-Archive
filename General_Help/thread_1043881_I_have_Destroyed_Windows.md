---
title: "I have Destroyed Windows"
date: 2009-01-18
forum: General Help
---

### Post by AJExtreme on 2009-01-18
A sad but very exciting time has happened for me.  I was in the process of attempting my first install of Ubuntu and in that process I destroyed my Windows Partition, while trying to partition Linux... But at this time it was very happily so... 

I finally realised I don't have the knowledge to understand the partitioning of Linux.  But don't want to go back to Windows, and would like to know so I can reinstall or repartition so that I can easily back up my data.

I have 1 HD (sda) (120Gig- sata) I want to have my OS on Ubuntu / Kubuntu 

I know that doing it in auto will work, but my problem is I don't understand how it is being partitioned.   I want to understand the partitioning of it... I enjoy understanding what it going on with my computer. But I have brain lock coming from Windows. 

Could someone please help me understand the partitioning of Linux (Ubuntu).  I have read about it, but it is like Chinese (jiberish) to me.

I have Ubuntu 8.10 currently installed and enjoy it so, I just don't understand how it is partitioned at this time.

Partitioning used to let me know what I needed to back-up (ie. data)

I am thinking of getting a second drive for a data drive...

Currently:

AMD 64 3200+
1 (120Gig sata)
1 (1 Gig Ram)

What is the best option(s) for what I have?
Does default partition setup a swap partition, and is it needed?

Thank You

AJ

---

### Post by theWrkncacnter on 2009-01-19
To take a look at your partitions, you can fire up gparted, a graphical partitioning editor, found under System>Admininstration>Partition Editor, or something like that. It's very powerful though, so be careful using it.

As you'll be able to see, the default partitioning scheme does set up the (needed) swap partition.

---

### Post by AJExtreme on 2009-01-19
So when I do a fresh install, what in your opinion or other opinions would be the best way to partition a 120 Gig hd.

My goal is to be able to have programs installed (ie. OS, Office Suite, Email, some Graghic editor, and KmyMoney) the rest is data, such as documents, pictures, music, etc.

Basically I am trying to understand what my partitions are cause I see in the books talking about creating partitions for /home, /root, /user etc. I dont understand all that.  All I know is that in Windows I Use c-drive as my primary for (os, programs, etc.) and d-drive (data, etc.)  and so on.

All I want to to is be able to do what I am doing on the computer but also have plenty of data storage seperated in case of a hardware cash especially being new and trying so many new things.  I don't want to loose my data should something happen.  And get this answered in plain english.

---

### Post by theWrkncacnter on 2009-01-19
It's a very good idea to have a separate /home partition for your userdata, in case anything happens to your root partition. Think of your root partition (mounted as /) as your c: drive, with programs, system settings, etc. Your userdata partition (which will be mounted as /home) would contain all your personal files, application preferences, the stuff on your desktop, etc.

If you just have one partition, your whole filesystem, including /home is on that partition. But if you have a separate partition for userdata, that partition will still show up in the filesystem as "/home," even though it is physically a separate partition.

I hope that explanation helps.

In my opinion the best way to partition a disk that size for Ubuntu would be to have a 10gb reiserfs root partition, 109gb ext3 /home partition, and 1gb swap partition.

---

### Post by zvacet on 2009-01-19
I will do it like this

1. 10GB root        mountpoint /
2.1-2GB swap
3.rest for home     mountpoint /home


On the root partition will be installed OS and all app you install later.On home partition will be your settings and files.And swap is virtual memory.

---

### Post by AJExtreme on 2009-01-19
Now were chit chatting... I really appriciate it that actually helps me a lot.  So what about this thing I've heard about a boot partition should I have one or not really a big deal.  My next big question on it is about the File format (i.e. NTFS, fat32, etc.)

What is the difference in the formats or more so what formats should I use for what partitions.

I am so used to Windows it gets confusing when a person has so many choises such as in Linux that it makes things probably more difficult than they really are.

Which is another reason why I want to get away from windows - where it seems to be like so many monopolies you have to conform to thier way...and learn that is the only way when that isn't true...

---

### Post by HermanAB on 2009-01-19
Hmm, same as in Windows, the minimum number of partitions required is one, for "/".  The system will then create a directory tree under that.  You can run Linux with a swap file and it is not slower than a swap partition either.  This type of setup is good enough for a first try.

However, once you get to know something about Linux, you'll realize that it may be nice to be able to re-install the system without losing all your data and you can accomplish that by having a separate /home partition, and while you are about it, you may want to try out a /swap partition, which gets you to the typical desktop setup:
/ (15GB)
/swap (4GB)
/home (rest)

If you run a server, then there are arguments to be made for more partitions for /var and /usr (and maybe /export).  The advantage is that when things go wrong, the damage can be contained.

Hope that helps!

Herman

---

### Post by theWrkncacnter on 2009-01-19
A boot partition can be really useful if you're ever planning to dual boot with other operating systems on the same computer. But if you don't want to do this, you don't really need one. You might as well make one anyway though if you're starting from scratch (make this one ext2)

reiserfs and ext3 are both pretty much the standard for linux right now. Reiserfs is somewhat higher performance, especially for small files, making it ideal for use by the system. Ext3 is a little slower, more compatible, and it is possible for Windows to read it, which makes it ideal for user files. ext2 is older and even more compatible, but lacks newer features.

---

### Post by AJExtreme on 2009-01-19
Thanks HermanAB,

That helps I understand Root is like the main (c-drive).
/home is like my data drive (d-drive)
/swap I don't really understand...

I get the general idea of it all.  I am not looking to set up a server so the /var, /usr, etc. is not really relevant to what I am tying to do.

Thanks Wrkncacnter

So how big should I make my /boot partition

Now I understand enough about the ext2 and ext3. Just curious why would you not make the boot ext3?

Thanks again for so much help thus far.

AJ

---

### Post by EvilRobotDrew on 2009-01-19
~So how big should I make my /boot partition

I have a /boot partition, and out of 500mb, i am using 150mb, a little bit of extra space here is a good thing.

~Now I understand enough about the ext2 and ext3. Just curious why would you not make the boot ext3?

the poster will probably have a reason, but i imagine it has to do with compatibility, you want /boot to be readable by any future OS, and while almost everything can read ext3, by making it ext2 you have a little bit of a safety net. it is like formatting a 256MB SDcard with FAT, you don't need the features in NTFS, and now you can be sure that everything will read it. my /boot partition is ext3 and i have had no problems. I don't recommend a separate /boot partition for most, but if you plan on trying out lots of new distros, or installing new distros regularly, and know how GRUB works, then it is nice.


the swap partition is where linux stores files when ram is full, and where your data goes if you hibernate the comp. if you have a laptop make sure it is at least a big as ram (i have an extra .5GB in swap to be safe). it is kinda like the pagefile in windows. (other posters can help you out more then i can with this)

it has already been said, but a separate /home partition is AWESOME! it allows you to upgrade or switch distros with no worries (as long as you keep the same username, and are careful about permissions). making /home a separate partition was the single smartest thing i ever did on my linux box.

---

### Post by adamlau on 2009-01-19
Here is how I would likely set up a 120 GB drive w/ 1GB RAM for general, all-around desktop use:

/ = 4 GB [PRIMARY #1]
/home = 10 GB [PRIMARY #2]
/files = 100 GB [PRIMARY #3]
/usr = 4 GB [EXTENDED #1]
swap = 2 GB [EXTENDED #2]

I prefer to mount 'tmpfs /tmp tmpfs defaults,noatime,nodev,nosuid,mode=1777 0 0' over a separate /tmp partition. I like a separate /usr to save time on having to recompile apps that were previously installed.

---

### Post by mixmaster on 2009-01-19
> **EvilRobotDrew said:**
> ~So how big should I make my /boot partition

I have a /boot partition, and out of 500mb, i am using 150mb, a little bit of extra space here is a good thing.

~Now I understand enough about the ext2 and ext3. Just curious why would you not make the boot ext3?
ext3 is, in simple terms, a journalled version of ext2.  This means that it can be recovered if something goes wrong (eg power outage) without corrupting the file system or losing a significant amount of data.  However, by its nature a journalled fs is fatter and slower than an unjournalled one.  
/boot is effectively read-only so it really doesn't need to be journalled.  It is also very small, containing kernel images and grub.  I would guess about 10Mb for each kernel image and its associated gorp, so your 500Mb partition looks to be more than adequate.

TBH, a separate /boot buys you very little in most circumstances.  A separate /home is very useful if you like to do a clean install instead of an upgrade and sometimes it pays to have /opt (or even /etc) on their own fs although you need to be careful with /etc.

---

### Post by adamlau on 2009-01-19
mixmaster is sport on in that having a separate /boot partition buys very little under most circumstances. Now that I think about it, I recommend that you keep /boot under / and choose to go with a separate /boot at  later time and only if you have a good reason to do so. After all, multiple reinstalls are how we all got good at it to begin with :) .

---

### Post by EvilRobotDrew on 2009-01-19
i forgot to mention that i have several GRUB backgrounds in /boot, and this is why i have 150mb used. 500 is definitely overkill, but with 80gb of HD space on my laptop, it doesn't hurt.

I don't recommend a seperate /boot partition either (technically a dedicated GRUB partition, but i digress), unless you are comfortable enough with GRUB and don't mind a little bit of extra work when new kernels some out. I never really intended to have /boot separate, originally i was dual booting Ubuntu and Fedora; when i decided to drop fedora GRUB was reading from the Ubuntu partition, [i deleted everything except /boot, shrank the partition, and here i am.]("http://ubuntuforums.org/showthread.php?t=1018816")

---

### Post by dragos240 on 2009-01-19
You destroyed windows? Good job! No just kidding, i needed to say that. I had to when i saw this title.

---

