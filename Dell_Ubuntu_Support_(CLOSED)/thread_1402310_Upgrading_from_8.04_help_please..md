---
title: "Upgrading from 8.04 help please. :/"
date: 2010-02-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nickxm on 2010-02-09
Okay I am running a Dell Mini 10v and as stated, it is running on 8.04.2.. But when I go to Ubuntu.com and look at the upgrade information and how-to, it states how easy it is and I read through it and the pictures, it seems very easy!

Except nothing is matching up... It says I can do the upgrade by changing the update in System Sources; but I do _not_ have an "update" tab in my System Sources... The only thing I can think of is am I not using 8.04 LTS? Is there other versions of 8.04? If so how the hell am I suppose to update it? Lol...
(Am I running the Netbook remix..?)

I am very confused at the moment, some help would be great...

I am looking to upgrade up to 9.10. 
Do I need to use a Flash drive to install (If so, how big of a drive do I need?) or can I really do this through system sources somehow?

Thank you in advance.

---

### Post by Kixtosh on 2010-02-09
AFIK, you can only upgrade to the next release, in turn, unless you want to do a complete install (using a Live CD etc., and which would be hardly very convenient unless you store all your documents on a separate partition, so that they don't get wiped out by the install process).

Otherwise, since you have a LTS release, why not wait for the next LTS, which will be available in April? It's actually already available in beta, but it may still be very buggy. You can upgrade directly from one LTS release to the next LTS release, so from 8.04 to 10.04, but not from 8.04 to 9.10, since Karmic Koala is not a LTS release and is therefore subject to the normal rules of not being able to leapfrog over intermediate releases.

From here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

> An upgrade is the process of going from an earlier version of Ubuntu to a newer version of Ubuntu. An example of this would be going from Ubuntu 7.10 to Ubuntu 8.04 LTS. To avoid damaging your system, **[COLOR=Red]u[/COLOR][COLOR=Red]pgrading should only be done from one release to the next release[/COLOR]** (e.g. Ubuntu 9.04 to Ubuntu 9.10) [COLOR=Red]**o****r from one LTS release to the next**[/COLOR] (e.g. Ubuntu 6.06LTS to Ubuntu 8.04LTS). If you wish to 'skip' a version, you can backup your data and do a fresh installation, or progressively upgrade to each successive version. For example, to upgrade from Ubuntu 8.10 to Ubuntu 9.10, first upgrade to 9.04, then upgrade 9.04 to 9.10. And also worthy of note:

> ...The LTS version is recommended for people in an environment (generally commercial/industrial) that want to keep the same version for a longer amount of time...

---

### Post by Nickxm on 2010-02-09
I mostly use my netbook to travel and mess around with, nothing too serious. (That's what I use my Desktop for.) so I was really just looking to upgrade it and play around with new lil features and such. I am well aware that I would have to upgrade from 8.04 -> 8.10, etc but I am unaware of how to do it. Since as shown here
[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

It says I should be able to just hit the "Updates" tab and it's very easy but I do not have this option. Under my "Updates" tab I have just an option to automatically check for updates; nothing to change my sources to "Normal".  (And for that matter, I only have tabs for Update, Third-Party Software and Authentication.) 

Will I have to make a bootable USB to get to 8.10? :/

& Thank you very much for your post, having some response is very nice.

---

### Post by Kixtosh on 2010-02-09
When you enter the Update Manager, you should see a "settings" button to click. In my version, it's on the bottom left, not far from the "check" button on the bottom right hand side. When you click that, you should see the Updates tab, where my version has an option to modify which new releases are shown ...

Show New Distribution Releases:

- "Normal releases" (default setting in my case).
- "Never".
- "Long term support releases only".

This is at the very bottom of the tab, in my case. Do you have the "settings" button to click when you first launch the Update Manager from the System menu? I'm running Xubuntu now, or I would try to guide you more precisely if I could.

*P.S. To upgrade directly to Karmic Koala, you could just use a Live CD, if you have a CD drive (and if that is more convenient).*

---

### Post by Nickxm on 2010-02-09
I have no settings button either. :( 

Here's a screenshot of my system with System Sources and Update manager open so people can kind of understand better my problem here, lol.

[IMG]http://img688.imageshack.us/img688/2066/screenshotot.png[/IMG]

---

### Post by Nickxm on 2010-02-09
Again I will say thank you for the replies, it's good to see. :) 

I am currently scouring everywhere trying to find some information on it. I can't explain it and so far am coming up empty handed that is why I posted this thread. I am still looking but not much is pointing towards why I do not have those available settings running any of the 8.04 versions.

---

### Post by Kixtosh on 2010-02-09
> **Nickxm said:**
> I have no settings button either. :(  ...Well, that doesn't look hopeful, unless other Hardy Heron users have found preference settings elsewhere that can manage this setting.

To be honest, I've read some posts where users claimed it was a lot easier to just update from a new installation rather than the usual update procedure anyhow, but I cannot offer a personal opinion on the subject since since I have yet to try the upgrade process (other than for normal updates). I'll probably keep all my documents safe (on a separate partition) for that very reason, just in case they are correct!

Hopefully somebody can offer a better answer before too long ... or at least confirm that if you wait for the new LTS release in just about two months from now, your system is actually set by default to upgrade.

---

### Post by Kixtosh on 2010-02-09
Did you try this procedure yet? It will only allow you to upgrade to Intrepid Ibex, but that's one step closer, and from there you could continue on to the next two releases, if you don't want to wait for April!

[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

---

### Post by Nickxm on 2010-02-09
I have looked through that and most seem impossible to do with what I know. I may just try to make a USB Bootdrive to update tomorrow unless when I wake up there is other users suggestions. :)  I appreciate you trying to help Kixtosh. :popcorn:

---

### Post by snowpine on 2010-02-09
Did you install Ubuntu 8.04 yourself, or is it the special "Dellbuntu" that comes preinstalled on the Mini series? 

If you have the special Dellbuntu, there is no upgrade path. It was a one-time special operating system that Canonical and Dell collaborated on. You will have to do a fresh reinstall if you want a newer release (but make sure you read and understand ahead of time the steps you'll need to get wireless working).

Some good tutorials on this site: [http://www.ubuntumini.com](http://www.ubuntumini.com)

Even if you have "regular" Ubuntu, I would still recommend a fresh reinstall as the easiest and safest way to get 9.10.

---

### Post by Elvis99 on 2010-02-09
> **Nickxm said:**
> 
I am very confused at the moment, some help would be great...

I am looking to upgrade up to 9.10. 
Do I need to use a Flash drive to install (If so, how big of a drive do I need?) or can I really do this through system sources somehow?

Thank you in advance.

Installation Types

Netbook Remix
1GB thumb drive with everything backed up elsewhere, because these commands will over write the partition table. 
ISO image file, or CD and another computer ubuntu-netbook-remix ISO, or kubuntu-netbook ISO, or 
Optional, large capacity SD card for storing ISO and or backing up data.

[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

---

### Post by Nickxm on 2010-02-09
Thank you Snowpine, you have told me exactly what I needed to hear. It was the one that came installed on the mini. Guess I have to look into making a USB install. Thank you very much for letting me know that. :KS

---

### Post by recluce on 2010-02-12
> **Nickxm said:**
> Thank you Snowpine, you have told me exactly what I needed to hear. It was the one that came installed on the mini. Guess I have to look into making a USB install. Thank you very much for letting me know that. :KS

I would highly recommend waiting for Lucid (10.04), since it is a one step upgrade to the most recent version. Only two months to go...

---

### Post by snowpine on 2010-02-12
> **recluce said:**
> I would highly recommend waiting for Lucid (10.04), since it is a one step upgrade to the most recent version. Only two months to go...

Not for "Dellbuntu" 8.04 users... Canonical is dropping support for the lpia architecture. 

A fresh reinstall is the OP's only choice at this time.

---

### Post by recluce on 2010-02-12
> **snowpine said:**
> Not for "Dellbuntu" 8.04 users... Canonical is dropping support for the lpia architecture. 

A fresh reinstall is the OP's only choice at this time.

I didn't know about this - and some reading proofed that you are quite right. I don't think Cannonical is doing Ubuntu a favor. Do you know of any other Linux distributions that have ongoing lpia support?

BTW: Cannonical recommends to upgrade lpia systems no further than Jaunty!

---

### Post by snowpine on 2010-02-12
> **recluce said:**
> I didn't know about this - and some reading proofed that you are quite right. I don't think Cannonical is doing Ubuntu a favor. Do you know of any other Linux distributions that have ongoing lpia support?

BTW: Cannonical recommends to upgrade lpia systems no further than Jaunty!

LPIA (Low Powered Intel Architecture for those just joining us) was unique to Ubuntu and its niche was an OEM offering for Dell and other netbook manufacturers. IMHO it was a marketing gimmick ("wow, Canonical made a special version of Ubuntu just for us!!!"); the Atom is well-supported by the Linux kernel itself.

---

### Post by Greyed on 2010-02-13
> **snowpine said:**
>  the Atom is well-supported by the Linux kernel itself.

Except it's not, still.  And people repeating this does not change it.

To the OP, yes, you'll have to create a live USB and install from there.  It is actually fairly painless.  I would highly recommend that when you do so that you reduce your Dell Remix 8.04.2 to a small partition (16Gb is what I chose for mine) and keep it there to fall back on.

Futhermore unless you're planning on waiting for 2 months do not jump to 10.04.  Note it is 10.02 right now and 10.04 is only on alpha2.  There are known problems with alpha2 which, unless you're a developer, you probably don't want to deal with.  Heck, I've used Linux for over a decade and *I* don't want to deal with them.

9.10 is the latest version available.  It works, mostly.  However be aware that the wireless driver is not installed by default (a regression in my book since it was in 9.04) and your video performance *will* suffer.  If you're not watching flash videos (Youtube, et al) or doing any sort of gaming (even 2D) then you shouldn't notice.  If you are watching videos and/or doing any kind of gaming you will notice the massive regression in video performance compared to Dell's 8.04.2.  It is this video regression why I still maintain my 16Gb 8.04.2 partition and get a tad upset when people say the 10v is "well supported by the linux kernel itself".

Finally, consider installing stock 9.10.  UNR only adds tweaks to "accomodate" the smaller screen of the netbooks.  If you're like me those tweaks will probably just piss you off and getting rid of them is an exercise in head-banging frustration.  Maximus, I'm lookin' at you, bub.

---

### Post by snowpine on 2010-02-13
Greyed makes a good argument :) and so I will point out that 8.04 will be fully supported through April 2011. There is no **need** to update at this time, if you are happy with 8.04 lpia (I wasn't and so none of my 3 Atom computers are running lpia).

---

### Post by Merk42 on 2010-02-13
> **Greyed said:**
> 9.10 is the latest version available.  It works, mostly.  However be aware that the wireless driver is not installed by default (a regression in my book since it was in 9.04) and your video performance *will* suffer.  If you're not watching flash videos (Youtube, et al) or doing any sort of gaming (even 2D) then you shouldn't notice.  If you are watching videos and/or doing any kind of gaming you will notice the massive regression in video performance compared to Dell's 8.04.2.  It is this video regression why I still maintain my 16Gb 8.04.2 partition and get a tad upset when people say the 10v is "well supported by the linux kernel itself".

But is that regression going from 8.04 to 9.10 or lpia to i386? 
If it's the former, then you really can't get upset about people saying the 10v is "well supported by the Linux kernel itself"

---

### Post by Greyed on 2010-02-13
True, but it is hard to tell when the 8.04 stock kernel is not supposed to support it well.  The two are so intermingled it is impossible to determine if the problem is lpia -> 386 or regressions in the kernel/video drivers.  :(

---

### Post by Merk42 on 2010-02-14
> **Greyed said:**
> True, but it is hard to tell when the 8.04 stock kernel is not supposed to support it well.

Who says it's "not supposed to support it well"?
What is stopping you (or anyone) from running tests with 8.04 lpia "Dellbuntu" and then rerunning those tests with the regular i386 build of 8.04?

In fact, I'm pretty sure those tests were run, and the differences were found to be negligable and not worth maintaining another architecture which is why it was dropped.  There was [a conference about it during UDS months ago](https://wiki.ubuntu.com/Specs/Mobile/LpiaFuture).

---

### Post by snowpine on 2010-02-14
My money would be on the Intel video drivers. There have been some regressions in these drivers lately, across all distros.

I use my netbooks mostly for email and forums (and have a Playstation for games ;)) so maybe my needs are different than yours. I did not expect the netbooks to be graphics powerhouses when I bought them. I am curious to check out the new nvidia ion platform at some point though...

---

### Post by Greyed on 2010-02-14
> **Merk42 said:**
> Who says it's "not supposed to support it well"?
What is stopping you (or anyone) from running tests with 8.04 lpia "Dellbuntu" and then rerunning those tests with the regular i386 build of 8.04?

Ubuntu itself?

> In fact, I'm pretty sure those tests were run, and the differences were found to be negligable and not worth maintaining another architecture which is why it was dropped.  There was [a conference about it during UDS months ago]("https://wiki.ubuntu.com/Specs/Mobile/LpiaFuture").Yes, read into that issue a tad more.  The move to have the base kernel compiled with options needed to support LPIA well enough to move to drop an LPIA specific distribution didn't happen until after 8.10 if memory serves.  So comparing 8.04 LPIA to 8.04 i386 does nothing to address 9.10 i386.

> **snowpine said:**
> My money would be on the Intel video drivers. There have been some regressions in these drivers lately, across all distros.

I believe so, too.  But part of those driver regressions are because Intel is reorganizing portions of the drivers out of user space and into, *dundundunnnnnn*, the kernel.  ;)'

> I use my netbooks mostly for email and forums (and have a Playstation for games ;)) so maybe my needs are different than yours. I did not expect the netbooks to be graphics powerhouses when I bought them. I am curious to check out the new nvidia ion platform at some point though...I pointed out two specific examples.  2D games and viewing videos off a website widely known and popular for videos.

The specific game in question, and the one I use as a benchmark, is [Yohoho! Puzzle Pirates]("http://www.puzzlepirates.com/").  8.10, runs smooth.  9.10, extremely choppy.  And videos off of Youtube at SD (360p) quality is hardly what I would consider a requirement for a graphic powerhouse.  Heck, my previous laptop, a 10 year old 667Mhz PIII plays them fine.  8.10, smooth and annotations work.  9.10, choppy at times and annotations flicker.

I'm not asking it to do even the simplest of 3D work or even high end 2D work.  We're talking simple screen updates and low-rez video causing serious chugging.

---

### Post by snowpine on 2010-02-14
I've tried dozens of distros on my three Atom-based computers, and for Flash performance, the clear winner by far was.... (drum roll please).... Windows. :)

In distant second place is CentOS, which has much older drivers compared with say Ubuntu 9.10.

---

### Post by Greyed on 2010-02-14
> **snowpine said:**
> I've tried dozens of distros on my three Atom-based computers, and for Flash performance, the clear winner by far was.... (drum roll please).... Windows. :)

Well, yeah.  But that ain't touching this machine.  I'll just upgrade to a System76 Darter Ultra.  My one Windows install is for games.  My netbook/laptop ain't a gaming machine.  Ergo, Ubuntu, preferably pre-installed so I can show commercial support.  :)

> In distant second place is CentOS, which has much older drivers compared with say Ubuntu 9.10.

Well, hopefully Intel will get this mess straightened out, soon.  Regardless we're straying pretty far afield and I bet the OP is all 8-[ now.

---

