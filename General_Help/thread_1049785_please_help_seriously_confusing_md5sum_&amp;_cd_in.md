---
title: "please help: seriously confusing md5sum &amp; cd integrity check problems"
date: 2009-01-24
forum: General Help
---

### Post by jnewm on 2009-01-24
*** SOLVED (see last page), will mark solved once forums lets me ***

*** UPDATE: I should mentioned 2 things: 1) I just tried OpenSUSE, and the exact same thing happened--I checked the md5sum of the opensuse .iso file in windows, and it was all good, but then when I did the "media check" on the live CD in linux, OpenSUSE said the md5sum of the CD was wrong (I then tried the live CD in another computer, and the md5sum was again all good); 2) I even cleared Ubuntu from my desktop and entirely removed all non-Windows partitions, just in case the md5sum problem was a lingering error from previous installs, but no dice.  This is so crazy!  I would think it was a memory or hardware problem, but I can't come up with a reason why Windows runs smoothly and checks md5sums just fine.  And I so want to use Ubuntu instead of Windows that I'd probably even buy a new computer just to solve this, but it seems so strange to have do so!... 

Hi all,

For the last couple years, I have had some very confusing problems with md5sum & cd integrity checks on my desktop computer.  And I concerned these problems are related to random and recurring glitches that have plagued my use of ubuntu or kubuntu on this computer.  (PS I have extensively searched the forums and internet generally for any similar experiences, with no luck).

Basically, here is the story:  When I first installed Feisty, I checked the md5sum for the .iso file in Windows, and it matched.  But when I checked the live CD integrity, it said "1 error found" (or something like that, it's been a while).  I tried the live CD in two other computers, however, and no errors were found.  So, I figured what the hell, and installed Feisty on my desktop anyway.  Afterwards, Feisty was always a bit buggier on my desktop than my laptops, which I thought uncommon, but I figured again oh well.  

Then, when Gutsy came out, I downloaded the .iso in Feisty.  But when I ran md5sum, I kept getting a different string each time (none of which matched the hash provided).  I rebooted into Windows, however, and the md5sum check ran perfectly!  So, again, I figured what the hell, and burned the CD image and tried the CD integrity check.  Again, always "1 error found" on the desktop, but no errors on the other computers.  So, I installed Gutsy anyway, but again seemed to have more bugs than on my other computers.

Next, thinking maybe these strange problems were causing the bugs, I tried downloading Kubuntu 8.04 & Ubuntu Server 8.10.  Exact same problem: md5sum checks in Ubuntu return different strings everytime, but Windows md5sum checks work fine and match the proper hashes.  And when I try the CD integrity check on my desktop, the Kubuntu live CD has 1 error, but my other two computers say the CD is fine.

Lastly, I got a tiny bit more information from the Ubuntu 8.10 CD check, which instead of just saying 1 error, actually stops at what seems like a random point during each check to tell me that a particular file (a new file each time I run the check) has failed the md5sum verification test.  Again, the CD checks out fine on my other computers.

So, all this makes me think that the CD check and md5sum check may have been related all along.  And that for some crazy reason my computer just can't check md5sums properly in Linux (or Ubuntu at any rate).  Which in and of itself wouldn't be a big problem, but it does make me wonder what else isn't working right between my desktop and Ubuntu, and if this problem might be related to the more extensive bugs I've noticed using Ubuntu on this computer.  (PS Pretty basic computer, Gateway P4...).

So, please anyone, I could really use some help.  I'd love to go back to feeling safe using Ubuntu.  But I'm now feeling like giving up.

Thanks!
Jesse

---

### Post by dcstar on 2009-01-25
> **jnewm said:**
> 
.........
So, please anyone, I could really use some help.  I'd love to go back to feeling safe using Ubuntu.  But I'm now feeling like giving up.


So you basically have a situation where one set of hardware always reports errors, and if Linux is installed on that same set of hardware, it has ongoing problems.

Get new hardware.

---

### Post by jnewm on 2009-01-25
> **dcstar said:**
> So you basically have a situation where one set of hardware always reports errors, and if Linux is installed on that same set of hardware, it has ongoing problems.

Get new hardware.
Huh.  Not the most explanatory reply I've received here.  

If you're saying that you don't think this is a solvable problem, or that it would be really really hard to solve, then I understand your conclusion that I should just get new hardware...  And fair enough.  But, in my limited experience at any rate, it seems like people run into weird things like this all the time that they are able to solve.  Of course, I have no clue which is which.  So, I totally defer if someone (like you) with expertise says "sorry, this isn't solvable or isn't worth fixing."  (And it's especially nice to get a bit of a hint why, for learning's sake).  But, I'm reluctant--on a financial and principled level--to get new hardware without any such, even brief, explanation.

But, in all honesty, thanks for at least responding...  If I don't hear back from you, I'll assume you meant to add "...because there ain't nothing you can do to solve this or it would seriously not be worth the trouble."

Jesse

---

### Post by mb_webguy on 2009-01-25
Actually, what he said was a sensible answer, though he was admittedly being a bit snarky about it.

From your description, you're having this problem on one specific computer, and not on other computers.  That, to me, indicates that it is a hardware issue rather than the software.  Windows and Linux access hardware in slightly different ways, so this could account for why you don't have the problem on this particular system under Windows.  If it were just the LiveCD integrity checks, I'd say that it was due to a minor incompatibility issue with that particular make of drive, but I don't know how to explain the md5sum problem.

If the md5sum or integrity check passes on one computer, however, the ISO or CD is good.  It's not going to be good on one computer and not on another unless you've damaged it somehow between checks.

---

### Post by -kg- on 2009-01-25
My suggestion would be to download using a bittorrent client.  The md5 checksums are done in the process, so you can be very sure that what you download is good.  The [Ubuntu Download Page]("http://www.ubuntu.com/getubuntu/downloadmirrors#bt") has a list of official torrent sites that you can use.

> If you're saying that you don't think this is a solvable problem, or that it would be really really hard to solve, then I understand your conclusion that I should just get new hardware... And fair enough. But, in my limited experience at any rate, it seems like people run into weird things like this all the time that they are able to solve. Of course, I have no clue which is which. So, I totally defer if someone (like you) with expertise says "sorry, this isn't solvable or isn't worth fixing." (And it's especially nice to get a bit of a hint why, for learning's sake). But, I'm reluctant--on a financial and principled level--to get new hardware without any such, even brief, explanation.

The thing that gave dcstar the idea that it might be the hardware was your statement:

> Basically, here is the story: When I first installed Feisty, I checked the md5sum for the .iso file in Windows, and it matched. But when I checked the live CD integrity, it said "1 error found" (or something like that, it's been a while). **I tried the live CD in two other computers, however, and no errors were found.**

Troubleshooting 101:

It shows an integrity error on one computer, but doesn't show any errors on two other computers.  That would lead me to believe that it isn't a bad burn on the disk...it is more likely that there is a hardware problem on the first computer.

Without knowing what hardware you have installed on the original computer, or it's age, or how hard of use it has seen, there is no way to know what might be causing the problem.  Have you tried installing on any of the other computers to see if you would have problems with those installs?

It could literally be anything.  For example, I tried installing MS FS-X on my desktop a while back.  I had already installed it on my laptop, and it took me around 2-3 hours to install both DVDs.  I had a relatively new DVD burner on the desktop (only a couple or three years old), but when I started to install I kept getting disk read errors and re-reads.  And this was a brand new disk.

I finally gave up after around 7 - 8 hours (and the first DVD hadn't even installed) and bought a brand new DVD burner and installed it.  2 - 3 hours later FS-X was installed and running.  The old DVD burner was bad.

But like I said, it could be anything.  You might have a memory stick going out.  Maybe your hard drive is getting corrupt or ready to go.  Without knowing more information there is no way to tell.

Yes, some people's answer is to "get new hardware" or "clean re-install" to correct problems.  It's just that you have some troubleshooting to do before the answer becomes apparent.  There is *some* reason that this is happening, but we're going to have to have more information before we can even *begin* to figure this out.

Anyway, if you have used this disk to successfully install Ubuntu on your other computers, then the checksum and disk integrity isn't the problem.  It *has* to be that particular computer.  We need to find out what that is.  What is the total specs on the computer; i.e., how much RAM, what size hard drive, CD Drive, how old is it, etc.  You might even need to flash your BIOS...no way of knowing.

---

### Post by dcstar on 2009-01-25
> **mb_webguy said:**
> Actually, what he said was a sensible answer, though he was admittedly being a bit snarky about it.
.........

There is nothing "snarky" about it. That was a concise summation of the whole problem, it just wasn't wrapped up in the wasteful fluff that too many people seem to expect these days. If one common component is always at the root of problems, then it is most likely the problem.

People are free to choose to spend their time trying to get a particular set of hardware to work with various Linux distros, but as anyone can see in posts in these forums (and many other Linux forums) it can be a very time-consuming and frustrating process that only those well versed in this field seem to achieve successfully.

The only real solution sometimes is to replace every component in the machine until things work correctly - hence "Get new hardware".

---

### Post by mb_webguy on 2009-01-25
Actually, it *was* a little bit snarky.  Of course, there's not necessarily anything *wrong* with snarky.  I *like* snarky. ;)  But your answer was short (or "concise") and mildly sarcastic, and, well... that's snarky.

"Doctor, my neck hurts when I turn my head to the left."
"So don't turn your head to the left..."

That was snarky.  As was "Get new hardware".  But it was also a reasonable answer.

---

### Post by jnewm on 2009-01-25
Genuine thanks to dcstar, and now to mb_webguy and -kg- as well for elaborating a bit,

PS -kg- notwithstanding the below, do you think getting my system info. really might help figure this out?  It strikes me that you all think it's a long shot, so I don't want to waste your time.  But if I'm wrong let me know and I'll post it first thing tomorrow (I'm running memtest86 all night just in case).  Thanks!

I totally get that it's the hardware and that dcstar gave me a sensible answer.  I was just looking to see if he or someone else would elaborate a bit, since--even when it is a hardware compatibility/failure issue--sometimes someone on the forums still has a brilliant solution.  Or, other times, you hear from someone who had the same problem, and knows what's causing it, or tried a million things, and can tell you not to waste your time.  Especially when it's something like this where, by and large the OS is functioning (albeit a bit buggily), but there's one really specific error (md5sum checks). For instance, I thought it entirely possible someone would say: oh yeah, some processors aren't compatible w/md5sum checks, but don't worry, the rest of linux runs fine (okay, maybe that's a little farfetched, but it's late here).

So, with that said, so far, it looks like everyone has the same impression: I'm SoL :).  And that's okay.  I definitely get that sometimes you just need new hardware.  I'll probably give it another week or so to see if someone recognizes my problem or has a particular insight.  And if not, I will move on.

Thank you again to all 3 of you.  And I guess I did think dcstar was a bit abrupt in his first response (I won't debate whether it was snarky) ;).  But I truly meant my initial thank you and certainly wasn't offended or anything.  I mean, everyone here is just helping to help, and a quick response is still going out of your way.  So really, thanks again.

Jesse

---

### Post by jnewm on 2009-01-25
PS Just one quick hardware-based Q, if any of you know: could a dying hard drive explain the live CD check failures?  I'm sorry, I just don't know jack about computer mechanics, and I'm not sure if at that stage in the boot process the hard-drive is at all involved.  Thanks again

---

### Post by mb_webguy on 2009-01-25
> **jnewm said:**
> PS Just one quick hardware-based Q, if any of you know: could a dying hard drive explain the live CD check failures?  I'm sorry, I just don't know jack about computer mechanics, and I'm not sure if at that stage in the boot process the hard-drive is at all involved.  Thanks again

No, but a bad disc drive or one with which Ubuntu has minor incompatibilities certainly could.  If it works fine under Windows, it's probably not the former, but it could still be the latter.

---

### Post by -kg- on 2009-01-25
> **jnewm said:**
> PS Just one quick hardware-based Q, if any of you know: could a dying hard drive explain the live CD check failures?  I'm sorry, I just don't know jack about computer mechanics, and I'm not sure if at that stage in the boot process the hard-drive is at all involved.  Thanks again

It's possible.  And it could be a host of other things.

> PS -kg- notwithstanding the below, do you think getting my system info. really might help figure this out? It strikes me that you all think it's a long shot, so I don't want to waste your time. But if I'm wrong let me know and I'll post it first thing tomorrow (I'm running memtest86 all night just in case). Thanks!


Possibly, and let me tell you...if I think something is a waste of my time, I will bypass it and not even answer it.  No, there is every possibility that this is caused by something very simple and easy to diagnose, but without the specific information we need, it *is* impossible.

Don't doubt the skills of some of the people on this forum!  While I'm not a flaming expert on Linux (actually, I'm probably as much a newbie as you are), I have been into the hardware aspect for many years (Ham radio operator since 1964; Ground Radio Repairman in the Air Force since 1974; into computers since 1982; and have built my own computers since around 1999) and have some experience in electronics troubleshooting.  Many here have my experience and more.

We ***are*** here to try and help...and I expect a little help with my problems (which I have gotten...and with some of which no one could help).  When we ask for some information or other, we need that information in order to help.

People don't realize...if we could be there; if we could come to your house, take over your keyboard, and do what we know to do, it would be (to us) a simple matter and we very possibly could have the computer up and running (or at least diagnosed) quickly.  When we're doing this at a distance, and with no direct access to the computer in question and a stranger who doesn't know what *we're* looking for, it is quite a bit more difficult.

I run into this all the time; when I *am* there, I am running through menus and options, and my friends tell me to slow down because they can't follow what I'm doing.  I know what I'm looking for...my friends don't!

Give us a little chance.  We might find something absolutely simple and you might be up and running in no time.

---

### Post by jnewm on 2009-01-25
*Ooops.  This was actually meant to be a response to mb_webguy's post.  So thank you to mb_webguy.  I accidentally missed your most recent post -kg-.  Which I'll read now.

Thanks again -kg-.  I tried one other thing: I used Unetbootin w/Kubuntu, and ran the CD check (with no CD in the drive of course, it just thought the CD was on the hard-drive I assume).  And it again found one error (specifically: "errors found in 1 files!").  So, I take it that rules out the CD drive?  And if it's not the hard drive or CD drive (and memcheck went okay), what might it be?
PS I found a post where someone seemed to be having a similar problem, so I'm going to reply and see if they ever figured anything out!
PPS Borrowing from that other post, here are my system specs via lshw:

---

### Post by jnewm on 2009-01-25
Alright, now a big thanks to -kg-.  And don't worry, I have never been anything short of amazed and what the people in these forums know and can solve :).

And seriously, thanks for helping look into this...  So, what info. can I get you?  I just uploaded a lshw output text file in my last post, which I didn't know existed until I read that other post (and which I just realized I forgot to link to, it's [http://ubuntuforums.org/showthread.php?t=845315](http://ubuntuforums.org/showthread.php?t=845315)).  

Is there anything else that would help?  I'm going to bed now, but I'll check the thread again bright and early tomorrow (alright, not that bright and early, but as soon as I'm up) ;).

Thanks again so much!
Jesse

---

### Post by jnewm on 2009-01-25
Hi -kg-, and anyone else reading this,

So, quick update with hopefully good news: I somehow managed, with Unetbootin, to get Kubuntu installed on my external hard drive.  (My OG plan was to try to run the cd check on the external drive, but for some reason I couldn't get to that option).  And, when I run md5sum in Kubuntu (checking the ubuntu .iso file), it works!!!  Yay!!!

And, just to confirm.  I then immediately rebooted, went through Unetbootin again, but this time installed the same exact Kubuntu .iso to my internal hard drive.  Went to try md5sum, and it does _not_ work!

So, given that (1) the CD check with a real CD always finds an error (presumably an md5sum error), (2) the CD check without a CD with the live CD running on my internal hard-drive always finds an error, and (3) md5sum itself fails (returning inconsistent results) when running Kubuntu from my internal hard-drive, but not when running from my external hard drive...  My internal hard-drive is the problem, right?  Because running Kubuntu from the external hard drive has to use the computer's internal motherboard, video card, etc.  The only difference is the drive itself, right?

Anyway, barring any advice to the contrary from you, -kg-, or anyone else, I'm just gonna get a new internal hard drive.  And that's not so bad: relatively cheap, and something I can hopefully handle installing :).

Thanks again to all!
Jesse

---

### Post by dcstar on 2009-01-25
> **jnewm said:**
> 
.........
So, given that (1) the CD check with a real CD always finds an error (presumably an md5sum error), (2) the CD check without a CD with the live CD running on my internal hard-drive always finds an error, and (3) md5sum itself fails (returning inconsistent results) when running Kubuntu from my internal hard-drive, but not when running from my external hard drive...  My internal hard-drive is the problem, right?  Because running Kubuntu from the external hard drive has to use the computer's internal motherboard, video card, etc.  The only difference is the drive itself, right?
........

Or the hard drive/CD interface on the motherboard.

After reading your system specs, I would suggest making sure that the internal drive and CD are put on separate IDE channels (if not already), and their jumper setting both set to "Master" devices - do not assume they are set correctly at the moment!

---

### Post by jnewm on 2009-01-25
*** UPDATE (ignore below): I opened the computer, saw that the hard drive was set to master and the cd to slave.  I changed CD to master.  The live CD check still returned 1 error.  I couldn't figure out how to tell if the drives where on separate IDE channels though...  I saw that the hard drive was set to 0, I think.  But there was no option for the CD.  Physically, they were plugged in to two different slots, and in Windows, device manager shows the hard drive as being at location 0, and the CD at location 1.  Does that mean they are on separate IDE channels? ***

Thanks dcstar, I was about to go get a new hard drive, but I'll follow up on this first.

So, just to make sure I have this right:  To check whether the CD and hard drive are on separate IDE channels and both set to master, I have to physically open the computer, right?  Is it then easy to tell if the drives are on separate IDE channels?  Whereas, with master vs. slave, I assume I have to try to find the product manuals online? (I don't have any manuals for the computer).

Thanks again,
Jesse

---

### Post by -kg- on 2009-01-25
> **jnewm said:**
> *** UPDATE (ignore below): I opened the computer, saw that the hard drive was set to master and the cd to slave.  I changed CD to master.  The live CD check still returned 1 error.  I couldn't figure out how to tell if the drives where on separate IDE channels though...  I saw that the hard drive was set to 0, I think.  But there was no option for the CD.  Physically, they were plugged in to two different slots, and in Windows, device manager shows the hard drive as being at location 0, and the CD at location 1.  Does that mean they are on separate IDE channels? ***

Thanks dcstar, I was about to go get a new hard drive, but I'll follow up on this first.

So, just to make sure I have this right:  To check whether the CD and hard drive are on separate IDE channels and both set to master, I have to physically open the computer, right?  Is it then easy to tell if the drives are on separate IDE channels?  Whereas, with master vs. slave, I assume I have to try to find the product manuals online? (I don't have any manuals for the computer).

Thanks again,
Jesse

OK, the first part:

> I opened the computer, saw that the hard drive was set to master and the cd to slave.  I changed CD to master.  The live CD check still returned 1 error.  I couldn't figure out how to tell if the drives where on separate IDE channels though...  I saw that the hard drive was set to 0, I think.  But there was no option for the CD.  Physically, they were plugged in to two different slots,

If they were plugged into different slots on the motherboard, with seperate cables for each, then yes, they were on different IDE channels.  Most computers will have two IDE plugs on the motherboard; one marked IDE0 and the other IDE1.  This plus the separate plug for a floppy on those that have one, and for SATA drives, if those are supported.

And yes, you were right in changing the cd drive to a master, being that they are hooked up each to their own IDE plug; that is, as long as you don't have anything else hooked to the same IDE plug along with the CD drive.  Of course, if you did, you definitely would get an error, because if more than one device is hooked to the IDE drive, one *must* be master and the other *must* be set to slave.

There is one other thing you might try.  I assume that while you might have unplugged the cable from the cd drive to change the shorting pins from slave to master, did you happen to unplug the cable from the motherboard?  Sometimes corrosion will build on a connector, whether plugged in or not, and just unplugging and replugging the cable will give it a good connection again.  I would try this with both the hard drive and the cd drive, on both ends of the cable, both the drive side and the motherboard side.

I don't expect too much, since the Windows side works correctly, but you really never know until you try.  I'm just trying to wrap my mind around the concept that it works under Windows but not under Linux.  I mean, you're right that you don't have any especially esoteric hardware.

Can you boot to the Live CD, and if so, does it run correctly (as it can...I know that some things won't function unless you have access to a hard drive)?  Can you recreate the "bugs" that you experience with an install?

Also, [if this is your computer]("http://support.gateway.com/s//PC/E4100_Series/2800471/2800471nv.shtml") you might want to click on drivers and download the current flash BIOS for your computer.  I don't know whether it would help, but your BIOS is dated 2003, and the one on the website is dated 2005.

Also be aware that, if you decide to flash your BIOS, to do it under a circumstance in which the flashing process **_will not be interrupted_;** specifically, using a UPS so that, should the power fail, the flash operation won't stop.

If you are flashing the BIOS and the process is interrupted, then..._get new hardware_ (you catch my drift?).  You will at least have to put a new BIOS chip in the computer, since you will no longer have access to *_anything_* on that computer...you won't even be able to bring it up through posting operations and boot to the floppy drive so you can re-flash the BIOS.

Try the simpler, less dangerous things first, unless you have cause to believe that it *is* a BIOS issue.

---

### Post by jnewm on 2009-01-26
Thanks again -KG-,

So, I have a bunch of crazy updates!

1) The hard-drive/CD are on separate IDE channels and both set to master, with no slaves plugged in.  I also tried moving and switching around the IDE plugs, and looking for corrosion, but no luck yet resolving the md5sum problem that way.

2) I went out and bought an internal Seagate 500gb SATA hard drive: I figured what the heck, I need a bigger hard drive anyway, and it's returnable if need be.  Plus, I figured it could help a lot with diagnosing my issue.  I then loaded Kubuntu, using Unetbootin from the external hard drive, on all three hard drives: the old internal IDE, the new internal SATA, and the external USB drive.

3) With everything plugged in as usual, the behavior was as before: a) the live CD still shows 1 error/wrong md5sum; b) the internal IDE still returns inconsistent md5sums; c) the internal SATA returns inconsistent md5sums; and d) md5sum actually worked on the external hard drive!

4) BUT I also experienced something new: when I ran md5sum from the internal SATA, checking the exact same .iso file that I had just copied from the external USB to the internal SATA, BUT running md5sum on the .iso still on the external USB, it actually WORKED!  And returned the correct md5sum multiple times in a row!  I then tried again running md5sum on the internal copy of the .iso, and it again returned wrong results...  Crazy!  I tied the same thing on the internal IDE, and again it could correctly md5sum the external .iso.

5) So, I tried something else: I unplugged the CD entirely: from both the IDE and power supply.  I then tried all of the above again.  It went the same, EXCEPT md5sum actually worked from the internal SATA (on the copy of the .iso on the internal SATA).  Which marked my first success md5sum'ing a file on an internal drive!

6) BUT bad news, I rebooted to see what the internal IDE would do, and it still returned incorrect md5sums.  I then booted back into the internal SATA to try one more time, and sadly this time md5sum failed again.  

7) So, I then tried switching the internal IDE to the other physical IDE channel (i.e. plugging it where the CD used to be), and I think I even switched it's power supply plug.  Then, the behavior changed again!: a) md5sum did not work on the internal IDE on an internal .iso (of course), but did work on the external .iso on the USB drive again; b) BUT, when I booted to the external hard drive, md5sum was not working! (the first time md5sum failed on the external USB drive); c) from the internal SATA, md5sum worked twice (i.e. it returned the correct md5sum twice), but then failed again (i.e. it started giving new, inconsistent strings).

Okay, so, needless to say I was losing my mind at this point :).  So...

8) I switched tactics and decided to try the BIOS idea, BUT I was unable to update the BIOS to the 2005 Intel version (the BIOSes did not match).  And after some internet research, it looks like this is because the Gateway version of the Intel motherboard that I have, is actually slightly different and uses a different Gateway-provided BIOS!  More annoying, Gateway has referred support of my computer to some other company, which doesn't have the drivers/BIOS updates readily available on their site.  However, after some more searching, I did find a link to a page that appears to have a matching BIOS update for my Gateway/Intel motherboard (i.e. the Gateway version), see [http://www.support.gateway.com/support/drivers/search.asp?st=pn&param=2520852](http://www.support.gateway.com/support/drivers/search.asp?st=pn&param=2520852).  But I haven't gotten around to trying to flash it yet.  ALSO, I found a couple web pages where it sounds like, with some leg work, people were able to re-flash the motherboard to the Intel version successfully...  So that could be an option too.  See [http://www.tomshardware.com/forum/219665-30-unsuccessful-bios-update-intel-mobo](http://www.tomshardware.com/forum/219665-30-unsuccessful-bios-update-intel-mobo), [http://www.wimsbios.com/phpBB2/topic10179.html](http://www.wimsbios.com/phpBB2/topic10179.html), [http://forums.guru3d.com/showthread.php?t=68181](http://forums.guru3d.com/showthread.php?t=68181), [http://www.eggheadcafe.com/software/aspnet/30037596/gateway-mobo.aspx](http://www.eggheadcafe.com/software/aspnet/30037596/gateway-mobo.aspx), [http://forums.pcpitstop.com/index.php?showtopic=122547&st=10](http://forums.pcpitstop.com/index.php?showtopic=122547&st=10), [http://forum.msi.com.tw/index.php?topic=93134.msg668247](http://forum.msi.com.tw/index.php?topic=93134.msg668247).  (PS The last link seemed to involve first-hand success).

So, lastly, with all that said, here are my plans:

#1 - I still haven't tried booting with the internal IDE hard drive completely removed, because my internal SATA and USB drives don't seem to be bootable on their own.  So, I am going to get my internal SATA bootable, and then try md5sum with all the internal IDE stuff removed (CD and hard drive). 
 
#2 - If that doesn't help, I am going to try to update my BIOS to the Gateway/Intel version.  And then re-try md5sum.

#3 - If that doesn't help, I may even try re-flashing my BIOS to the regular Intel version.

What do you think?  Does that make any sense?  Is there anything else you would try first?

Thanks everyone so much!  
Jesse

---

### Post by -kg- on 2009-01-27
OK.  I thought that I was dealing with a complete noob, but I can see that you at least have my thought train concerning troubleshooting.

I just got back from pool league and am not in the frame of mind to do this at this moment.  Let me sleep on this and, since I'm making this post to your thread, it will be at the top of my "posts list."  I'll attack this with a fresh mind in the morning (I don't have to go to work tomorrow) and see what I can come up with.

Good troubleshooting techniques!

---

### Post by -kg- on 2009-01-27
Well, I just re-read the entire thread and you're right...this is a very confusing problem, and seemingly a problem that is inconsistent.  You try something, and something different works; switch to something else and something else works; the reboot and what worked all of the sudden doesn't, or, as you said, works twice then fails.

I just wonder...have you tried downloading and making the .iso on one of your other computers?  I would try downloading the iso on one of your working computers using a bittorrent client from the [[COLOR="Blue"]_Ubuntu Download page's_[/COLOR]]("http://www.ubuntu.com/getubuntu/downloadmirrors#bt") recommended mirror sites, check the md5sum on that computer to make sure it's good (you shouldn't need to do this step using a torrent download, but...) and either burn the .iso to a CD or using Unetbootin, what ever, and put both the files on to the external drive.

Switch the external drive to your desktop and make the checks, copy the files to where ever you want to check, and check them there, too.  I'm still suspecting a problem somewhere in your desktop's hardware, and just want to confirm that it definitely isn't the download you're using, though to have the exact same problem with several downloads seems too much to be coincidence.

An even better way to check this would be to get a commercially available disk...one that hasn't been downloaded, but commercially produced.  I bought one from Best Buy the other day, but I've never personally had any problem with any of my downloads.

Also, I forget the procedure or software required for md5sum checks and disk integrity check (I haven't had any problems in quite a while, and I always use torrents, which check md5sum as part of the download process), but are you sure that any software you are using to check all this is correctly installed and not corrupted?

With all you've done, I almost can't believe that you haven't been able to find the problem yet.  I'm sitting here wracking my brains (I've been typing this for several hours now) trying to figure out what the problem could be.  With the erratic behavior of the problems, in my mind it almost *has* to be a hardware problem, but I don't know what it would be.

I'm  frankly getting to the point that I'm just slinging mud and seeing what sticks.  Hopefully, you have a good UPS, because I'm coming to the point that one of the last logical things you might try is to flash your BIOS.  I would save that for one of the last things I try, though.

---

### Post by jnewm on 2009-01-28
Hi -kg-, thanks again for all your time!

I know.  I can barely believe it myself.  And it even gets crazier!  So, here are my updates (WITH A SUM AT THE END of what I found most important, since there is a ton of stuff):

#1 - I removed the old IDE hard drive entirely.  And tried the CD integrity check on the IDE CD.  No luck: errors found.  I then switched the IDE cables and power plugs around a bit, trying different combinations.  And tried the CD integrity check on the IDE CD.  No luck: errors found.

#3 - I hadn't yet read your most recent warning about BIOS flashing, and was losing my mind.  So, I decided to try it.  THANKFULLY no problems.  I upgraded to the Intel BIOS using the BIOS recovery method, and my Gateway seems perfectly happy.  UNFORTUNATELY, the change in BIOS did nothing for the problem.

#4 - I then tried removing my CD drive and IDE cable and bringing them with me to work (where we have some old computers).  First, I tried a CD integrity check on my Ubuntu .iso CD in an old computer at work (in the computer's old CD drive).  The check worked fine.  No errors.  So, I then tried plugging in my CD drive, on the old work IDE cable.  No errors.  

_#5 - So, I'm thinking, damn.  Not the CD drive.  No big surprise.  BUT just for the heck of it, I decide to try my CD drive with MY IDE cable (not the work IDE cable).  AND LO AND BEHOLD the CD integrity check finds errors!!!  I then repeat this test over and over like 10 times with different combinations of work and home IDE cables and work and home CD drives.  AND, without, fail both CD drives performed checks with no md5sum errors with the work IDE cable, and both cd drives did have md5sum errors with my home IDE cable!!!_

#6 - So, at this point I'm ECSTATIC!!!  I'm thinking it's just the IDE cable, incredible!  Doesn't quite explain the problems actually running md5sum from Ubuntu once it was installed via Unetbootin, not the CD drive, on my computer.  But, the fact that I could reproduce the errors on a separate computer and CD drive just by using my home IDE cable seemed huge!

#7 - So, I come home fingers crossed, with my work IDE cable in hand of course.  BUT SADLY, no luck.  I seriously almost cried.  CD integrity check, which had just worked at my work with the same combo, does not work here: md5sum errors every time.

#8 - I then go into random mode.  Messing with some BIOS settings for the memory and CD drive.  I try moving my RAM into different slots.  Still no dice.

_#9 - I then read your post, feel a bit inspired :), and download a new .iso onto my laptop in Ubuntu.  Md5sum checks out perfect time after time.  I then copy the file to my USB hard drive.  I md5sum that from my laptop.  It checks out fine time after time.  I then move the USB drive to my new computer, and md5sum the .iso from my SATA drive, unetbootin ubuntu live, and md5sum STOPS working._

PS Somewhere around here I totally disconnect my IDE CD drive, just to make sure it's not just having it plugged in that is screwing things up.  No change.

_#10 SO...  I think it HAS to be hardware, right?  BUT I learned one other interesting thing.  I started just md5sum'ing everything in sight on my USB drive.  And it turns out that md5sum works on everything up to about 200mb.  AND then FAILS on anything 300mb + in size (such as the .iso)._


SO... IN SUMMARY, most important points: (1) new SATA hard drive and IDE hard drive completely removed, no dice; (2) **my CD drive with my CD cable on a different computer also returns CD check errors!!! BUT (deception of deception) work cable with my CD drive back at home still DOES return errors :(**; (3) **last but not least, md5sum does NOT work on a totally clean .iso tested on a USB drive on my computer, BUT md5sum works on any file up to about 200mb! **

WHICH, leads me to my final hopes before resorting to a whole new computer (or giving up on linux on this computer for now): 1) get my hands on a different piece of RAM -- because, even though my RAM passed the memory test, it seems so much like a memory problem that md5sum only fails on bigger fails, right? (although I guess that still leaves unexplained why md5sum works on the big files in windows); 2) get my hands on a USB CD drive, just in case...  I don't know...  Maybe that isn't even worth it...

Finally, if none of that works, all I can say is it's got to be the motherboard itself, right?  I can't come up with anything else...

Let me know if you have any other ideas, and I will definitely give you a heads up tomorrow evening after I get a hold of some new RAM to try.

Thanks again so much!
Jesse

---

### Post by Gizenshya on 2009-01-28
sorry if I missed something, as its complicated.

but...

have you tried a new ide drive witha new cable ON your computer?

once seemingly narrowing the problem down to your computer, that would be the first thing I'd do.  new drive and new cable.  then try swapping ide slots (just remove the hdd if need be).

now, does an md5checksum work with your troubled computer setup while in an OS?  or is it just when checking at install at boot?

Also.. jsut because a cable is new doesn't mean it necessarily works.  I've had people with similar problems have 'drives' go in and out and new cables seeminglynot work.. and the issue was poor handling of cables (ide cables can separate easily if mishandled).  pins can bend.  and with the broken or separated cable ends (or even in the middle of a cable) the problem can go away and come back as connections come and go.

but in general, its usually a good idea to take chunks of things out of the equation, and then narrow it down from the data, instead of tackling toomany small things at once.

on a side note.  some other things that I'd probably do before doing much of what you did...

swap out a hard drive with another working comp, install to the drive, then swap back.

install to the drive in a USB enclosure

install from your drive (or any other ide drive) thats hooked up to the hookups from an external ide enclosure (yeah, you can do that! I did it for my most recent install. ;) )

same is true for SATA drives (hdds, rom's, and also laptop (2.5") drives work in 3.5" sata enclosures).

install from a network image

there are tons of ways to work around it :)

---

### Post by jnewm on 2009-01-28
I CAN'T BELIEVE IT!  IT'S SOLVED!  IT WAS MEMORY ALL ALONG!

Ok, first off, thanks again -kg- for all your help, and thanks Gizenshya for the excellent ideas.  

So, let me tell you what happened, and why this is strange:
(1) I ran memtest for 24 hours about a month ago, long after I noticed these md5sum problems.  No errors.
(2) Md5sum works perfectly in Windows.  So I figured, if it were memory, it would have affected Windows too.  Right?  (Apparently, wrong).
(3) BUT, last night I decided to try memtest again, and after 12 hours of testing, it reported about 7 errors.
(4) I brought my computer to work today and borrowed the memory from an old computer that successfully checked the CD's integrity and successfully md5sum'd within Ubuntu.
(5) SUCCESS!!!  My computer ran the Live CD integrity check with no errors for the first time ever. AND just to confirm, I booted into Ubuntu through Unetbootin, and it successfully md5sum'd the .iso file (and believe me, I tried like 30 times).

Anyway, if only I had just switched the memory first I would have saved so much time and energy!!! (And even buying a new hard drive).  BUT, the good news is: I learned a ton and I can now use Ubuntu and any other variant of linux I want on this computer :).  Plus I needed a bigger hard drive anyway.

So, if anyone else ever reads this thread because they are having similar md5sum/CD integrity check problems, my advice is: try switching the memory! (even if memtest is working, and md5sum is working in Windows).

Thanks again all!  I'll mark this as solved as soon as the option returns to forums,

Jesse

---

### Post by -kg- on 2009-01-28
YeeHAW!!

I read your second to the last post and my heart rose when you talked about the successful/unsuccessful tests on your work computers with the cable.  Then it sank into my boots when it was once again unsuccessful back at home.  I was nearly in tears.

Then, when you were able to declare success in your final post, it was like a burden was lifted.  That is really great!  You know, you should consider a side career in electronic melodrama.

:lolflag:

You know something else; I think I would go ahead and put a new CD burner *and* cable, just in case.  I don't know if a weak CD-Burner or a slightly faulty cable would cause a problem with memory, but with the prices on newer CD/DVD burners being what they are, what the heck, if you can afford it.  Or, like you said, an external.

> So, if anyone else ever reads this thread because they are having similar md5sum/CD integrity check problems, my advice is: try switching the memory! (even if memtest is working, and md5sum is working in Windows).

That still isn't necessarily the only thing that might cause such a problem, but it should be held out as a consideration, for sure.  Congrats!  I think everyone involved feels they have won a victory right along with you, even though you did the lion share of the work and we just armchair quarterbacked. :p

Enjoy, and see you around the forums.

---

### Post by jnewm on 2009-01-30
Hilarious!  I am glad to see I was able to wrap you up in my melodrama -kg- ;).

But seriously, I would have given up long ago if you and the other posters hadn't been giving great help and advice.  So it is definitely a team victory, and thanks again!

And thanks for the advice on following up with whatever what might have caused the faulty memory.  You know, now that I think about it, I wouldn't be entirely unsurprised if the memory was faulty to begin with.  I think I bought the memory from and had it installed back in the day by (before I knew how install memory) a relatively shady guy at a little computer shop.  And while that doesn't quite explain past successful memtest checks, maybe it just took a full 24 hour test to find the errors.

Anyway, I replaced the CD cable already, and will think about replacing the CD drive.  But a fresh, error-free, ubuntu is already running on my computer!!!

Yay! :popcorn:

PS -kg-, now that I have two apparently working hard drives on the same machine (80gb IDE and 500gb SATA), any thoughts on how best to use those while prolonging hard drive life and without wasting electricity?  For instance, I was thinking I'd use the 500gb as my main drive and backup important files to the 80gb.  But does that mean I should do something so that the 80gb isn't running all the time, or at least not spinning every time I turn on the computer?  Or is it better for hard drive life just to leave it running?  And does it make a difference in terms of electricity?  Anyway, obviously this is a new question, and my real problem is solved, so no obligation to reply.  I just thought you might be a good person to ask regarding this more mechanical question. :)

---

### Post by -kg- on 2009-01-31
> **jnewm said:**
> PS -kg-, now that I have two apparently working hard drives on the same machine (80gb IDE and 500gb SATA), any thoughts on how best to use those while prolonging hard drive life and without wasting electricity?  For instance, I was thinking I'd use the 500gb as my main drive and backup important files to the 80gb.  But does that mean I should do something so that the 80gb isn't running all the time, or at least not spinning every time I turn on the computer?  Or is it better for hard drive life just to leave it running?  And does it make a difference in terms of electricity?  Anyway, obviously this is a new question, and my real problem is solved, so no obligation to reply.  I just thought you might be a good person to ask regarding this more mechanical question. :)

Well, if you decided to use the newer hard drive to store important files, and the newer hard drive to actually run your system, then a couple of considerations would have to be addressed.

What type of files would these be, and how often would you anticipate needing to access them, or to add new files to it, or update the existing ones?  If you just planned to make image files of your operating system every once in a great while, you could store the image files there, then unplug the 80 GB drive, both power and IDE cable.  The drive certainly wouldn't spin up and run while the computer was on.

However, if you were to anticipate a need to access that drive daily (or even semi-daily) then I would leave it hooked up.  There is a certain amount of risk involved in unplugging and then plugging the cable to a hard drive, especially the ribbon cable plug.  Pins can be bent or broken (don't ***I*** know...not long ago I had to take one apart and solder a pin back on the circuit board - a rather daunting task!) and ribbon cable wires can be broken (leading to another set of problems...a lot more easily corrected, but leading to more troubleshooting problems, and I think you know about that! :D ).

If I remember correctly (from a long time back, and possibly an earlier Windows version) there was a way to regulate hard drive spin up and down times, and their delays.  It might be so under Linux, but I'm not sure, and I'm thinking it's not a problem under Linux, anyway.  When I'm running Windows, I will typically see a lot of disk activity, but running Linux I usually see little or no disk activity, unless I'm doing something that I *know* will cause it (like saving a file or whatnot).

Of course, I'm used to seeing some amount of disk activity all the time, since all of my computers are continuously running [BOINC (The Berkeley Open Infrastructure for Network Computing)]("http://boinc.berkeley.edu/") distributed computing projects in the background.  But I do notice that my drive light blinks much less often under Linux than it does under Windows.

I really don't know what to suggest to you.  If your 80 GB is more than, say, 3-4 years old, you might want to consider switching to the newer one and, if it's much of a concern to you, take it completely out of the system and store it somewhere for emergencies.  It has a working OS on it, and it might come in handy someday in recovering in the event of catastrophic failure to recover vital files, without having to use the Live CD or a recovery disk (much faster, and less hassle).

Or, continue to use the 80 GB as your main system disk, save images of the partitions on it on a fairly regular basis, and use it until it does go out.  Then you've gotten the max life out of the drive and can quickly recover when it goes.

Really, it's not much of an issue to me.  The first time I added a larger hard drive to my system, I used it as a secondary drive, partitioned it, and put files on it.  Then my first drive started to go, so I bought another one, cloned the partitions on it to the newest addition, and put it in it's place as the primary, leaving the old one as it was.  It was just easier than trying to transfer partitions back and forth.  Both of those drives are still in my desktop (the secondary is the one I broke the pin off the circuit board), along with a new TB SATA drive.

Just be sure to do fairly regular backups.  I screwed up my partition table on the desktop's primary drive and eventually was forced to completely reinstall Windows fresh and everything.  No big deal, really...I recovered all my really important files, and my previous incarnation of Windows really needed a fresh start, anyway.  That, and I was in the process of making the switch to Linux, anyway, so wasn't really concerned about dragging along all the accumulated "baggage" from the other install.  :D

Oh, a little "tip and trick" I learned when making back-ups (you might already have figured this out); when you make an actual image of a disk or partition ("bit by bit" as opposed to only used sectors), you must recover to exactly the same size partition (and, I think, partition scheme, if my memory serves me).  I have found it useful to include a little text file describing the exact size of the partition(s) and their layout on the disk so that I can replicate it should it be necessary to set up a new hard drive and recover to it.

Now, I haven't checked it out, but apparently [PING]("http://ping.windowsdream.com/ping.html") is a backup utility that not only will create a backup image of the partitions, disk, MBR, and Partition Tables, but will back up BIOS settings, as well.  Sounds real handy.  To this point, though, I have only used [Clonezilla,]("http://clonezilla.org/") with a very good tutorial on it (and PartImage) [at this site.]("http://www.dedoimedo.com/computers/free_imaging_software.html")

Of course, I have all this information and more at:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

I re-wrote this page a little while back, and tried to include as much information on it as I could, while still keeping it within the realms of basic.  Quite a bit longer than the original, but if you've noticed, there are quite a few questions on partitioning in the help forums, and it makes a real good reference to point someone to.

---

### Post by jnewm on 2009-03-01
Hi -kg-,

Sorry for the delayed response to your very helpful response to my last question :).  After the many many hours solving that damn md5sum problem, I decided to take a brief computer break ;).

That all makes perfect sense.  I think I will just let the old IDE drive load up and function in the background as a back-up drive until it kicks the bucket.

Thanks again so so much for all your advice!!!

---

