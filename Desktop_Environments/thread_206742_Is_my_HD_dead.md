---
title: "Is my HD dead?"
date: 2006-06-30
forum: Desktop Environments
---

### Post by xyz on 2006-06-30
Hi-
Fresh install and/or reinstalling no longer work.I've been trying for 2 weeks now. I've encountered just about every error in the book. Please see the link below for the latest. 

[http://www.tldp.org/FAQ/Linux-FAQ/error-messages.html#my-syslog-says-end-request](http://www.tldp.org/FAQ/Linux-FAQ/error-messages.html#my-syslog-says-end-request)
From what I understand, my HD is damaged.  All my data is safe.
What can I do about this?
Thanks for the help.

---

### Post by ahaslam on 2006-06-30
Seeing as you've backed up your data, why not try a boot nuke? This completly destroys all data & partitions on the drive & randomly fills the disk with binary digits, it then repeats the processs over & over. It's said that after running this, the hard disk should be like new. If this doesn't work it may be time for a new drive (if all connections are ok). Find out more & download here: [Darik's Boot and Nuke]("http://dban.sourceforge.net/").
Personally I've only used this (at a mid level) before a fresh install, be aware that it takes hours.

Tony.

PS. It's also included in the  [Ultimate Boot CD]("http://www.ultimatebootcd.com/"), which is a very useful tool.

---

### Post by xyz on 2006-06-30
Thanks Anthony Haslam...I'm at work right now with Windows...
I'll be checking this out and I hope it'll work! Connections seem fine.
I bought my Toshiba Satellite A40 in August 2004..I hope this doesn't mean "old" in computer time!

---

### Post by ahaslam on 2006-06-30
[QUOTE=xyz]Thanks Anthony Haslam...I'm at work right now with Windows...
I'll be checking this out and I hope it'll work! Connections seem fine.
I bought my Toshiba Satellite A40 in August 2004..I hope this doesn't mean "old" in computer time![/QUOTE]
I wouldn't class that as old. I bought my laptop at a similar time and I've not felt the need to upgrade, though Nvidia graphics would be nice for games. 
I hope that a nuke boot helps, it must be quite rare to have a serious hard disc fault at only 2 years old.

---

### Post by hda on 2006-06-30
To check for defective sectors on your hard disk you could boot from a rescue cd and try a non-destructive test with the 'badblocks' command.

---

### Post by xyz on 2006-06-30
[QUOTE=hda]To check for defective sectors on your hard disk you could boot from a rescue cd and try a non-destructive test with the 'badblocks' command.[/QUOTE]
That one sounds good,too!  I'll give it a try as soon as I can and let you guys know how it turned out. Thanks for the help.

---

### Post by xyz on 2006-07-01
[QUOTE=hda]To check for defective sectors on your hard disk you could boot from a rescue cd and try a non-destructive test with the 'badblocks' command.[/QUOTE]


Booted on Knoppix's Live and pressed F3 for booting options and ran:
```
knoppix 2
```
to get a text root prompt and typed in:
```
badblocks /dev/hda3
```
Right now the computer is just spitting out numbers,numbers and more numbers.

Did I type in the correct command to try and fix badblocks?
Should I let it run til it stops all by itself?

...forgot to say that hda3 is where my ext3 Ubuntu is!

---

### Post by hda on 2006-07-01
If badblocks is 'spitting out numbers' than there's certainly something wrong. Check the cables first, maybe replace than. That's the cheapest solution. If the errors are not gone then you have to replace the drive.

Maybe you can still do a backup of the filesystems?

---

### Post by xyz on 2006-07-03
Hi everyone,

Things are rather confused in my head. But let me just say this first

1. I use a Toshiba laptop so cables/connections are fine
2. I have no running OS whatsoever or any Recovery Mode *LIVE CD only*
3. Darik's Boot and Nuke was dowloaded at a friend s house and burned as an iso file on one CD and  extracted RAR and burned to another CD. Neither worked when I tried booting on it. BIOS is set right.
4. I have also downloaded SLAX which allows a copy to RAM using this command at the boot prompt:
```
slax copy2ram
```..to be used only if you have 256MB RAM!
This way I get to use my CD ROM to burn stuff with k3b if need be.

What am I doing wrong? Can I at all do anything to run DBAN having no running OS?
I must admit I am at a total loss. Thanks for the help and time.

---

### Post by xyz on 2006-07-04
Well, sorry for panicking in my last post and asking stupid questions!
Turns out that burning DBAN.iso at my friend's house didn't somehow come out right under Windows. 
Using SLAX's 'copy2ram' option (thus freeing my CD-ROM for use), I burned the iso file with k3b and it worked fine.

So I booted on DBAN's and at the boot prompt, typed in
```
autonuke
``` which, when I left home, had been running for 9 and a half hours and showing
a 68 percentage left to completion. I gather I'm in for another good 20 hours.
...posting back later...good day to you.

---

### Post by 2501 on 2006-07-04
I recently installed my own version of Slax/KillBill edition  on a Sandisk 1G memory stick and my laptop is flying. I have Ubuntu installed in my hd but I haven't touched it in about 2 weeks. 

I am keeping Slax and I can take it anywhere and tell my Window XP users: Can Windows do this? Can Apple do this? :-) Last week I resurrected one of my best friends computers by using Slax. Now he is running Slax too. He saved a lot of money and he is even using it at work.

Slax is awesome and even if we could run Ubuntu in the future the same way as Slax, I would choose Slax because its modular design.

That is my thought.

-2501

---

### Post by xyz on 2006-07-05
This here site is a great place to read about DBAN:
"Darik's Boot and Nuke: A great tool for obliterating your data
**By: Lee A. Spain**"
[http://software.newsforge.com/article.pl?sid=05/09/14/178204](http://software.newsforge.com/article.pl?sid=05/09/14/178204)
If you need to deeply oblitarate HD under Windows, you'll find DBAN's equivalent - *Eraser*- here:
[http://www.heidi.ie/eraser/](http://www.heidi.ie/eraser/)

Approved by the 'highest' authorities such as State Governments, DBAN also:
> In addition to removing personal data, DBAN can also be used to return 
drives to a pristine state for reuse.
Lee A. Spain also says:
> For my test, I chose the DoD Short method. DBAN made three passes 
on my hard drive in an hour and nine minutes....DBAN is not for the impulsive....
Some users report that DBAN took up to 24 hours to erase their data using 
the most rigorous methods.
For more click on the link above.

I've got a DBAN runtime of over 30.5h at time of writing using DoD Short method on a
Toshiba Satellite A40 (laptop)
(R)Intel (R)Celeron - 2.7
40G HD - 512MB RAM
At the prompt, I ran "autonuke" over the entire 40G HD.

Do you think DBAN's pushing my patience? I'm in no hurry...I prefer to let it run til the
weekend if it's my best bet to achieve the best job.:cool:
What do you think?

---

### Post by ahaslam on 2006-07-06
xyz,

I used 6 or 7 passes on a similar spec machine. It took about 6 hours to complete but as long as it's making steady progress, it should be working fine. Maybe it's down to other settings, I set it up manually & didn't use the autonuke command.

I hope that it works for you,

Tony.

---

### Post by xyz on 2006-07-06
Hi Tony,

Yes it is making steady progress and I'm assuming that I could have shorten the thing a bit
if I had run another command than "autonuke". But now that it's on its way, I'm not going
to abort.
This is what it says on the screen:
> Enthropy  : Linux Kernel (urandom)
PRNG  : Mersenne Twister (mt 19937 ar-cok)
Method  : DoD Short
Verify  : Last Pass
Rounds  : 1
Runtime  : 54h.....
CPU Time  : 1%
Load Averages  : 3.00 3.00 2.93
Throughput  : 9405 B/s (this digit's been higher but, from what I read, it's normal that
it slows down a bit as it gets closer to the core of the HD)
Errors  :0
(IDE  0,0,0, -,-) TOSHIBA MK4025GAS
[00,92%, round 1 of 1, pass 1 of 3] [writing] [9402 B/s]

Lee A. says 3 passes should be enough! The following sounds, to me, like a logical
way of thinking but may not be a 'computer way' of thinking: I'm hoping 'Pass 1' is 
doing the heavy work...so 'Pass 2 and 3' will not take as much time!!

At the end of the day, the point is to get a clean slate and...avoid purchasing a new HD!
Money's tight.

Tony, thanks a lot for keeping an eye on my small pbm!
Bye for now.

Terry

---

### Post by ahaslam on 2006-07-06
My CPU was worryingly running between 99-114%, the cooling fan was on constantly for over 6 hours! I was half expecting my laptop to melt!

It took the same amount of time to complete each pass, as each pass is doing the same operation (writing random digits), it makes sense.

As your CPU is taking it easy and your computer wasn't working anyway, you may as well stick to your guns and continue. I also wouldn't be able to suggest other settings without using it again myself.

I suppose we'll have to wail until next week to find out if it's worked (fingers crossed). ;) 


Tony.

---

### Post by xyz on 2006-07-07
A quick report:

Pass 1 completed in 3 days (72h).
Now at the 80th hour, what I'm assuming to be Pass 2, shows a progress of 1.04% at a 7152 B/s rate and 0 Errors.
I really hope Pass 2 measures progress differently than Pass 1 because if it has to reach 100% to be complete, I just can't imagine how long it'll take!!

CPU's fine at 1%.

---

### Post by xyz on 2006-07-08
Between the 72nd hour (start of pass 2) and now...the 106th hour, there's been a steady progress of 1,17%!!!
I wish I knew why, during pass 1, % number moved up 1% at a time and now, 0,01% at a time. I also wish I knew whether this is good news or not. Also, the B/s rate's been steadily going down...6109 at this time. I may not have searched right but I find it difficult to find information about those %!!CPU rate's the same.
Anybody has any clues about...anything at all?
Thank you.

---

### Post by ahaslam on 2006-07-08
It is taking way too long. I've never heard of it taking over a day.
CPU @ 1% is nromal. I don't know why mine went mad.
Maybe the speed is relative to the condition of the drive?

Have you looked on ebay for a cheap drive? Seccond hand (but tested ok) ones go for less than £30.

There's no guarantee that the nuke boot will work. But if you've got the patience (& don't need the computer for a while), you may as well continue.

---

### Post by xyz on 2006-07-08
I sent an email to the creator of DBaN. Hopefully, he can enlighten us::) 
> Hi,
I'm emailing you because I don't know whom to turn to anymore. I'm a noob at DBaN,
but a noob willing to learn. If you have a little time, please take a quick 
here: [http://www.ubuntuforums.org/showthread.php?t=206742](http://www.ubuntuforums.org/showthread.php?t=206742)
I've briefly exposed my pbm on the ubuntuforums site. However, I'll give
you the short end of my story.
According to the kind of errors I got while booting my laptop Toshiba Satellite A40
(R)Intel(R)Celeron 2.7 / 512RAM HD:40G, I came to the conclusion that the HD
was damaged. I enquired on the ubuntuforums site and was kindly directed to
DBaN.
I booted on DBaN's latest version and typed "autonuke" at the prompt. Being no expert at all,
I just let it go at that.Pass 1 came to an end in 72h showing % progress in a 'normal' way...
I mean from 10%, it then went to 11% and so on. Right now DBaN's been running, in what I assume 
to be pass 2 out of 3, for 38 MORE hours. One of the weird things about it is that it no longer
shows % progress as it did during pass 1. It goes, f.inst., from 1.01% to 1.02% and so on.
At the moment, it's at 1.20% and is taking a worrying long time to move.
I'm willing to go to "the end of this experience" but I just can't imagine how long it would
take if the % has to reach 100 in order to complete pass 2!
Thanks for your time,

Terry

---

### Post by xyz on 2006-07-08
Hi everyone,
Here is Darik Horn's answer:
> When DBAN slows down like this, a DMA fault probably happened.

Run the vendor hardware diagnostic on this disk. Past that, replace it.
I'm not home right now but can anyone tell me if it's safe to simply eject DBaN from my CD-ROM without risking further damage?
Thank you.

---

### Post by ahaslam on 2006-07-08
> **xyz said:**
> Hi everyone,
Here is Darik Horn's answer:

I'm not home right now but can anyone tell me if it's safe to simply eject DBaN from my CD-ROM without risking further damage?
Thank you.

You can eject the disc safely, as the program now resides in memory & should couninue. If you turn off the machine while it's writing to the disk, there may be a risk of further damage, but I doubt it would have much impact upon your drive (in it's current state).

Tony.

PS. I've had to turn the power off a couple of times while the hard disk was still writing (system lockups) and I have no bad blocks. I think that the risk is minimal.

---

### Post by xyz on 2006-07-08
Thanks Tony! I still haven't lost all hopes. I'll try and run the vendor hardware diagnostic on this disk without turning off my computer and see what happens.
I guess after that, I'll be able to power off my box with no further risk of damage...
I'll keep you informed...til then,;) 

Terry

---

### Post by xyz on 2006-07-09
Well, I thought that > running the vendor hardware diagnostic on this disk would be a plain and simple task! I could not find it on the disk,could not figure out how to do it.
I powered off and rebooted on DBaN-s and looked for it, for a way to do it to no avail.
I now booted on Slax live CD to be able to post here. Prior to that, I used Knoppix Live to check out my dev/hda with qtparted; it is empty,unformatable and unpartitionable. Maybe I should try to stick in Dapper-s Install and make an attempt at creating a partition from scratch. It may just be my lucky day!
I think I need a short break on this.:oops:  You all have a good Sunday.

---

### Post by ahaslam on 2006-07-09
> **xyz said:**
> Well, I thought that  would be a plain and simple task! I could not find it on the disk,could not figure out how to do it.
I powered off and rebooted on DBaN-s and looked for it, for a way to do it to no avail.

There's a few hard disk diagnostic tools on the [Ultimate Boot CD]("http://www.ultimatebootcd.com/").
Check it out.

Tony.

---

### Post by xyz on 2006-07-11
Thanks to *ismael* who posted similar pbms on Sourceforge.
I was lead to downloading Digital_Dolly, a 41MB zip file containing "cdrom.iso", a
133 MB file...and that 133MB became my main problem as far as being able to burn
the image under SLAX.
Dolly's here: [http://www.download.com/3000-2248-10220909.html](http://www.download.com/3000-2248-10220909.html)

What was I saying...yes, SLAX (copied-to-RAM) is great but could not handle burning
that 'heavy' .iso file. The message "Disk is full" kept on coming up. SLAX's not heavy
at all...just too heavy for my box and the goal to be achieved.

So I began looking for a lighter bootable distro "Puppy Linux in my case" so as to be able
to burn Dolly's (cdrom.iso) image onto a CD. I just love CD-RW! That worked fine.
Then I simply booted on Dolly (I chose the 'wipe' option) and I can now SEE errors being fixed on the screen. The word -SUCCESS-
appears as errors get fixed one at a time. I'm keeping my fingers and toes crossed!

I hope Dolly will run to a successful end.
Keeping you informed...

A definition:

> - Dolly, also called Digital Dolly, is a program that can quickly clone (copy) drives to drives, drives to files, files to drives, or files to files. It is similar to the Symantec product known as Ghost. Dolly can also clone entire disk partitions in block-wise fashion. Dolly can be used to clone the operating system of a computer to numerous others.

When Dolly is used in a network, the server (or other designated computer called the master) sends data to one or more client machines. The clients store the data on their hard drives. A server can clone data to all the clients in a network. Alternatively, clients can send the data to other clients, and the process can continue until the data has been cloned to as many machines as desired. Dolly can be used to back up or restore hard drive partitions, as well as to back up, restore, or archive data. Dolly can be run from a bootable CD-ROM in the event of corruption of the original data on the hard drive.

Dolly is named for a famous sheep of the same name, the first mammal to be cloned from an adult cell. Dolly the sheep was born in 1996 at the Roslin Institute in Scotland and died just six years later. Her short life-span, possibly a result of the process, reinvigorated debate into the ethics of cloning. 

---

### Post by xyz on 2006-07-13
Dolly's still running, awful slow but fixing things;that is what it says on the scrren.
A friend lent me his (very) old Dell Latitude for (very) basic work in the meantime.

---

### Post by xyz on 2006-07-15
Some people have no luck! Like Dolly wasn't running slow enough,
I got a ONE-AND-A-HALF second power shortage! And, yes I did curse
the whole world! Anyway, I rebooted Dolly.
I've learned a couple of things in the meantime:

- I've got approx. 7500 ERRORS in need of fixing!! which, I'm assuming
explains why Dolly is "slow"

- Dolly is fixing errors at a rate of approx. 30 per 5 minutes


For those of you interested in this, here is a sample of what Dolly
displays on my screen:

> hda: write_intr: error1 : nr_Sectors=1, stat = 0x51
hda : write_intr : status=0x51 {DriveReady SeekCompleteError}
hda : write_intr : error = 0x04 {DriveStatusError}
end_request : I / O error, dev 03:00 (hda) , sector 882015
ide0 : reset : success

Any comments?

---

### Post by ahaslam on 2006-07-15
> **xyz said:**
> Any comments?

Only that I wish you the best of luck with you ordeal. ;) 

How p1553d are you going to be if it doesn't work out? :-# 


Tony.

---

### Post by xyz on 2006-07-15
Yes it is an ordeal, a saga...maybe I'll write a book or get in touch with the Guiness Book...or "Dolly Parton!"](*,) :) 

Sorry I don't know that expression but I can "feel" what you mean by that:
```
How p1553d are you going to be if it doesn't work out?
```
Thanks for the reply, Tony...I feel less stranded out there on Dolly's Island!

---

### Post by xyz on 2006-07-24
Hi-
Is there any way of finding out how many "Sectors" a 40G HD has? Keeping in mind I've got no working OS!
Correcting Sector 74746565 right now, not following a chronological order. It seems to 'fix' things moving from in between 1 and 2000000;3 to 400000 and now 7...... (always a 7-digit number)
Thanks.

---

### Post by xyz on 2006-07-24
I found somebody else's fdisk -l command output for a 40g HD on the net:


> Disk /dev/hdc: 40.0 GB, 40027029504 bytes
255 heads, **63 sectors**/track, 4866 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes

Right now Dolly put this out: "sector 7365296"
Anybody knows how this compares to 63 sectors? What it means as far
as how many sectors have so far been checked?

I think I'm gonna end up in the 'Psycho Sector' of some ward somewhere...

---

### Post by ahaslam on 2006-07-25
> **xyz said:**
> I think I'm gonna end up in the 'Psycho Sector' of some ward somewhere...
I'd get another drive while you can still venture outside. ;)

Tony.

---

### Post by xyz on 2006-07-25
Even if my cause is desparate and nearing psychological disorder:wink: ,
the following may help others run diagnostic tools to check what's
left of their HD.

I discovered that my 'looney' 40 G HD is made of 78140160 that is, 10x
more that stated in my previous post. Booted on Dapper "Live" and formatted
/dev/hda1 as FAT 32 and checked on HD infos. Remember I have no operational
OS. My HD has only "errors" on it..haha..

Then I found some diagnostic HD tools here <**supposed** to work on whatever HD brand>
[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)
'DFT diagnostic tool Bootable CD  for Linux is located at the bottom of the page'

I ran it and returned this error code
> Disposition Code = 0x72 from what I understood, I *think* 
no errors = 0x00. That is where you want to be...unlike me.
You can find a guide to DFT here  [http://www.hgst.com/downloads/dft32_user-guide.pdf](http://www.hgst.com/downloads/dft32_user-guide.pdf)
and on Page 28...a list of what various error codes mean. damn it that is always nice
to know...
OK this is for Hitachi HD but the guide is useful for all. I may add that running
DFT revealed the 0x72 SMART error, advising to contact Toshiba. If DFT is no good on 
your HD brand, it will tell to search for an appropriate diag tool.


Anyways..my HD seems dead...[b]I will go and spread the ashes of this 23 months old HD 
over Japan...[/b]:mad: 

Brian Auyoung on forum1.itrc.hp.com/service said

> There's really not much that can be done - the drive definitely has a problem. The error that has been corrected is likely the Drive Fitness Test tool moving the data on a bad sector and marking it off. I'd recommend running the DFT weekly or bi-weekly to determine if there are any more errors. If the number errors increases with every scan, then it would be wise to replace the drive.

I might try and dig up a Toshiba diag tool later...

---

### Post by xyz on 2006-08-01
Well, my HD is definitely fried as most of you knew long ago!

However, I'm glad I tried for so long to fix it because, in the process, I learned an awful lot of things.
I discovered and learned how to use DBaN, Digital Dolly, UBCD,DFT and much more. Thanks again to Tony who led me that way.

I also understand my box much better now and I would probably not have found all of this out if I had had enough money to go out and buy a new HD right away.

I have been working around this HD pbm using Slax, Puppy Linux, Damn Small Linux, Deli ...learned an awful lot there too. The copy to RAM thingy is really great...among other things.

I read somewhere *can no longer get my hands on that site!* that it is possible to add -boot from USB HD option- to BIOS if, like me, that booting option isn't in your BIOS. I have an external HD and I might try that if I can find that site again.
Also there's a great thread right here on ubuntuforums explaining how to install on external drives provided you can boot from it.

Good day to all!

---

### Post by linuxgrrl on 2006-08-02
> **Anthony Haslam said:**
> Seeing as you've backed up your data, why not try a boot nuke? This completly destroys all data & partitions on the drive & randomly fills the disk with binary digits, it then repeats the processs over & over. It's said that after running this, the hard disk should be like new. If this doesn't work it may be time for a new drive (if all connections are ok). Find out more & download here: [Darik's Boot and Nuke]("http://dban.sourceforge.net/").
Personally I've only used this (at a mid level) before a fresh install, be aware that it takes hours.


I second the recommendation for Boot and Nuke. I had a Maxtor drive go bad last week after 1 year of use.  The Maxtor diagnostics pronouned it dead and gave me a "return code", but I had bought the drive on EBay so figured why waste my time trying to return it.  After Boot Nuking, the disk now works fine and the Maxtor utilities report that it is clean.  NB, running Maxtor's "low level format" did NOT work, only Boot Nuke did.  Thanks Tony for saving me $$!!:D

---

### Post by ahaslam on 2006-08-02
> **linuxgrrl said:**
> I second the recommendation for Boot and Nuke. I had a Maxtor drive go bad last week after 1 year of use.  The Maxtor diagnostics pronouned it dead and gave me a "return code", but I had bought the drive on EBay so figured why waste my time trying to return it.  After Boot Nuking, the disk now works fine and the Maxtor utilities report that it is clean.  NB, running Maxtor's "low level format" did NOT work, only Boot Nuke did.  Thanks Tony for saving me $$!!:D

A pleasure   :wink: 

Tony

---

### Post by ahaslam on 2006-08-02
> **xyz said:**
> Well, my HD is definitely fried as most of you knew long ago!

However, I'm glad I tried for so long to fix it because, in the process, I learned an awful lot of things.
I discovered and learned how to use DBaN, Digital Dolly, UBCD,DFT and much more. Thanks again to Tony who led me that way.

I also understand my box much better now and I would probably not have found all of this out if I had had enough money to go out and buy a new HD right away.

I have been working around this HD pbm using Slax, Puppy Linux, Damn Small Linux, Deli ...learned an awful lot there too. The copy to RAM thingy is really great...among other things.

I read somewhere *can no longer get my hands on that site!* that it is possible to add -boot from USB HD option- to BIOS if, like me, that booting option isn't in your BIOS. I have an external HD and I might try that if I can find that site again.
Also there's a great thread right here on ubuntuforums explaining how to install on external drives provided you can boot from it.

Good day to all!

I'm interested int the 'copy to RAM' thing, which distro utilised this & how's it done? It sounds very useful for system recovery when you only have the one DVD drive.

The Ultimate Boot CD that I mentioned earlier in this thread may well have a utility to boot from USB, I've used it to boot a partition when I borked GRUB.

Tony.

---

### Post by xyz on 2006-08-03
linuxgrrl

I did try Nuke...I "nuked" my HD for over a week's time but it never ended.
I used the default method DoD Short (3 passes) but never saw the end of it
so I quit it. See previous posts about that. I'm glad your HD recovered though!

Tony
[http://www.slax.org/](http://www.slax.org/)
I've tried several distros. One of them is SLAX.Booting on the CD, simply type
"copy2ram" and wait. After a while, you'll need to log in as "root", password is 
"toor". Then just type "startx". You'll be able to take the SLAX CD out and use
your CD-ROM as usual. I've got an external HD, as you know, and use it to store
stuff. KNOPPIX can also be copied to RAM
 

Minimum system requirements for Knoppix:
> #  Intel-compatible CPU (i486 or later),
# 32 MB of RAM for text mode, at least 96 MB for graphics mode with KDE (at least 128 MB of RAM is recommended to use the various office products),
# bootable CD-ROM drive, or a boot floppy and standard CD-ROM (IDE/ATAPI or SCSI),
# standard SVGA-compatible graphics card,
# serial or PS/2 standard mouse or IMPS/2-compatible USB-mouse.

PUPPY Linux's great, too:
[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Puppy-Linux-1996.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Puppy-Linux-1996.shtml)

Also Damn Small Linux (DSL)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) a 50MB mini desktop oriented Linux distribution.

As a musician, I appriciate dyne:bolic a multimedia-ortiented distro.
> You can employ this operating system without the need to install anything, and if you want to run it from harddisk you just need to copy a directory: the easiest installation ever seen!
[http://dynebolic.org/](http://dynebolic.org/)
The options "docking" and "nesting" are also quite interesting and very practical.
Check them out: [http://dynebolic.org/manual/](http://dynebolic.org/manual/)

Also:> Install GNU/Linux without any CD, floppy, USB-key, nor any other removable media

[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html) 
I haven't looked much into that one yet.

Let me know how it goes!
I realize there are more distros usable in this manner...those are just the ones I've most looked into.

---

### Post by ahaslam on 2006-08-04
[I][COLOR="DimGray"]"Tony
[http://www.slax.org/](http://www.slax.org/)
I've tried several distros. One of them is SLAX.Booting on the CD, simply type
"copy2ram" and wait. After a while, you'll need to log in as "root", password is
"toor". Then just type "startx". You'll be able to take the SLAX CD out and use
your CD-ROM as usual. I've got an external HD, as you know, and use it to store
stuff. KNOPPIX can also be copied to RAM"[/COLOR][/I]

Thanks for the info. 

I downloaded the popcorn edition with the idea of putting it on my 128mb flash stick. I couldn't install a bootloader on the stick, so tried as a cd. Quite disappointed, no cd burning app & didn't offer copy to ram :(

I'll try out regular SLAX, maybe with a couple of extra modules ;)

Thanks again,

Tony.

---

### Post by xyz on 2006-08-05
Hi Tony,

Strange...I downloaded SLAX Killbill -the one with the yellow background and the sword- and typed  slax copy2ram  at the boot prompt. I made a mistake in my previous post when I said to type simply  copy2ram.And I have not tried putting it on a stick.
This one has k3b among other things.Of course, it does remain a smallish distro!! See you.

---

