---
title: "How i can Install on MINI 12??"
date: 2009-03-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by miami2verona on 2009-03-31
Hi guys, i meet some problems to install ubuntu 8.04 on my mini 12!

How i can install ubuntu on my laptot??
There are 2 models of this laptot. The first is sell with ubuntu...and the second (with more power (1.60 ghz ecc)) with windows xp.

i bought the second because is better...but ubuntu doesn't run....
so...where is the problem???
i read that the possible error is the graphic card??? 
pls help me.

thx

---

### Post by timcredible on 2009-03-31
yes, it's the graphics card.  a friend at work has a mini 12 that he bought before dell offered ubuntu as an option, and he installed 8.10 on it, he had to do a search and found the video driver somewhere.  i'll ask him if he remembers where he found it and post to this thread again if i find it, but if you just do a search on this forum you'll probably find it.

---

### Post by miami2verona on 2009-03-31
i try to download ubuntu from *linux dell*

if don't run again.....i call dell support !!!!

**** off graphic card

---

### Post by miami2verona on 2009-04-01
update: i called dell support and they told me to call ubuntu support lol :popcorn:

---

### Post by sugarland2k on 2009-04-01
Dell support is mostly for hardware issues.  Good luck with a Linux O/S or software issues unless it is MS, it is also not US sourced..  I ordered a CD/DVD with my Mini 9 and loaded Kubuntu 9.04 9beta) and after a few update cycles it works great.  You can install Ubuntu/Kubuntu with an external CD/DVD or via a large capacity USB drive.

---

### Post by miami2verona on 2009-04-02
well, i try with usb.....and is impossible. So they sell laptot without cd/dvd player and is impossible to install linux os??? :lolflag:

So i want to  save some money to buy this pc....but i must to buy other pieces???  :mad:

---

### Post by anjilslaire on 2009-04-02
It is not impossible. You simply need to create a bootable USB drive with the linux installer on it, tehn set your Mini to boot from the usb and then start the installation.

It has been done on th mini 9, and I'm sure I"ve read it being done on the 12 as well.

---

### Post by miami2verona on 2009-04-03
how?? 
i try more and more times with usb....but every time the prolem was:

pen drive without system....

I try also with unebootin but there are other problem....

i try to install 9.04 beta ma he need internet connections....

So i must try with cd player ......The problem is INTEL GMA 500!!!
:(:(

---

### Post by jaqrah on 2009-04-05
The easy solution is virtualbox.  


[http://www.virtualbox.org/](http://www.virtualbox.org/)

Download the version for Windows.  Then, install Ubuntu .iso.  Virtualization is easier than dualbooting in many instances.

These two tutorials might also be helpful:

[http://seogadget.co.uk/how-to-install-virtualbox/](http://seogadget.co.uk/how-to-install-virtualbox/)

[http://forum.tinymelinux.com/index.php?topic=63.0](http://forum.tinymelinux.com/index.php?topic=63.0)

Good luck...and look for the Virtualization forum on this site if you have questions.

---

### Post by dk92123 on 2009-04-06
Good luck running a virtual machine with 1GB RAM and XP's page file. XP alone is slow as molasses on a mini 12 with all of the pre-installed software dell puts on it. Not trying to be rude but it won't work.

You need the Dell Ubuntu OEM Software. I got a refurbished mini 12 from dell outlet and it came with XP. I didn't think it would be a problem to get the ubuntu cd from dell but they routed me out of the country and I spoke to someone who said the will not send me the cd. 

Anyway, [B]I copied my buddy's recovery iso (DVD) and it worked perfectly. 
If someone can tell me how to extract the drivers needed, I'll be glad to email them to you.[/B]

---

### Post by dk92123 on 2009-04-06
Oh...and no, tried the bootable usb with ubuntu 8.04 & 8.10 & Fedora & openSUSE and it does not work.

-and-

The easiest way to make a bootable USB is to download the windows utility from the fedora website, it extracts the iso image onto tour flash drive and makes it bootable(w/any live linux cd not just fedora). -or- the 7-zip utility w/another app from USB Linux website, can't remember where but if you google it, its there.

Am I still on my 1st cup of ubuntu??? ;)

---

### Post by jaqrah on 2009-04-06
> dk92123  	
Re: How i can Install on MINI 12??
Good luck running a virtual machine with 1GB RAM and XP's page file. XP alone is slow as molasses on a mini 12 with all of the pre-installed software dell puts on it. Not trying to be rude but it won't work.

Well...I might be wrong and it wouldn't be the first time ;) but I have read about some pretty cool things happening on the Mini 9.  You know, people just fooling around **to see if it might work.**  The same is probably true about the Mini 12 and Mini 10.

It would still give it a try, what does anyone have to lose?  Its not like you are decimating your OS, making partition errors, etc.  You are just running an .iso to see if it works.  Definitely rid your machine of all the Dell bloat.

I recently picked up another mini 9 with 1gb ram 32gb ssd.  I have Ubuntu 8.10 as native and as vbox guests I am running (1)XP Pro SP3 with Office 2003 (2) WattOS Beta.  Everything works pretty damn well considering I am running it all on a netbook.

Imho...these are fun toys to play with, push their capabilities.  See just what they really can do...and for that matter what exactly they can't do.

Jaq

---

### Post by dk92123 on 2009-04-08
> **jaqrah said:**
> Well...I might be wrong and it wouldn't be the first time ;) but I have read about some pretty cool things happening on the Mini 9.  You know, people just fooling around **to see if it might work.**  The same is probably true about the Mini 12 and Mini 10.

It would still give it a try, what does anyone have to lose?  Its not like you are decimating your OS, making partition errors, etc.  You are just running an .iso to see if it works.  Definitely rid your machine of all the Dell bloat.

I recently picked up another mini 9 with 1gb ram 32gb ssd.  I have Ubuntu 8.10 as native and as vbox guests I am running (1)XP Pro SP3 with Office 2003 (2) WattOS Beta.  Everything works pretty damn well considering I am running it all on a netbook.

Imho...these are fun toys to play with, push their capabilities.  See just what they really can do...and for that matter what exactly they can't do.

Jaq

I'm impressed with your virtual machine success! My mini 12 has the dual 1.33GHz processors and 1GB mem (maxes out @ 1gb) and it seemed to struggle with XP alone, I'm guessing you have the dual 1.66Ghz on your vbox host but still I'm impressed with using 1gb mem.

Does 8.10 have the drivers for the dell mini? I tried a while ago booting it from a flash drive and didn't work out. I didn't feel like finding drivers and troubleshooting so I left 8.04 on it.

And I'm sorry for acting like a know-it-all, I'll try to be more humble in my opinions.
Thanks :)

---

### Post by ketanmnd on 2009-04-08
:KS When you buy a Mini 12 with Ubuntu you will get the dell cuztomized one. If you are able to find a ISO file of it or a friend has a cd you can burn the iso to a disc and put it in a usb drive. Or if you know some one who has the ubuntu dell disc then use that disc. If possible do it throw usb. Im not sure how you do it on a usb, but i think its possible. I did it throw usb cd drive from a iso of mini 12 ubuntu i found on the internet, after a quick download WA-LA! perfect working dell ubuntu

If you want normal ubuntu, your out of luck.

---

### Post by ketanmnd on 2009-04-08
ISO Image DELL Ubuntu (if needed) 
[http://thepiratebay.org/torrent/4446076/Dell_Mini_9_Ubuntu_Netbook_Remix_-_Restore_iso_image](http://thepiratebay.org/torrent/4446076/Dell_Mini_9_Ubuntu_Netbook_Remix_-_Restore_iso_image)

its not illegal because ubuntu is a free os
drivers i dont think is a problem, mini 9 ubuntu is pretty much the same.

---

### Post by notwen on 2009-04-08
Use [Unetbootin]("http://unetbootin.sourceforge.net/") to make a USB drive act like a Linux LiveCD.

---

### Post by 2oh1 on 2009-04-08
> **ketanmnd said:**
> ISO Image DELL Ubuntu (if needed) 
[http://thepiratebay.org/torrent/4446076/Dell_Mini_9_Ubuntu_Netbook_Remix_-_Restore_iso_image](http://thepiratebay.org/torrent/4446076/Dell_Mini_9_Ubuntu_Netbook_Remix_-_Restore_iso_image)

its not illegal because ubuntu is a free os
drivers i dont think is a problem, mini 9 ubuntu is pretty much the same.

Go to that site.  The first line of notes couldn't be any more clear.  It ONLY works on the Dell Mini 9.  The Mini 12 has a different chipset (Poulsbo), which is why the standard Ubuntu doesn't quite work.  Dell's version of Ubuntu for the Mini 12 comes with proprietary drivers.  Dell's version is Belmont.  I'm not sure what the Mini 10's use.

I wish people who had the Mini 9 would stop assuming the Mini 12 is the same, only bigger.  It's not.

---

### Post by miami2verona on 2009-04-09
> **notwen said:**
> Use [Unetbootin]("http://unetbootin.sourceforge.net/") to make a USB drive act like a Linux LiveCD.

i tried.....but the pc told me: pen drive without os.....etc.

---

### Post by notwen on 2009-04-09
> **miami2verona said:**
> i tried.....but the pc told me: pen drive without os.....etc.

I'm not sure I understand what you're trying to say.  Could you possibly write down the exact text when you try to boot off a Linux iso on a USB drive made using Unetbootin?  Be sure you have changed the settings in BIOS to boot off of a USB device.

---

### Post by miami2verona on 2009-04-21
> **notwen said:**
> I'm not sure I understand what you're trying to say.  Could you possibly write down the exact text when you try to boot off a Linux iso on a USB drive made using Unetbootin?  Be sure you have changed the settings in BIOS to boot off of a USB device.


with wubi the grapich of ubuntu didn't start

with the install on usb , pc told me : usb without os

with onebootin : pc send me other message of error during the installation.

So, tomorrow i'll try with external cd player to edit the kernell and to downgrade the drivers of vga.

---

### Post by miami2verona on 2009-04-23
release 9.04

installed with wubi.

Problem solved!!!! 


amen:guitar:

---

### Post by zim2dive on 2009-04-23
> **miami2verona said:**
> release 9.04

installed with wubi.

Problem solved!!!! 


amen:guitar:

I didn't think 9.04 contained drivers for our graphics chip (Poulsbo) ?? What resolution are you getting on your Mini 12?

---

### Post by kylecronan on 2009-04-24
It doesn't.  Over 40 pages of info on this topic over at [http://ubuntuforums.org/showthread.php?t=1014534](http://ubuntuforums.org/showthread.php?t=1014534)

---

### Post by zim2dive on 2009-04-24
> **kylecronan said:**
> It doesn't.  Over 40 pages of info on this topic over at [http://ubuntuforums.org/showthread.php?t=1014534](http://ubuntuforums.org/showthread.php?t=1014534)

That was what I thought and why I asked miami2verona to clarify (still I had small hope that we could use something less ancient :( )

---

### Post by miami2verona on 2009-04-24
> **zim2dive said:**
> I didn't think 9.04 contained drivers for our graphics chip (Poulsbo) ?? What resolution are you getting on your Mini 12?


:-(:-( you are in right. Drivers doesn't exist!!!!! (i think....because i'm checking now on internet....)

But ubuntu 9.04 is installed (with usb boot now :P) ....
Ubuntu run and the graphic start now (so good at the moment)...

But drivers doesn't exist so...graphic is not good like a vga with its driver....

So... now i can use ubuntu with very slowly grapich :( ....

The problem with the last ubuntu (8.10) was that it didn't start the graphic.....it loaded nothing

Now..run but with this problem.

What can i do?? Only wait for the drivers?

---

