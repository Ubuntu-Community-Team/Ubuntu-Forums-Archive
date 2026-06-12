---
title: "Ubuntu/Kubuntu 8.10 File Browser Freezes (goes grey) when reading Hard drive"
date: 2008-10-31
forum: Desktop Environments
---

### Post by Gilreygar on 2008-10-31
Hi i'm new with linux and i wanted to try ubuntu/kubuntu, all went smooth (besides wireless :P) but now i'm having a strange problem.

First, it's a Laptop (Toshiba Satellite Pro L300D-SP5802) AMD turion64 X2, ati x1200, 1 gb ram, 1 Sata 160 GB HDD.

So, since i had Winxp and it's my "production" laptop so i dual booted kubuntu 8.10 32 bits, since i tested with the live cd and i could use everything (except wifi, that i'm aware that it's atheros problem), the HDD it's like this: partition 1: WIN XP 27 gb(ntfs) partition 2: DATA 107 gb(ntfs) part3:LINUX 15-20 gb(ext3) part 4:linux swap 1 gb(swap).

So, i installed, no prob, i updated all via wired connection (eth0) so far so good, so i thought "lets hear some music while this thing updates", so i double clicked the win xp partition, it asked me for my sudo pass si it could mount, no problem there, i coul browse that partition and open files, but then i wanted to hear my main music collection (that it's on "DATA") so i double clicked "DATA" asked me for the sudo pass, i wrote it, it started like reading it an then he file browser window got grey and froze, i could do other things like use firefox or open other apps but the file browser was dead, if i clicked the X to close it would tell me that i had to "force" the closing, so i accepted and then it seems to me that all the file browser sistem dies and restarts since the icons of my mounted partitions/drives dissapears and appears like 1 minute after.

I thought, well maybe it's because the partition it's big, maybe it was indexing or something, so the nex time i let it like 1 hour alone after double clicking "DATA", it showed me my folders but if i double clicked them to open them it would again take forever and get grey (damn..)

The not so funny thing it's that on the live cds (RC by the way) the file browser doesn't hang/freeze. so i dont know what to do.

Wireless i can live without it... but no access to my work ans personal files? no way...

This happens with kubuntu 8.10 and ubuntu 8.10 fully patched 32 bit(from RC to release)

So I REALLY WANT TO USE LINUX, im willing to try everything even touching code (if you let me know how). so if anyone here has an idea, please write.

THANKS

BTW, if i'm posting in the wrong forum section please move it.
Ah, and sorry about the grammar ^^u

---

### Post by Ron from MD on 2008-11-02
Same thing happens to me with Hardy, if I try to access anything in my home folder the file browser greys out and freezes. It will unfreeze after a bit without opening anything but to close it I have to force quit and it keeps popping back up.....the only way out of the force quit cycle is to restart the machine.

---

### Post by Gilreygar on 2008-11-02
> **Ron from MD said:**
> Same thing happens to me with Hardy, if I try to access anything in my home folder the file browser greys out and freezes. It will unfreeze after a bit without opening anything but to close it I have to force quit and it keeps popping back up.....the only way out of the force quit cycle is to restart the machine.

Thanks for the reply :)

as an update: i tought it was the indexing but i turned off and i still have the problem. i opened the "resources monitor" (the windows that shows my ram/swap/cpu used) and it's normal, but when i try to open the drive one of my cores goes to 100% and never goes down until the file browser shows my files. 

Because of that i tought it was the indexing.. but nope T_T

---

### Post by Ron from MD on 2008-11-02
> **Gilreygar said:**
> Thanks for the reply :)

as an update: i tought it was the indexing but i turned off and i still have the problem. i opened the "resources monitor" (the windows that shows my ram/swap/cpu used) and it's normal, but when i try to open the drive one of my cores goes to 100% and never goes down until the file browser shows my files. 

Because of that i tought it was the indexing.. but nope T_T

Yep, one of my cores goes to 100% usage as well. I don't yet know enough about Ubuntu to even guess the cause. I'm still trying to learn how it names drives.......;)

---

### Post by piloupuc on 2008-11-03
Same thing has been happening to me since I upgraded from 8.04 to 8.10.

I have 2 disks: disk 1 has 3 partitions: sda1 (ntfs), sda2 (ext-3) and sda3 (linux-swap
disk 2 has 2 partitions: sdb1 (ntfs) used for windows system and sdb2 (ntfs) used for data

It looks as if sdb2 partition is corrupt (rythmbox & nautilus freeze when I access data on sdb2). Processor activity is normal, though.
This is very problematic since I very often save data on sdb2 so I can access it both from ubuntu and from windows.

I ran the Maxtor disk-checking tools and everything was OK. 
Also, when I boot Windows I get no errors.
I even reformated the problematic drive, but the problems remain.

Not sure what to do next... Any ideas?

---

### Post by Gilreygar on 2008-11-03
Hi, thanks to all that have posted, more info from me (hopefully we will solve it soon?)

Since i had seen that i'm not the only one affected i tought that maybe if it wasn't the file browser, maybe it was the thing using the file system.. and since we all use ntfs i looked to see what was handling ntfs...so it turns out that it's ntfs-3g, so i look in the syslog and see that ntfs-3g gives some weird error when accessing my "DATA" disk wich was the following.

> ntfs_atrr_pread error reading '/msvci70.dll' at offset 0: 16384 <> 0: No existe el fichero o directorio

ntfs_attr_pread error reading 'msvci70.dll' at offset 0: 4096 <> 0: No existe el fichero o el directorio

For those not fluent in spanish it says that it can't find the file or directory "msvci70.dll"

So since i was a lazy bum i decided to see if it was a newer version of ntfs-3g on the net so i opened synaptic and saw that apparently it was up-to date but the file was "ntfs-3g-ubuntu" or something like that so i again searched for the home page of ntfs3g and apparently it was a NEWER version (1.5 something on the site versus 1.2 something in ubuntu) so since i'm a newbie i downloaded then unpacked it, then ./configure, make, sudo make install.

So i unmounted everything, and mounted them again (the home page says that) and voilá ! i can now see my "DATA" hard drive instantly !! :):):)

But as life goes and since life isn't perfect, now it turns out that i can SEE the files on my HDD but i can't acces them, i can't open a single file but i can browse the disk....

Maybe it's because it's not an "ubuntu version". or maybe ther are some permissions not asigned, who knows.... but at least we're progressing os far i think...

I hope this helps someone, and since fixing this seems so fun (i'm learning. weeee!) i will try to get a happy ending xD

till next post ;)

---

### Post by piloupuc on 2008-11-04
Hmm, nice work!

The thing is, my other NTFS drives work perfectly, both read and write, from Ubuntu. So I assume that in my case NTFS-3g is probably not the cause, unless it has a specific problem with this particular drive?

---

### Post by Gilreygar on 2008-11-04
Thanks :)

Well, maybe it's the drive.. you tried "updating" ntfs-3g? maybe this will correct your problem (just remember that it also created a new problem to me..)

in case this helps my HDD is a Hitachi HTS542516K9SA00 (160GB)

now the update:

i checked syslog again and it seems that ntfs-3g is spitting some error when trying to read the drive, it says that an Inode flag on XXX place is corrupted and then says I/O error.

For what i read Inodes are like files that linux uses (unix-Oses) to store the info of the files, so if the os can't read them they cant access the files...i think..maybe.. couldn't grasp the concept at 100%.

fsck doesn't work with ntfs files or at least thats what the help on the terminal says, so i don't think i can fixit on linux.

Keep in mind that on windows the drive is fully accesible, i can read/write everything....

i'll keep you posted ;)

---

### Post by Ron from MD on 2008-11-06
I run 4 WD SATA II drives and Ubuntu can see them all just fine. I can access everything but the following folders: Home, Ron, Root. Those three cause the freeze then the force quit cycle until I restart. All four drives are NTFS but three of them are strictly data storage. XP Pro sees them all of course but I really want to migrate away from XP well before it goes EOL. I've tried going in through Nautilus with my password and it will display the contents of the three folders but only once then if I try to anything other than quit it freezes.

What's really frustrating is I want to get into the downloads folder and I want to try some copy dll tricks on a couple of apps I'm trying to get to run in wine and Crossover but those two are buried somewhere in one of those three folders.

---

### Post by Ron from MD on 2008-11-07
OK, I upgraded to 8.1 and the file manager still freezes if I try to access Home, Ron or Root but force quit at least makes it really quit and not keep popping back up.

---

### Post by piloupuc on 2008-11-07
Well I decided that it was enough and moved my data to another partition, also under NTFS, but this one does not freeze. So I guess even though I didn't really fix the problem, at least it is not an issue for me anymore.

I still don't understand why the other partition would be perceived as corrupt by Linux and as perfectly OK by Windows and most of all by the manufacturer, Maxtor!!!

And these problems started to appear when I upgraded to Intrepid.

---

### Post by piloupuc on 2008-11-07
> **Ron from MD said:**
> I run 4 WD SATA II drives and Ubuntu can see them all just fine. I can access everything but the following folders: Home, Ron, Root. Those three cause the freeze then the force quit cycle until I restart. All four drives are NTFS but three of them are strictly data storage. XP Pro sees them all of course but I really want to migrate away from XP well before it goes EOL. I've tried going in through Nautilus with my password and it will display the contents of the three folders but only once then if I try to anything other than quit it freezes.

What's really frustrating is I want to get into the downloads folder and I want to try some copy dll tricks on a couple of apps I'm trying to get to run in wine and Crossover but those two are buried somewhere in one of those three folders.
How about copying the files you need on an external drive or USB key, from the Windows side and then onto a non-corrupted folder in Ubuntu?
At least then you might be able to try to run these apps you want in Wine & Crossover.

---

### Post by Ron from MD on 2008-11-07
> **piloupuc said:**
> How about copying the files you need on an external drive or USB key, from the Windows side and then onto a non-corrupted folder in Ubuntu?
At least then you might be able to try to run these apps you want in Wine & Crossover.

Because I can't get to the wine folders. Since they're apps critical to actually working I may just say hell with it and go back to windows, dual boot is not an option.

---

### Post by Ron from MD on 2008-11-08
Get this through syunaptic: pcmanfm and it works.

---

