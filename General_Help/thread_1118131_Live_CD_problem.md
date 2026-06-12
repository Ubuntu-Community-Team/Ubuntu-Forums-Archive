---
title: "Live CD problem"
date: 2009-04-06
forum: General Help
---

### Post by mynameinc on 2009-04-06
I have a problem with Ubuntu. I downloaded it from ubuntu.com, made a Live CD. When I tried to boot from the CD drive, it gives me:
"PXE-E61: Media test failed, check cable
 PXE-M0F: Exiting Broadcom PXE ROM"

What is the cause for this? And how can I fix it.

My computer:
Dell Inspiron 1501 
Windows XP Media Center Version 2002 Service Pack 3
AMD Turion 64 Mobile
Technology MK-36
1.99 GHz
896 MB of RAM
Physical Address Extension
ATI Radeon Xpress 1150
TSSTcorp CDRW/DVD TSL462D

I have three devices I haven't installed drivers for because I reinstalled XP recently and they weren't hurting anything, so I never "wasted" the time. 

But thanks in advance,
mynameinc

---

### Post by r1ch on 2009-04-06
This may be a shot in the dark but do you get to the first option menu on the CD and is there a selection available to check the integrity of the CD?
I had huge problems recently with downloaded and burnt Ubuntu images to CD where my drive was unable to burn it accurately and so I never got an installation performed successfully (until i borrowed a disk from a friend).
If it fails this check then you could try a couple of different CD's or one from a magazine cover perhaps.

Just a thought.

---

### Post by kanikilu on 2009-04-06
> **mynameinc said:**
> "PXE-E61: Media test failed, check cable
 PXE-M0F: Exiting Broadcom PXE ROM" That looks like it's trying to network boot (PXE). When you start your computer with the CD in, as soon as it gets to the Dell screen, start pressing F12 to choose a boot device. When you get to the temporary boot device menu, choose the CD/DVD-ROM.

If that fails to boot, try the CD in another computer, or simply make a new one, as something may be wrong with that one. If you need to make a new one, it would probably be worth re-downloading if you have a relatively fast connection, then use [ImgBurn](http://www.imgburn.com/) to burn the ISO image to a new disc.

---

### Post by mynameinc on 2009-04-06
> **r1ch said:**
> This may be a shot in the dark but do you get to the first option menu on the CD and is there a selection available to check the integrity of the CD?
I had huge problems recently with downloaded and burnt Ubuntu images to CD where my drive was unable to burn it accurately and so I never got an installation performed successfully (until i borrowed a disk from a friend).
If it fails this check then you could try a couple of different CD's or one from a magazine cover perhaps.

Just a thought.

I think I understand your post, but I don't see any option menus other than the one to boot after I press F12.

---

### Post by mynameinc on 2009-04-06
> **kanikilu said:**
> That looks like it's trying to network boot (PXE). When you start your computer with the CD in, as soon as it gets to the Dell screen, start pressing F12 to choose a boot device. When you get to the temporary boot device menu, choose the CD/DVD-ROM.

If that fails to boot, try the CD in another computer, or simply make a new one, as something may be wrong with that one. If you need to make a new one, it would probably be worth re-downloading if you have a relatively fast connection, then use [ImgBurn](http://www.imgburn.com/) to burn the ISO image to a new disc.

I chose the CD/DVD-ROM. And it took well over an hour to download (but I was surfing YouTube at the same time).

So try it on this compy again, then if that fails, try it on another one, then if that fails, make a new CD, and if that fails re-download it?

---

### Post by mynameinc on 2009-04-06
Tried it again, made sure I selected CD/DVD, (PXE was under it), hit enter, same problem again.

---

### Post by r1ch on 2009-04-06
> **mynameinc said:**
> I think I understand your post, but I don't see any option menus other than the one to boot after I press F12.

Sadly I don't have any CD's to be able to recreate/find the menu options that I mentioned. Fortunately kanikilu's advice sounds like a much better avenue to enquire down.

Good luck solving your problem.

---

### Post by kanikilu on 2009-04-06
> **mynameinc said:**
> So try it on this compy again, then if that fails, try it on another one, then if that fails, make a new CD, and if that fails re-download it? Yes.

> Tried it again, made sure I selected CD/DVD, (PXE was under it), hit enter, same problem again. Yeah, that sounds like a problem with the CD. If you have another computer, try that, otherwise, try burning it again.

A common problem is that people accidentally make a *data* disc with the ISO file on it. Make sure you select "burn ISO or CD image" in whatever software you are using, or just download and use the free ImgBurn utility.

---

### Post by mynameinc on 2009-04-06
> **kanikilu said:**
> Yes.

 Yeah, that sounds like a problem with the CD. If you have another computer, try that, otherwise, try burning it again.

A common problem is that people accidentally make a *data* disc with the ISO file on it. Make sure you select "burn ISO or CD image" in whatever software you are using, or just download and use the free ImgBurn utility.

Is there an easier way to install Ubuntu?

And would me making a data disk be responsible for this problem?

---

### Post by kanikilu on 2009-04-06
There are a number of installation methods, I'd say the easiest/quickest is the standard install from a CD, though. But that's just my opinion...

- Standard install from CD
- Portable Ubuntu run inside of Windows: [http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows](http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows)
- Wubi, installs and uninstalls like a regular windows program, but runs like a dual boot (you have to restart your computer any time you want to access Ubuntu): [http://wubi-installer.org/](http://wubi-installer.org/)
- As a virtual machine in VMWare or the free VirtualBox: [http://www.virtualbox.org/](http://www.virtualbox.org/)

...others?

---

### Post by kanikilu on 2009-04-06
> **mynameinc said:**
> And would me making a data disk be responsible for this problem? Yes, open the CD in Windows, if you see a single .iso file rather than a whole list of files and folders, that's what happened...

---

### Post by mynameinc on 2009-04-06
> **kanikilu said:**
> Yes, open the CD in Windows, if you see a single .iso file rather than a whole list of files and folders, that's what happened...

So how do I write it to the CD the other way? I just sent the file to the D: Drive and then wrote it to a CD using the programs that come with Windows. 
 
And thanks for all the help so far.

---

### Post by kanikilu on 2009-04-06
Download and install the program I linked to earlier called ImgBurn. It's a small free utility that specializes in writing images, so it's hard to mess up...

---

### Post by mynameinc on 2009-04-06
> **kanikilu said:**
> Download and install the program I linked to earlier called ImgBurn. It's a small free utility that specializes in writing images, so it's hard to mess up...

Is there another way? I hate to download on Windows, for obvious reasons.

---

### Post by kanikilu on 2009-04-06
Sorry? Uh...no I don't think Windows comes with a built-in method to burn ISO images. I've used that program before and there shouldn't be any problem. There are other programs you can use to burn ISO's (both free and commercial software), but either way you'll need to download *something*. If you don't care to try...well, good luck...

Just out of curiosity, how do you use Windows without downloading anything? It comes "out of the box" with almost *nothing*...

---

### Post by mynameinc on 2009-04-06
> **kanikilu said:**
> Sorry? Uh...no I don't think Windows comes with a built-in method to burn ISO images. I've used that program before and there shouldn't be any problem. There are other programs you can use to burn ISO's (both free and commercial software), but either way you'll need to download *something*. If you don't care to try...well, good luck...

Just out of curiosity, how do you use Windows without downloading anything? It comes "out of the box" with almost *nothing*...

I download from reliable sources, such as Mozilla or Sony.

---

### Post by kanikilu on 2009-04-06
CNet is reliable, and it says it's "tested spyware free":

[http://download.cnet.com/ImgBurn/3000-2646_4-10847481.html](http://download.cnet.com/ImgBurn/3000-2646_4-10847481.html)

What more assurance do you need?

By the way, don't just blindly trust a big-name brand...someone correct me if I'm wrong, but didn't Sony have the whole "rootkit on Windows as a copy-protection scheme for some CD's" debacle? :rolleyes:

---

### Post by mynameinc on 2009-04-06
> **kanikilu said:**
> CNet is reliable, and it says it's "tested spyware free":

[http://download.cnet.com/ImgBurn/3000-2646_4-10847481.html](http://download.cnet.com/ImgBurn/3000-2646_4-10847481.html)

What more assurance do you need?

By the way, don't just blindly trust a big-name brand...someone correct me if I'm wrong, but didn't Sony have the whole "rootkit on Windows as a copy-protection scheme for some CD's" debacle? :rolleyes:

I trust them because it seems stupid for a big-name brand to risk a large share of their profits because they were fined for a small malware violation.

---

### Post by kanikilu on 2009-04-06
I can appreciate the generous post-count padding this thread has provided, but I'm starting to wonder if this is some sort of belated April Fool's joke, lol :lolflag:

...if you want to burn an image on Windows, you'll need the right software. Either drive to your local computer store and pay $50+ for something like Roxio or Nero, or download and install any number of free programs that can do this: ImgBurn, InfraRecorder, CD Burner XP, whatever. 

InfraRecorder is open-source, by the way, so I would imagine if there was any malware, someone would have caught it.

Oh, and Sony *was* that stupid, just FYI: [http://en.wikipedia.org/wiki/2005_Sony_BMG_CD_copy_protection_scandal](http://en.wikipedia.org/wiki/2005_Sony_BMG_CD_copy_protection_scandal)

---

### Post by dk92123 on 2009-04-06
> **mynameinc said:**
> I have a problem with Ubuntu. I downloaded it from ubuntu.com, made a Live CD. When I tried to boot from the CD drive, it gives me:
"PXE-E61: Media test failed, check cable
 PXE-M0F: Exiting Broadcom PXE ROM"

What is the cause for this? And how can I fix it.

My computer:
Dell Inspiron 1501 
Windows XP Media Center Version 2002 Service Pack 3
AMD Turion 64 Mobile
Technology MK-36
1.99 GHz
896 MB of RAM
Physical Address Extension
ATI Radeon Xpress 1150
TSSTcorp CDRW/DVD TSL462D

I have three devices I haven't installed drivers for because I reinstalled XP recently and they weren't hurting anything, so I never "wasted" the time. 

But thanks in advance,
mynameinc
=======================================================================
Here is a Live USB Creator to use in windows, it works with any live cd including Ubuntu
[https://fedorahosted.org/liveusb-creator/](https://fedorahosted.org/liveusb-creator/)
--------------------------------------------------
[correction: #I need to read more carefully , skipped over the first part where it talks about PXE failure and "check cable" sorry :|
That's another good reason open source & community support is better: more eyes, less mistakes (and mistakes are corrected 
faster ;) 
>>Seriously, I apologise for not reading more carefully, It's one of my shortcomings
--------------------------------------------------
Also, make sure you select the boot from CD option not the PXE boot

---

### Post by mynameinc on 2009-04-06
kanikilu, I looked the program up on WP, and it was legitimate, and I installed it. It worked. You are my new hero. 

Thank you tremendously,
mynameinc

---

### Post by kanikilu on 2009-04-06
No problem. Sorry I was getting a little frustrated - heh, it's probably not a *bad* thing that you are cautious when it comes to downloading things on Windows that you haven't heard of ;)

---

### Post by mynameinc on 2009-04-06
> **kanikilu said:**
> No problem. Sorry I was getting a little frustrated - heh, it's probably not a *bad* thing that you are cautious when it comes to downloading things on Windows that you haven't heard of ;)

Do you have any good guides on *installing* Ubuntu?

---

### Post by orethrius on 2009-04-06
> **kanikilu said:**
> No problem. Sorry I was getting a little frustrated - heh, it's probably not a *bad* thing that you are cautious when it comes to downloading things on Windows that you haven't heard of ;)

Not to start anything here, but isn't trusting Wikipedia over several outside sources a bit of a bad trend?

---

### Post by kanikilu on 2009-04-06
> **orethrius said:**
> Not to start anything here, but isn't trusting Wikipedia over several outside sources a bit of a bad trend? Huh? I'm not trusting wikipedia over anything, it's just a *reasonably* good central source of information like this.

You'd prefer I link to every source individually? Ok...

How about BusinessWeek? [http://www.businessweek.com/technology/content/nov2005/tc20051129_685454.htm](http://www.businessweek.com/technology/content/nov2005/tc20051129_685454.htm)

The EFF? [http://www.eff.org/cases/sony-bmg-litigation-info](http://www.eff.org/cases/sony-bmg-litigation-info)

SecurityFocus? [http://www.securityfocus.com/news/11369](http://www.securityfocus.com/news/11369)

Straight from the horses mouth? [http://cp.sonybmg.com/xcp/english/home.html](http://cp.sonybmg.com/xcp/english/home.html)

// Edit - After mynameinc posted it just occured to me that you might be talking to him even though I linked to wikipedia...anyways...

---

### Post by mynameinc on 2009-04-06
Never mind.

But WP pwns all.

---

### Post by kanikilu on 2009-04-06
> **mynameinc said:**
> Do you have any good guides on *installing* Ubuntu? I would start here:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Just ask if you have more specific questions...

---

### Post by orethrius on 2009-04-06
Oops, sorry kaniklu, I just noticed that.  My bad. :lol:

I was indeed questioning mynameinc's willingness to rely on Wikipedia's track record over sworn testimonials (nothing personal, I just think Wikipedia has had one too many flub-ups for me to take them seriously anymore).

EDIT: And there is where I got sidetracked from providing the link to the download site for [Ubuntu Pocket Guide](http://www.ubuntupocketguide.com/download.html).  Perhaps he'd also be well-advised to backup anything of importance before diving into the installation process, in case anything should happen. ;)

---

### Post by mynameinc on 2009-04-06
> **orethrius said:**
> Oops, sorry kaniklu, I just noticed that.  My bad. :lol:

I was indeed questioning mynameinc's willingness to rely on Wikipedia's track record over sworn testimonials (nothing personal, I just think Wikipedia has had one too many flub-ups for me to take them seriously anymore).

EDIT: And there is where I got sidetracked from providing the link to the download site for [Ubuntu Pocket Guide](http://www.ubuntupocketguide.com/download.html).  Perhaps he'd also be well-advised to backup anything of importance before diving into the installation process, in case anything should happen. ;)

I trust WP articles with good sources and when the last edits have been by trustworthy editors.

---

