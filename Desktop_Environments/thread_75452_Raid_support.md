---
title: "Raid support"
date: 2005-10-13
forum: Desktop Environments
---

### Post by ismimyok on 2005-10-13
Hi,

Does Breezy support ITE 8212 raid card? (I know Hoary didn't.) If it does my installation fails to see my harddrives on the raid card. If it doesn't could you PLEASE include it in the next version? I read from previous posts that it needed to be included into kernel and it is posible to put together a custom kernel, but I don't have the technical ability to that, and it looks like there are many people like me who use this raid card, and isn't caple of creating his own kernel. I know that OpenSuse 10 supports this raid card, if that one can I am sure Ubuntu can too.

Thank you,

---

### Post by ismimyok on 2005-10-16
Am I the only one who requests this? What happened to all other people who poted before me? Have you all been able to fix the raid problem?

Somebody please help me!

---

### Post by Dark79 on 2005-10-16
If it helps any, I'm in the process of trying to get the it821x module working so that my system can detect the it8211 controller on my P5WD2 motherboard. But I'm having a lot of problems so far. Been working on it for the last couple of days without any real progress. I consider myself a linux newbie so that could be why it's taking so long.

I had it working under Hoary, but I had to compile 2.6.13 kernel for it to work. For some reason that's not working for me under Breezy but I don't know if I'm missing a step (which might be the case since I haven't done a kernel compile in a while). Just to be on the safe side I'm applying a patch to the ubuntu patched kernel that is supposed to give me it821x support, but isn't quite working yet. I can modprobe the driver just fine, but rebooting the computer gives me a "can't find drive" error.

Also, since I'm compiling the kernel after installing Breezy, my method's only going to work if you have a working IDE controller under Breezy so that you can still run Ubuntu to compile the custom kernel. If this isn't the case, you're on your own.

If I come up with a solution, I'll be sure to post. But right now I don't see light at the end of the tunnel any time soon.

---

### Post by nighthawk39 on 2005-11-26
I too have the same problem.  I can't install Ubuntu 5.10 because of that.

ASUS P5WD2
it8211

---

### Post by sergiopereira on 2006-01-11
Count my vote to get this in soon. I have a Gigabayte mobo with the IT 8212F raid chip onboard (they call it giga-raid). I cannot install ubuntu b/c the installation does not recognize that controller and I cannot recompile the kernel (I am willing to learn how to do that) with all the mentioned patches and code from ITE but I don't even have another ubuntu installation to do that.
I think this controller seems to be rather common in current hardware, deserving out of the box support.
I'm also willing to get involved in fixing this, if needed, at least testing the fixes.

Thanks
  - Sergio

---

### Post by mntbighker on 2006-01-11
Add my vote. I accepted the fact I would have issues with this when I opted to switch to Ubuntu from what I read. I was using Linux software RAID under Mandriva but I want to switch to using the built-in RAID on my MoBo. The question is really, what are the advantages to doing so? I was hoping Linux would see my striped RAID as one single ATA device that I could partition XFS/NTFS. So far I have had limited success even getting the BIOS set up. I hope Breezy gets an updated kernel with the RAID support patched in.

Lets get a discussiuon going on those who get this working and what real world benefits are realized over a simple Linux software RAID. I used mine for over a year with no RAID specific problems until I managed to let the Mandriva installer erase it for me :-(

--MM

---

### Post by jazz on 2006-01-11
Ok, u can count me in too.. to get this controller supported soon !
So for that time, i'll either have to look into Gentoo, or just stick to windows for a while :( 

Thanx,
jazz

---

### Post by sergiopereira on 2006-01-16
Since it does not look like I will be able to run Breezy anytime soon, I installed Fedora Core 4 with virtually no effort. I'm hopping next release of Ubuntu supports this chip because I really want to try Ubuntu.

---

### Post by shmoolik on 2006-02-24
I too have a ASUS p5LD2 and i must say that i have so saport at all with my IT8211 controler 
plz add this drivers to the next release of Ubuntu

---

### Post by sergiopereira on 2006-04-21
Good news. I downloaded and booted the 6.06 Beta LiveCD today and it (finally) detected my ITE 8212 correctly and I was able to access my existing partitions, including NTFS ones. I did not take the further step of overwriting my Fedora Core 5 (upgraded from FC4 recently) yet 'cos I'll wait for the official release to do so.
I hope this means it will work when I try to install it in June.

---

### Post by shmoolik on 2006-05-25
[QUOTE=sergiopereira]Good news. I downloaded and booted the 6.06 Beta LiveCD today and it (finally) detected my ITE 8212 correctly and I was able to access my existing partitions, including NTFS ones. I did not take the further step of overwriting my Fedora Core 5 (upgraded from FC4 recently) yet 'cos I'll wait for the official release to do so.
I hope this means it will work when I try to install it in June.[/QUOTE]
i have tryed to install the beta with now secsess ( the same problem no it8211 support )

---

### Post by justmoon on 2006-10-08
6.10 Edgy Eft Beta

Hmm, doesn't seem to be fixed yet. Installation doesn't detect ITE8212 on ASUS P5WD2 Premium.

(Gentoo Minimal LiveCD works fine since 2005.0, what's the hold-up? I really want to try Ubuntu.)

Is there any kernel parameter I can give to make him load the ite821x kernel module, cause that seems to be all he's missing, is it not?

---

### Post by shmoolik on 2006-10-08
The only way i found is to install sata HDD... and don't bother to buy one for Ubuntu the system is very havy and slow.

---

