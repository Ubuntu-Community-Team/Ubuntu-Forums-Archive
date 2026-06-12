---
title: "Need Adware/Spyware app for Ubuntu"
date: 2008-11-13
forum: Desktop Environments
---

### Post by TWGTech on 2008-11-13
Before you get your "Linux can't get adware/spyware" lines out, That's not what this is for.

I am using Ubuntu to clean a friends hard drive (it's SATA, and the only SATA system I have is Ubuntu 8.04.1, no other OS).

That being said, is there any Adware/Spyware utility that can run under Debian that I can use to clean this Windows hard drive?

And i'm not going to install Ubuntu. It's a friends, and I don't have the time nor inclination to teach her how to use a new OS.

Thanks in advance to those who can answer this question (even if it's "No, there is no such thing").

---

### Post by prshah on 2008-11-13
> **TWGTech said:**
> 
I am using Ubuntu to clean a friends hard drive (it's SATA, and the only SATA system I have is Ubuntu 8.04.1, no other OS).

That being said, is there any Adware/Spyware utility that can run under Debian that I can use to clean this Windows hard drive?


If you don't mind commercial, you can try Kaspersky (Linux version); it's low-cost, fast and reliable.

---

### Post by TWGTech on 2008-11-13
Thanks, prshah.

A little bit more than what I was looking for (and, of course, free is good).

Still looking. Something like AdAware or Spybot would be great.

---

### Post by prshah on 2008-11-13
> **TWGTech said:**
> 
A little bit more than what I was looking for (and, of course, free is good).
Still looking. Something like AdAware or Spybot would be great.

[F-Prot Free for Linux]("http://www.f-prot.com/products/home_use/linux/") - Free for personal use on personal workstations.

Yeesh, just took a look at the Kaspersky e-store; the prices are over 3.5 times the street price. No wonder you didn't feel it worth it.

Kaspersky is very good value for money and very popular especially because of it's low (street) price. I'll have to remember to avoid it's e-store in the future.

You can also setup a VM in VirtualBox, install a good Windows Antivirus / Ad-Aware / Spybot and use that to scan the "friend's" hard disk.

---

### Post by TWGTech on 2008-11-14
Thanks for the fprot idea. I ran the online version last night (i can only get her system into safe mode w/ networking), and it said it found 29 viri!! It only got to the 3rd one cleaned before the machine started fighting it.

The VM idea is a good one. I'll keep that in mind. I'm also going to hook up one of my hardenend systems to it and try to get it from there.

Also, this is an 18 year olds computer, not one of mine, so "friend" is friend. If it was mine, I'd have formatted it by now.

---

### Post by prshah on 2008-11-14
> **TWGTech said:**
> so "friend" is friend. If it was mine, I'd have formatted it by now.

I didn't mean it that way; I've always put "friend" in quotes after advising someone to "replace with a good hard disk" and mis-spelling the last word ("c" instead of "s").

(On re-reading, this post doesn't make much sense.. I guess it's not much of an explanation out of context).

---

### Post by TWGTech on 2008-11-14
LOL!! I see. I always took the quotes to mean "yeah, sure, your "friend"".

I seem to be making progress with Trend Sysclean utility and the Malwarebytes app. Both are win apps, but I was finally able to get into safemode where I can actually do some work.

It trashed spybot and f-prot.

Anyway, thanks for the advice. Much appreciated.

---

### Post by mitchroberts on 2008-12-01
looking for antivirus for linux to clean windows drive maybe one
of these.The avast and avg has spyware scanner built in and the rest i do not know about.
good luck

free.avg.com/download 

[www.clamav.net/](www.clamav.net/)

[www.pandasoftware.com/download/linux/linux.asp](www.pandasoftware.com/download/linux/linux.asp) 

[www.avast.com/eng/download-avast-for-linux-edition.html](www.avast.com/eng/download-avast-for-linux-edition.html)

---

### Post by ScarySquirrel on 2008-12-01
WINE might work for this, if a simple windows spyware checker is already on the hard disk.  
     When run in WINE, rootkits should not be able to get at the windows malware checkers already installed.

---

### Post by Swagman on 2008-12-01
This is actually an interesting topic.

It would be extremely handy to have an Ubuntu install on a USB pendrive if Avast etc would work in Wine.

I have a 16gb pendrive.. Methinks a little "Play" is imminent.

---

### Post by mitchroberts on 2008-12-02
oh no don't use wine advast has a copy for linux.

---

### Post by C. Wizard on 2008-12-02
I've used ClamAV to scan NTFS partitions, but I don't remember if it has any spyware seeking abilities.

---

### Post by TWGTech on 2008-12-05
Thanks to all for your suggestions. I did play with WINE a bit, as well as ClamAV and Avast for Linux.

Bottom line...I still F&R'd her. The bug was dug in too deep, and after a weke of trying to rip it out, decided to go through the pain of a rebuild. At least this time I was able to get my stuff on it before she got ahold of it.

I am, however, going to build a bootable USB drive in order to better handle stuff like this moving forward, so if anyone has any suggestions on configuration/softwrae/etc..., I'm all ears.

---

### Post by Craftycorner on 2008-12-07
OMG!  It was viruses that made me ditch Windows entirely for email and mostly for surfing except a very few safe sites.  Regardless, the friend should have a copy of Avast Free on her Windows.  

But what bugs is the Avast for Linux thinks that the Lavasoft maleware detector is a trojan and pitches a fit when I scan.:mad:

---

### Post by mitchroberts on 2008-12-09
avg also has a spyware scanner in there antivirus if it helps

---

### Post by Saghaulor on 2008-12-10
I would be very interested in a bug cleaner for windows via ubuntu, especially ran from a flash drive or live cd.

Normally, I'd just recommend a format as its safer, and usually quicker, but sometimes formatting just isn't the best option.

So please, if anyone has any ideas or has something already setup for this purpose, please chime in.

---

### Post by mattman85 on 2008-12-10
> **Saghaulor said:**
> I would be very interested in a bug cleaner for windows via ubuntu, especially ran from a flash drive or live cd.

Normally, I'd just recommend a format as its safer, and usually quicker, but sometimes formatting just isn't the best option.

So please, if anyone has any ideas or has something already setup for this purpose, please chime in.

It may not be Ubuntu-based, but there are a number of liveCDs that might have what you want..  
[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")
[http://www.hiren.info/pages/bootcd]("http://www.hiren.info/pages/bootcd")
[http://www.bootdisk.com/]("http://www.bootdisk.com/")
[http://www.e-fense.com/helix/]("http://www.e-fense.com/helix/")

I used Ultimate Boot CD and Helix quite a few times in college. Ulitmate Boot CD has a few AV programs on it.

My computer forensics classes used Helix a lot, as its an incident response / forensics bootable liveCD.  It has ClamAV on it.

I can't remember off-hand about UBC, whether their one AV prog does do bug cleaners.  ClamAV might work as a bug cleaner.  I haven't used it enough to know yet.

---

