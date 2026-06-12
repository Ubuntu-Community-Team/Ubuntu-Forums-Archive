---
title: "Questions about Virus(es)"
date: 2008-12-22
forum: General Help
---

### Post by Guns90 on 2008-12-22
Hello all.  I haven't been here in a long while.  I was finally beat down by my family about them not being able to do the things the way they wanted to on our computer (meaning they wanted windows back), so I built a new computer  and dual booted it with Vista and Ubuntu 7.10.  They have all been quite happy until a major virus took over a couple of days ago.I've now given the kids their own computer, told my wife to either get used to what I have, or go use the kids computer, but I'm done with M$!

I don't know how computers work, so I don't understand what exactly is infected on my computer.  I cannot boot into Vista, and if I tell Grub to  boot into Feisty on the other drive, I get in, but the virus messes with ubuntu also after a while.  

My questions are (and I realize that that no one can really be specific 
without diagnosing my computer, so just answer as best as you can, please):

1) Do viruses infect all of the hardware in a computer, or do they generally target something specific like the hard drives, graphics card, and motherboard?

2) Do viruses corrupt the processor? 
 
What I want to do is fix this the infected computer as economically as possible by trashing only what I must.  What say you experts?

---

### Post by beno1990 on 2008-12-22
> **Guns90 said:**
> 
1) Do viruses infect all of the hardware in a computer, or do they generally target something specific like the hard drives, graphics card, and motherboard?


Neither - Viruses are software, not hardware. They merely interrupt the normal functioning of your software, and the way your operating system communicates with the hardware in some cases.

> 
2) Do viruses corrupt the processor? 


No - As I said above, viruses are software, not hardware related. The most they can do is interfere with how your computer *uses* the hardware.

> 
What I want to do is fix this the infected computer as economically as possible by trashing only what I must.  What say you experts?


Reinstalling Windows or installing Ubuntu to over-write Windows completely will fix the problem, if you're not willing to pay for antivirus software.

---

### Post by Guns90 on 2008-12-22
Thanks beno1990, I told you I know NOTHING about how a computer works. 

Because of my lack of knowledge, I was assuming that every piece of hardware has software incorporated in it to make it work, and that was what was being infected.  My bad.  Thanks for the info.  

Oh, the infected computer had McAfee and Symantec on it and it still got infected.  I think I payed $150 for those two programs, which I purchased three and five months ago respectively. That's why I'm done with Microsoft. If the rest in my house don't want to learn how to use linux, they can go pound salt.

---

### Post by hursto75 on 2008-12-22
Viruses can seem to effect hardware, but they are only making software changes within that hardware. If that makes sense. A virus can change the partition table on your hard drive makeing the drive look like it is not there. A virus could change some settings within your os to make it look like your Network card is missing. But ultimately the virus is only effecting the software on the hardware itself or in the OS.

Thans

---

### Post by benny bronx on 2008-12-22
One of your problems may have been having two antivirus programs at the same time.  If they are both running real-time, you are almost guaranteed to have problems and, if one is real-time and one on demand, conflicts can still happen. I remember when I was running KAV 6 and decided to try out bitdefender 8's on demand scanner, I swore I heard my computer let out this little scream before completely locking up.

---

### Post by Cope57 on 2008-12-22
> **Guns90 said:**
> Thanks beno1990, I told you I know NOTHING about how a computer works.

Not to be mean, but why own one then?

If you own a vehicle, you should learn how to drive.
If this is your first computer, you have a lot to learn. Good luck with your studies...

Google is your friend, he knows very much. ;)

---

### Post by Slim Odds on 2008-12-22
I see some comments that viruses are only software.....

But, since most computers now use FLASH memory for their BIOS, it is possible for a virus to reprogram the BIOS.

This creates a MUCH more difficult problem to recover from. Some viruses will WIPE OUT the BIOS altogether. In a case like that, you're screwed pretty bad.

---

### Post by bodhi.zazen on 2008-12-22
> **Slim Odds said:**
> I see some comments that viruses are only software.....

But, since most computers now use FLASH memory for their BIOS, it is possible for a virus to reprogram the BIOS.

This creates a MUCH more difficult problem to recover from. Some viruses will WIPE OUT the BIOS altogether. In a case like that, you're screwed pretty bad.

I have seen those types of infections and all that needs be done is flash the bios.

But I agree with the OP, While windows has some nice features, security is not one of them. Yes I know Windows can be "hardened" but most users do not do this, they just use the OS as it was installed and set up by whoever installed Windows.

The problem is also antivirus can not yet protect you from "zero day exploits".

---

### Post by Slim Odds on 2008-12-22
> **bodhi.zazen said:**
> I have seen those types of infections and all that needs be done is flash the bios.

Depends on the system; some are easy, some are not.

---

### Post by TeXtonyx on 2008-12-22
Anti-virus software is a defensive measure. If somebody downloaded
malware and chose to install it, or when browsing the web gave an
OK to install some wolf in sheep's clothing program, then the
anti-virus software can be circumvented, because to the computer
it is just as if you deliberately installed the program. It does
not know you've been duped. 

There are software areas, vulnerable locations on your hard drive,
that are outside your Windows partition. It is possible to format
your entire hard drive and not remove a virus, but that is rare.
Some of the hardware has what is called firmware, quasi-software.
Usually just formatting your Windows partition and doing a clean
install will clear the virus. Adding the anti-virus should be one
of the very first programs to reinstall after a clean sweep, just
after the drivers for your hardware. 

You have to warn your family about lettings strangers into your
computer. Don't open email attachments unless the sender of the
email mentions the attachment by name; all those chain mails that
relatives like to send you. Schools still teach using Windows
programs and it is too much to expect for kids to learn how to do 
it on Linux also, and translate or convert back and forth. When 
they get jobs, 99% of them will have to use Windows programs.

---

### Post by lykwydchykyn on 2008-12-22
Not to sound condescending, but are you quite certain you have a virus, and not some kind of hardware issue?

The reason I ask is when you say "the virus starts affecting Ubuntu".  I don't see how that would be, if it's a windows virus sitting on a windows partition, that it would ever impact your Ubuntu install.  

Can you describe the symptoms you're seeing?  Sometimes bad RAM or bad spots on the HD can cause errors that many users mistake for virus or spyware activity.

---

### Post by Guns90 on 2008-12-22
I appreciate all the responses, guys.  It appears that I have my computer up and running again.  

I downloaded the latest release of Ubuntu linux, copied it to a CD, installed it on drive C, and I reformatted my second hard drive. Everything seems to be working pretty good right now.  I had a little trouble at first with my sound driver, but a little research took care of that.  I know it will be a fairly long time (if ever) to get all programs to work as they do on windows, but I'm a lot happier now knowing that there are a comparatively minuscule number of hackers out there writing bad stuff for linux as compared to the numbers writing junk for windows.  I used linux for three years without one incident before.  

Thanks again guys.

---

