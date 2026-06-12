---
title: "Sidux Talk"
date: 2007-01-27
forum: Debian
---

### Post by Rodneyck on 2007-01-27
Here is a new Debian based distro I am keeping my eye on. Others have reported that it is much faster than (K)Ubuntu and is running the latest kernel under the hood.

The name sidux represents a new project and distribution created by a recent split in the KANOTIX developer community. After two months of work, the initial preview version of sidux 2007-01 has been released for public testing: "I have the pleasure to announce the first public preview for sidux 2007-01. This release is a proof of concept for the sidux building environment. What's on the menu: amd64 and i686; Debian 'sid', up to date as of 2007-01-24; kernel 2.6.19.2; minimal, but fully functional KDE 3.5.5; completely overhauled live mode; largely adapted installer; new graphical installer front-end...." 

[http://sidux.com/](http://sidux.com/)

---

### Post by mips on 2007-01-27
I had it installed on my laptop a few months ago before the cd was released. It definately is faster than ubuntu. It has all the latest stuff available. Kinda stable cutting edge.

---

### Post by xabbott on 2007-01-27
Is this intended more as a live disc? I can't really find anything that makes this better than just running Debian Sid itself. The days of repackaging Debian for the sake of a new installer are numbered. The Etch GUI installer is just as friendly as any other.

---

### Post by mips on 2007-01-27
> **xabbott said:**
> Is this intended more as a live disc? I can't really find anything that makes this better than just running Debian Sid itself.


I dunno about the live disc thing as i used it before there was any disc available (was net install of debian, upgrade to sid, add repos & run a script).

There will be differences between sid & sidux. The goal of Sidux is to provide you with a stable sid ala kanotix which they split from.

---

### Post by Rodneyck on 2007-01-27
I read somewhere on their webpage that a livecd will happen. This is their initial "pre" release, the official release will happen in another two weeks.

There will be some unique Sidux applications included in the official release, probably to dectect hardware/apps, easier installation, etc. So that sets it apart from pure Debian I guess.  It is a welcome for me as Debian sid is pretty basic (not that that is bad) but sometimes you don't feel like searching forums and reading for hours on how to make the screen gamma increase or install some codec.  

Now is the time to jump in if you would like to provide input as to what will be included in their official release app-wise, as there is a thread about it on the forum. When they do release (personaly, I don't want to go through updating again in another two weeks) I will jump in and take it for a spin.

---

### Post by Rodneyck on 2007-02-13
**sidux 2007-01 preview 3**

We are a little late in our release schedule for sidux 2007-01 since Kernel 2.6.20 entered the stage, most of our efforts have gone into adapting sidux for the new kernel, fixing a number of smaller issues reported over the last two weeks so we would like to take the opportunity of releasing another preview to test regressions imposed by kernel 2.6.20 and to confirm fixes we cannot test ourselves. Please note this is not the final release. The full featured final release of sidux-2007-01 "&#935;&#940;&#959;&#962;" will be ready soon (i686 and amd64), intermediate xdeltas will be provided as needed until then. 
As already mentioned in "sidux Release Plan" we're skipping preview 2 which couldn't be released due to grave bugs in time, special thanks go to our qa teams to uncover these issues on their hardware.

Complete Story...
[http://sidux.com/Article99.html](http://sidux.com/Article99.html)

---

### Post by Rodneyck on 2007-02-17
A quick update to Sidux. Preview 4 was released today to add a fix regarding problems with booting from some drives (including sata and usb.)  

I got a chance to take this baby for a test drive and I must say, this distro is fast, really fast on my system using KDE for the desktop. It is about to hit final release anyday now and I plan to replace Kubuntu when it does.  I have had my eye on this one and I am excited it has turned out as I hoped.

These guys are serious about no proprietary anything, so you basically get a stable Debian Sid bare-bones system with a few of their handy handmade apps to help you install software and hardware. One unique app I want to try once I put my TV card back in the box is to configure TV cards (bttv-chipset). There are many more all housed under "Sidux" on the Kmenu. 

With only 400mb CD, you have the terminal and APT to work the magic. I did install Adept (synaptic equivalent for you Ubuntu users) just to make life easier. The proprietary stuff is easy to hunt down, as there are many Debian howtos and downloads on the internet.

The only negative is minor. The current artwork is a bit scary, sort of gay leather bar meets Alien The Movie graphical appearance, but I think (at least I hope) all that will change for the final release. I believe I read that on one of their releases. Again, a minor squabble as I usually tear apart the eye candy to my liking anyway. It just does not have the warm inviting feel at the moment.

If you are looking for something to tweak, staying in the Debian family with speeds that rival Gentoo and Arch, give Sidux a try.

---

### Post by qpieus on 2007-02-19
I ran preview 4 on parallels and I like it. It is fast, even running on the VM. It saw my networked printer and file server right out of the box, which some other live distros didn't do. When this thing is finalized I think I'll install the hard drive on a spare computer and give it a spin.
Does sidux use the debian repositories (I assume), or their own repos?
You're right about the wallpaper artwork - that's gotta go.

---

### Post by Rodneyck on 2007-02-19
It uses both sid and their own repos I believe. I would check but I am running Kubuntu from my first hard drive at the moment. 

Regarding the artwork, I have made my comments known on their forum, even provoking their graphic designer to step in. It appears most users over there like it. 8-[ 

Since they seem to be stuck on this planetary theme, I only hope they make it more professional looking in the end, polished.  Red and black though... :-|  If I can remember back to my college days in color theory class, doesn't prolong exposure to the color red cause the following; inflammation, stomach cramps...harsh vomitting, excess mucus build up, pregnancy, iron deficiency...on and on?

---

### Post by Rodneyck on 2007-02-21
Wooo Hooo!!!  I have been waiting, and waiting....waiting, for this release. Sidux final release is today. I love this new distribution, one of the fastest, if not the fastest Debian-based distributions around. This is cutting edge...debian sid made stable and also includes the new 2.6.20.1 kernel.  How's that for a cherry on top?

Please read the manual which includes helpful installation tips (especially if you have problems installing) and other goodies, such as 3D driver support and more.

Manual:
[http://manual.sidux.com/](http://manual.sidux.com/)

Press release...

> After 3 months of development we are proud to annouce the immediate availability of the sidux-2007-01 "&#935;&#940;&#959;&#962; release" for amd64 and i686 systems, shipping in a ~402 MB lite KDE and a ~700 MB full KDE flavour. sidux is a full featured debian sid based live CD with a special focus on harddisk installations, a clean upgrade path within sid and additional hard-/ and software support.

This is the first official sidux release after stabilizing and largely rewriting the distribution framework, further efforts in that direction are ongoing to improve the hardware support/ detection and streamline the live operations. While the first release concentrates on two KDE flavours (lite and full), special purpose releases and support for other desktop environments and window managers are planned. The ISO is completely based on Debian Sid and enriched & stabilized with sidux' own packages and scripts. It comes with kernel 2.6.20.1, which is based on the most recent vanilla kernel together with several patches for improved hardware support and allows initial testing of kvm for pacifica or vanderpool compatible CPUs (AMD64 for socket AM2, Intel Core2).

Now to the interesting topics, like what's on the menu:
amd64 (AMD64, Intel Core2, newer 64 bit capable Pentium 4 CPUs (watch for the "lm" flag in /proc/cpuinfo or use infobash -v3) and i686 (pentium pro/ pentium II or newer).
debian sid, up to date as of 2007-02-21.
kernel 2.6.20.1 (smp, voluntary preemption). 
kvm virtualization support for pacifica or vanderpool compatible CPUs (AMD64 for socket AM2, Intel Core2)
KDE 3.5.5 (en + de).
completely overhauled live mode.
largely adapted installer.
new graphical installer frontend.
netcardconfig can cope with wpa/ wpa2 again.
offline manual for en + de directly on the disc, online manuals for more languages online at [http://manual.sidux.com/;](http://manual.sidux.com/;) a big thank you goes to the documentation and translation teams!
a completely new ISO creation process written from scratch in a clean room environment.

More..

[http://sidux.com/Article116.html](http://sidux.com/Article116.html)

---

### Post by mips on 2007-02-21
> **Rodneyck said:**
> Wooo Hooo!!!  I have been waiting, and waiting....waiting, for this release. Sidux final release is today. I love this new distribution, one of the fastest, if not the fastest Debian-based distributions around. This is cutting edge...debian sid made stable and also includes the new 2.6.20.1 kernel.  How's that for a cherry on top?


Thnx for the heads up. Busy downloading the 32bit full version for my laptop (my test machine now), no ways i'll do 64bit on any debian based distro.

I liked this distro way back when I tried the beta via debian net install. I think handy from Oz might also be interested.

Btw. Feisty is using a newer kernel.

---

### Post by Rodneyck on 2007-02-25
I have been running Sidux since Final release, actually before, but only as a test. I have zero complaints so far and loving every minute of it.

Here is a nice write-up in the event anyone is interested...

> Their self-proclaimed long-term ambition: to "strive to do the impossible: making Debian Sid (aka "Unstable") stable. The goal is to become the best Debian Sid based live distro with special focus on clean and easy hard disk install. Strategic milestones and 3-4 annual releases timetabled will give stability and accountability to corporate and home users with a demand for bleeding edge software running on modern hardware, as well as a definable path over time."

Full story...
[http://www.netscape.com/viewstory/2007/02/24/sidux-a-new-star-in-the-linux-galaxy/?url=http%3A%2F%2Fwww.kdedevelopers.org%2Fnode%2F2691&frame=true](http://www.netscape.com/viewstory/2007/02/24/sidux-a-new-star-in-the-linux-galaxy/?url=http%3A%2F%2Fwww.kdedevelopers.org%2Fnode%2F2691&frame=true)

---

### Post by mephisto786 on 2007-02-25
You go boy! Perfect timing......!   Kanotix was great, and im glad this lives up to its heritage
Finally, a Debian based deriv with brains......:-P

Last Kanotix stable was 2005, talk about a long time between releases

cheers,

---

### Post by Rodneyck on 2007-03-02
Quote from ReviewLinux...

> Three months of development has created SIDUX 2007-01, which is now available for download. New in this ex-KANOTIX developer release is a rewritten distribution framework, further efforts dealing with hardware support/detection, and lite and full editions of SIDUX. Check it out at Phoronix.
[I just downloaded and burned a CD if Sidux, I will be putting it on my Duel Boot macine in the next week or so, I'll tell you all how it goes. - Scott]

[http://www.phoronix.com/scan.php?page=article&item=655&num=1](http://www.phoronix.com/scan.php?page=article&item=655&num=1)

---

### Post by Rodneyck on 2007-03-05
Sidux receives a cash reward from distrowatch...

**February 2007 donation: sidux receives US$350**

> We are pleased to announce that the recipient of the DistroWatch.com February 2007 donations is the sidux project (US$350.00).

 Despite being a very young distribution (sidux split from KANOTIX just a few months ago), the overwhelming support among the DistroWatch Weekly readers last week suggests that sidux is on a right track. The project delivered its first stable release, version 2007-01, two weeks ago and it has also published a roadmap promising four stable release per year. It is clear that the idea of developing an installable live CD based on Debian's unstable branch (sid) has been well received in the Debian user community.

[http://distrowatch.com/weekly.php?issue=20070305#donation](http://distrowatch.com/weekly.php?issue=20070305#donation)

---

### Post by mips on 2007-03-05
They need to spend a bit of time on the artwork & fonts, could do with some polishing.

Been on my laptopfor a while now and I like it. I have not been spending much time fiddling or beautifying it as i have been playing with sabayon betas.

---

### Post by Rodneyck on 2007-03-05
> **mips said:**
> They need to spend a bit of time on the artwork & fonts, could do with some polishing.

Been on my laptopfor a while now and I like it. I have not been spending much time fiddling or beautifying it as i have been playing with sabayon betas.

I agree. I am hoping to help out in that department and they have put a call out to create your own wallpaper/icons, etc to be judged and added to the release in April. 

Here are some off the cuff wallpapers I did for them. I came up with these quickly to replace the Mars Nebula theme....  8-[ 

[http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=2149&highlight=](http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=2149&highlight=)

---

### Post by mips on 2007-03-05
> **Rodneyck said:**
> 
Here are some off the cuff wallpapers I did for them. I came up with these quickly to replace the Mars Nebula theme....  8-[ 

[http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=2149&highlight=](http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=2149&highlight=)

I cannot see anything except the last link ?

---

### Post by Rodneyck on 2007-03-05
> **mips said:**
> I cannot see anything except the last link ?

You know, I tried looking at that link with Firefox the other day and did not see anything either. I use Konqueror for my web browser. Maybe it is something that Firefox does not understand. Try another browser if you have it, Evolution or something.  There are several pics, even my proposed logos I did.

Edit... I was told you also have to be logged in to see the pretty pictures. :-)

---

### Post by Kateikyoushi on 2007-03-06
> **mips said:**
> Btw. Feisty is using a newer kernel.

Almost everything I checked is newer in feisty.

---

### Post by Rodneyck on 2007-03-06
That will change here soon when the freeze is lifted due to the upcoming Etch release, probably in the next month, around the same time Feisty is released.

Also, currently, Feisty is beta. Sidux is a stable release.

---

### Post by Kateikyoushi on 2007-03-06
Well feisty is very stable for me, also while after feisty, it will take some time till development start and sidux can leap forward ubuntu testing it will take quite some time till the ubuntu developments trivkle back to deb or sid I assume. Considering the development behind ubuntu I think ubuntu test verions will be more interesting than sidux can be.

The etch freeze effects even sid ? I assumed it does only effect version what are close to make it in the release. I will educate myself about this.

---

### Post by Rodneyck on 2007-03-06
Feisty may be stable for you, but it is still in testing phase and may not be for everyone.

As soon as the freeze lifts the flood gates will open and Sidux will be more updated. For example, I am waiting for KDE 3.5.6 which is very stable, but unfortunately is being held back at the moment for this reason. 

You never really have to upgrade Sidux via a CD/DVD upgrade/release like in Ubuntu, ie no cycles. A apt-get dist-upgrade is your ticket here. Your Feisty may be considered cutting-edge today, but another release will not be out until November (six months), then we will see how cutting-edge it is against Sidux. You could always use the Ubuntu testing releases, but then again, you might as well be using Debian Sid.  Sidux is only held back during these freeze release cycles and only for a few months (depending on how many bug reports are released.)  

Also, I have tried both Feisty and Sidux, and Sidux is much faster.

Edit to add Debian Etch Freeze Info:
[http://lists.debian.org/debian-devel-announce/2006/12/msg00004.html](http://lists.debian.org/debian-devel-announce/2006/12/msg00004.html)

---

### Post by Rodneyck on 2007-03-06
I did not feel like I was explaining it clear enough, so here is a better explanation of why Sidux is not ahead of the game on releases at the moment, chalk it up to bad release timing, yet still remains cutting-edge or will soon.

> "It's not really difficult: sidux IS SID and therefore ahead of all the other popular distros most of the time because you get the most actual versions every single day. There is only one exception to this: when SID is frozen. This happens only when a new Debian Release is coming (which is not THAT often) During this period of time, other Distros can catch up and even bypass sidux taking even newer versions directly from experimental (as you said). But this "advantage" will vanish within one day the moment, Etch is released and all the experimental stuff will drop into SID. From then on, sidux will be bleeding edge again, way ahead of other distros. 
 
 Tragedy is, that sidux has launched just while SID is frozen, so many people who look just at the curent stats can't see, why sidux is top notch."

---

### Post by Kateikyoushi on 2007-03-17
I find it somewhat strange that the freeze effects packages which would take months if not a year to trickle down to the stable repos.
Anyway, could boot it from firewire dvd and plan to install it in 2 weeks then can tell more about it, hopefully they get some people who have some artistic talents, not sure whether the target audiance requires it though.

---

### Post by Rodneyck on 2007-03-18
It was announced that Debian freeze will be unfrozen in about 17 or so days. What apps they can't debug by then, will be left out. So you might want to wait to get all the new updated stuff.

---

### Post by Kateikyoushi on 2007-03-18
Okay I won't bother with it till the packages melt. ;)

---

### Post by igknighted on 2007-03-20
Am using sidux now... this is one slick distro... WOW.  Doing some quick timing I found the time on my system from selecting the OS in grub until the login screen was 21 seconds.  When I enabled auto-login via KDE control panel it took 27 seconds to get to the fully loaded KDE desktop.  By contrast, my Ubuntu install (with a custom built, semi stripped down 2.6.20.1 kernel, but also with beryl) booted in 36 seconds (with auto-login) to a full gnome desktop.  The speed doesn't end here.  Everything is snappy in this distro.  Konqueror opens as soon as I click, as does pretty much everything else.  Overall, the look is quite nice.  As a Sabayon user as well I have grown to love the darker themes, and Sidux has a great one.  The built in script which can handle dist-upgrades, clean the system, and even install video drivers is tremendous.  I forget the name, but I found it to be a great help trimming the system (one of my systems only has a 4gb HD...).

My one complaint is the inclusion of Iceweasel.  I know konqueror doesn't have a lot of plugins, but for a KDE distro as sharp looking as Sidux, the GTK Mozilla clones stick out like a sore thumb.  Either write a FF theme to cover it up, or use a different browser.  Konqueror could certainly be the default, and that wonderful script can install Opera (which is QT based)... there, problem solved.  And the people who still want FF/Iceweasel can download that if they want.

---

### Post by Kateikyoushi on 2007-03-20
Is switching to gnome possible ? I am really not familiar with kde.

---

### Post by igknighted on 2007-03-20
> **Kateikyoushi said:**
> Is switching to gnome possible ? I am really not familiar with kde.

Xfce, fluxbox and a few others are available at install (in addition to KDE... it is definitely a KDE centric distro).  Gnome is not available at install.  Since it just uses Debian Sid repo's, I see no reason why Gnome wouldn't be there to install, however, so you should be able to install it.  You might then have to replace the KDE apps with Gnome replacements however.  I would explore what KDE is like, as Sidux has a great implementation.  If you really want Gnome try installing it, but if it doesn't work really smoothly there's probably a Gnome based distro using Debian Sid.

---

### Post by Kateikyoushi on 2007-03-20
Didn't use KDE for 4-5 years it will be a good chance to see how it matured, just wanted to compare them with the same DE.
I will report back next week about the insane speed how it boots.

---

### Post by Rodneyck on 2007-03-20
You need to read this thread as to why Gnome is not a recommended desktop with Sidux....

[http://sidux.com/PNphpBB2-viewtopic-t-2486-highlight-gnome.html](http://sidux.com/PNphpBB2-viewtopic-t-2486-highlight-gnome.html)

---

### Post by Kateikyoushi on 2007-03-20
Okay I guess I have to do it the other way then. ;)

---

### Post by Rodneyck on 2007-03-21
Great review from a user, always nice to hear...

> ...Sidux is very, really VERY! fast - even on my 7 years old desktop - at least it feels so

[http://tamilinux.wordpress.com/2007/03/21/sidux-2007-01-%ce%a7%ce%ac%ce%bf%cf%82/ ](http://tamilinux.wordpress.com/2007/03/21/sidux-2007-01-%ce%a7%ce%ac%ce%bf%cf%82/ )

---

### Post by igknighted on 2007-03-21
> **Rodneyck said:**
> Great review from a user, always nice to hear...



[http://tamilinux.wordpress.com/2007/03/21/sidux-2007-01-%ce%a7%ce%ac%ce%bf%cf%82/ ](http://tamilinux.wordpress.com/2007/03/21/sidux-2007-01-%ce%a7%ce%ac%ce%bf%cf%82/ )

I was compelled to do a small review in the latest post in my blog as well... see link in my sig.

---

### Post by Rodneyck on 2007-03-21
igknighted, great review and I agree with all of it. 

If you want iceweasel and other non-kde apps to have the same kde look, then there is an app in the repos called "gtk -qt-engine" you can install.

> The GTK-Qt Theme Engine (also known as gtk-qt-engine) is a GTK 2 theme engine that calls Qt to do the actual drawing. This makes your GTK 2 applications look almost like real Qt applications and gives you a more unified desktop experience.
Please note that this package is targeted at KDE users and therefore provides a way to configure it from within KControl.

I don't care for the blocky, M$crosoft 95 look either. :-)

---

### Post by igknighted on 2007-03-21
> **Rodneyck said:**
> igknighted, great review and I agree with all of it. 

If you want iceweasel and other non-kde apps to have the same kde look, then there is an app in the repos called "gtk -qt-engine" you can install.



I don't care for the blocky, M$crosoft 95 look either. :-)

Wow, thanks for the tip.  I'll have to check that out.

---

### Post by fuscia on 2007-03-27
how is sidux different from ubuntu regarding installation and getting stuff working? as an end user, i have no idea how to ask that more specifically. one concern would be my wireless (ipw2915); it works out of the box in ubuntu, but doesn't work with the live sidux cd (i believe i would just need to install the firmware).  i'm sure there's lots of stuff i wouldn't even know existed until it didn't work.

---

### Post by Rodneyck on 2007-03-27
> **fuscia said:**
> how is sidux different from ubuntu regarding installation and getting stuff working? as an end user, i have no idea how to ask that more specifically. one concern would be my wireless (ipw2915); it works out of the box in ubuntu, but doesn't work with the live sidux cd (i believe i would just need to install the firmware).  i'm sure there's lots of stuff i wouldn't even know existed until it didn't work.

For specific installation issues, consult the manual found on the left hand side of the [www.sidux.com](www.sidux.com) menu. It is full of helpful solutions. Also, the forums and IRC (everyone is very helpful) so post specifics in those.

---

### Post by Amorphous_Snake on 2007-04-06
How would sidux run on a PIII 1.2 GHz with 384 MB SDRAM?

---

### Post by igknighted on 2007-04-06
> **Amorphous_Snake said:**
> How would sidux run on a PIII 1.2 GHz with 384 MB SDRAM?

I get boot times of under 30 seconds and instantaneous response from my Athlon 1ghz, 704mb ram.  Not sure how much effect the ram has on boot time, it might affect system responsiveness a little.  I would bet that overall it would still be really quick.

---

### Post by Amorphous_Snake on 2007-04-06
Thanks. I will try it and let you know about the reults.

The thing is that the motherboard only supports 512 MB RAM and it has only 3 slots, each has a 128 MB stick in them. I can't get a 256 MB SDRAM nowadays!

Currently it has Ubuntu 6.10 which boots fast (I didn't time it) but the programs take a bit to load. I hope sidux will be faster.

---

### Post by igknighted on 2007-04-06
> **Amorphous_Snake said:**
> Thanks. I will try it and let you know about the reults.

The thing is that the motherboard only supports 512 MB RAM and it has only 3 slots, each has a 128 MB stick in them. I can't get a 256 MB SDRAM nowadays!

Currently it has Ubuntu 6.10 which boots fast (I didn't time it) but the programs take a bit to load. I hope sidux will be faster.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000170147+1052107967&name=168-Pin++SDRAM](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2000170147+1052107967&name=168-Pin++SDRAM) - if you want some more ram.

---

### Post by Amorphous_Snake on 2007-04-07
Thanks. Actually I don't live in the US and newegg only ships in the US. I could ask a friend to get them for me, though. But they are a little bit expensive for my old PC. Would the extra 128 MB (From 384 to 512) really make a difference? 512 is the top of my motherboard.

---

### Post by Kateikyoushi on 2007-04-07
I am certain sidux uses less ram than ubuntu out of the box but the price for it is the more hand configured hardware and software.
You would get better performance if you run more than one app at a time, but starting apps might be I/O and disc speed related.
Also the FSB os sdram machines is quite important.

I would check used stores or auctions on the net used sdrams are really cheap now.
I have no idea how is it in Cairo but I can find the used 128 MB models for 1USD and 512 MB around 10USD in hard off's.
Whether it worth to buy one or not depends on when you want to upgrade to a newer machine.

I plan to install it next week then can compare the ram usage.

---

### Post by finferflu on 2007-04-07
Wow, I didn't even know there was a Sidux talk here. Good! I'm on it :D

---

### Post by Rodneyck on 2007-04-07
Good news!!!  Etch is releasing this weekend, April 7th or 8th, and that means that Sidux will be flooded with the latest cutting-edge packages from Sid.

> As you may or may not have spotted, we're planning to release Etch 
 this weekend, the 7th/8th April. Yay! The current schedule includes me 
 running the CD and DVD builds during the day on Saturday (UTC), ready 
 for us to release with the archive simultaneously on Sunday 
 morning. 

What does that mean for Sidux?

> That means for us, sid will get many packages from the waiting queue from experimental.
 So please be extremely carefull with dist-upgrades for a while and read the warnings here before upgrading.
 In this situation we cannot guarantee, that we can filter all broken packages fast enough, so best practice is to not dist-upgrade for a couple days, until the dust has settled.

More here..
[http://lists.debian.org/debian-cd/2007/04/msg00005.html](http://lists.debian.org/debian-cd/2007/04/msg00005.html)

[www.sidux.com](www.sidux.com)

---

### Post by mephisto786 on 2007-04-12
"Accidentally" wiped ubuntu and installed Sidux......its blindingly fast........has more apps and a support team that will walk you thru the dangers of Sid.....excellent distro!     Upgraded sid even while the freeze and etch release was in place and the upgrade util scirpts are incredible!   

I cant believe a real Sid distro, more stable than debian sid, heh...the kanotix legacy lives on, and its called sidux

cheers

---

### Post by mips on 2007-04-12
> **mephisto786 said:**
> "Accidentally" wiped ubuntu...


I installed Feisty from the daily builds 3days ago, why I don't know. I don't use sidux btw.

---

### Post by davtaine on 2007-04-13
Yes! Sidux is fast. After short testing i wiped my kubuntu and my linux life is better now .

---

### Post by igknighted on 2007-04-13
> **davtaine said:**
> Yes! Sidux is fast. After short testing i wiped my kubuntu and my linux life is better now .

Be aware that Sidux, since it i based on Deban Sid (see: unstable) can break from time to time.  If this is a machine that you cannot afford to go down randomly (not often, but be aware of the risk) then you may want to consider at least having another distro dual-booted just in case.

That said, welcome aboard.  Sidux is a great distro, I think you will enjoy it.

---

### Post by davtaine on 2007-04-14
Ok, point taken but this Sidux machine is not my only linux PC so no worries. I hope that those horrible breaks dont come often and this main machine stays allways up . I really like this sidux, its fast, applications are new and their community (forum & IRC) is good too. Life is good :D

---

### Post by igknighted on 2007-04-14
> **davtaine said:**
> Ok, point taken but this Sidux machine is not my only linux PC so no worries. I hope that those horrible breaks dont come often and this main machine stays allways up . I really like this sidux, its fast, applications are new and their community (forum & IRC) is good too. Life is good :D

Agreed.  And I should note that after several dist-upgrades I myself have not had any issues, but I wouldn't run it as a sole OS on an important machine, so I thought I'd give fair warning... but you have things well in hand :). Enjoy!

---

### Post by Rodneyck on 2007-04-16
I run Sidux as my only distribution and have for some time now. Not a problem. Others report running Kanotix, which was also based off of Sid, for years without a hitch.

The great thing about Sidux is that the devs watch the repos closely. As long as you update through the wonderful du-fixes script, any broken packages are held back and you are notified of the reason during the process. It is an amazing script and an amazing user/support community. 

[www.sidux.com](www.sidux.com)

---

### Post by livesys on 2007-05-16
New version of sidux has been released May 14, 2007:

sidux 2007-02 preview 1

[http://sidux.com/Article216.html](http://sidux.com/Article216.html)

They did an excellent job with the *"completely overhauled early boot sequence."* because this is the **fastest** booting linux distro that I have tried.

---

### Post by davtaine on 2007-05-17
Sidux is fastest distro on so many levels( at least for me ) and i have tried at least 50 different ones. That du-fixes script is a mother of all scripts :). I have upgraded my kernel (now 2.6.21.1) and i upgrade whole system every day and no problems at all. My main distro in Sidux with KDE and i use Sidux with fluxbox on other machine and those distros flyes. &#932;&#940;&#961;&#964;&#945;&#961;&#959;&#962;...

---

### Post by Rodneyck on 2007-05-22
I swear, it is the best distro out there. With the final release of the next version out soon, it should be very bleeding edge. And of course, it is a "rolling release distro" so members just need to update. 

This from one of the users....

"sidux 2007-02: Kernel 2.6.21.2 (I guess), KDE 3.5.7 and Xorg 1.3 The new fglrx is coming tomorrow or on thursday."

---

### Post by dakini on 2007-05-22
> **Rodneyck said:**
> I swear, it is the best distro out there. With the final release of the next version out soon, it should be very bleeding edge. And of course, it is a "rolling release distro" so members just need to update. 

This from one of the users....

"sidux 2007-02: Kernel 2.6.21.2 (I guess), KDE 3.5.7 and Xorg 1.3 The new fglrx is coming tomorrow or on thursday."

I completely agreee with you.  It's unquestionably the best distro I've used, and the first that I feel downright enthusiastic about.  :p

---

### Post by ThinkBuntu on 2007-05-30
I'm going to give Sidux a try on my separate partition. I had dedicated it to Zenwalk, but after working with openSuSE's KDE for a bit now (and other KDEs) I feel positively crippled in Xfce. Until either (a) Xfce becomes usable, while remaining lighter than GNOME, or (b) Zenwalk begins to rely on another DE, like the GNOME-lite one of their devs is working on, I really can't make much use of Zenwalk, unfortunately. THe 4.6 RC1 even seems a bit slower than 4.4.1. In any case, openSuSE is my standby so I can afford to experiment.

Is Sidux a light distribution by nature? Of course, I'm downloading the KDE-lite version, but once I've built it out (Office, Graphics, Web design, Web development, and more) how much can I expect to use? Granted, I could always use gParted to resize it later...

---

### Post by Rodneyck on 2007-05-31
> **ThinkBuntu said:**
> 

Is Sidux a light distribution by nature? Of course, I'm downloading the KDE-lite version, but once I've built it out (Office, Graphics, Web design, Web development, and more) how much can I expect to use? Granted, I could always use gParted to resize it later...

Sidux is very fast for a KDE desktop OS. As far as being light, well that all depends on the desktop environment and KDE with all its wonder (I love it) comes at a price....bloat, as compared to Xfce, etc. If you compare Sidux KDE with any other KDE distribution, then you will be very happy.

With that said, Sidux-lite is probably your best bet. Yes, you will probably add more apps that will give it more bloat, but at least you will be selecting the ones YOU want.  

I for one love the lite version! Not that many distros out there give you the opportunity to customize the distro to your liking off the bat.  I usually end up going through and removing apps, a nice switch. Even though you can resize your hd later, I would devote as much as you can to Sidux, because I think you will find it to your liking. 

Have fun!

---

### Post by ThinkBuntu on 2007-05-31
> **Rodneyck said:**
> Sidux is very fast for a KDE desktop OS. As far as being light, well that all depends on the desktop environment and KDE with all its wonder (I love it) comes at a price....bloat, as compared to Xfce, etc. If you compare Sidux KDE with any other KDE distribution, then you will be very happy.

With that said, Sidux-lite is probably your best bet. Yes, you will probably add more apps that will give it more bloat, but at least you will be selecting the ones YOU want.  

I for one love the lite version! Not that many distros out there give you the opportunity to customize the distro to your liking off the bat.  I usually end up going through and removing apps, a nice switch. Even though you can resize your hd later, I would devote as much as you can to Sidux, because I think you will find it to your liking. 

Have fun!
Thanks for the info. I'm a former Archer, so how does Sidux differ from and compare with Arch, besides needing a little less manual configuration?

---

### Post by Rodneyck on 2007-05-31
> **ThinkBuntu said:**
> Thanks for the info. I'm a former Archer, so how does Sidux differ from and compare with Arch, besides needing a little less manual configuration?

Sorry, I tried to get Arch installed a couple of times and it was a b*tch!  I gave up. I haven't tried it since the recent update though.

Sidux is Waaaaaay easier to install.  Maybe someone else can compare for you.

---

### Post by ThinkBuntu on 2007-06-01
Arch was a piece of cake for me. They have very simple, clear confg files.

---

### Post by danielph on 2007-06-04
I like Debian and have a lot of respect for the developers. I have just started using Sidux on my old Dell laptop. I am from the Gnome camp and have been using gnome for the last couple of years, but I was so impressed with this distro I think that I maybe jumping ship to KDE. 

The installation picked up all the hardware, suspend worked (which is tricky on old Dell laptops), it picked up rt2500 wireless and was blisteringly quick. Looks nice and latest everything from the deb world. Very impressed.

As for comparisons, I have run etch and arch on the same machine

Etch 
Sidux feels quicker
Sidux detected more of my hardware and made the setup easier
Good scripts for setup and upgrades
Splash is all setup and system looks nice
Everything is bang up to date - SID
It can never be as stable and stable, but as someone else said, I don't need it to run a pacemaker.

Arch - is a closer comparison
Installing Sidux is easier and also easier to get things working quickly
More hardware is detected out of the box
I do like Arch simple structure for example rc.conf and you can get a minimum system up and running very quickly.

---

### Post by FuturePilot on 2007-06-06
How stable is Sidux?

---

### Post by danielph on 2007-06-07
> **FuturePilot said:**
> How stable is Sidux?
They take a snapshot of Debian sid and work on it then release it.It pulls from Debian sid repository, so you could potentially add a buggy package. These are likely to be fixed fairly quickly from what I understand. There is a sidux repository included in the repo's which includes fixes.

I have been running it a couple of weeks and to be honest I was expecting a lot less when I installed it and I was also expecting it to crash a lot more and have loads of problems. It has been rock solid and a pleasure to use and it is very fast.

---

### Post by CocoAUS on 2007-06-07
I ran sidux for a while, as well as participated in their forums.  I've got to tell you, a lot of what sidux does is amazing.  It is hands down the fastest shutdown I've ever seen, and the bootup is fast as well.  The installer is much better than Ubiquity, and there are a lot of scripts to do things like install the latest nvidia driver.

However, the community is rather poor.  They are very condescending and elitist.  Their way is not only the best way, but they make it the only way.  They'll tell you you can do what you want, but really what they're saying is, "You're stupid."  Sidux uses hd* instead of sd*, sux instead of su or sudo (they think sudo is evil), talk about Gnome like it's absolutely horrible and refuse to support it at all, etc.  There is no polish whatsoever.  Things are full of misspellings, poor grammar, and half-assed implementations of otherwise great ideas.  It smacks of German and elitist flavor (redundant?).  Even the colors are red and black.  The forum members are jerks and the developers brush off questions or bugs as though the user is clueless about what he's doing.  I even got two different answers from two different developers, and each completely ignored what the other said as though it wasn't even worth their time to consider it.

I imagine that sounds pretty harsh, but it's all quite legitimate.  sidux has done some great things (speed, scripts), but as great as those things are, they're really almost irrelevant.  You'd probably do better just using a live Debian cd (Sid isn't available right now, but should be soon).  You could also check out DSL or GRML.

---

### Post by Rodneyck on 2007-06-08
I disagree wholeheartedly with your comments regarding Sidux support. All one has to do is read through forum to quickly realize that your comments are nothing but a fallacy. 

In all my questions posted on the Ubuntu forum and others, not once has a dev ever replied. User and dev support is quite common on Sidux, simply the best.

With that said, not every distro is suitable for all users.  Good luck with finding yours.

---

### Post by CocoAUS on 2007-06-08
Uh, your comment is 1) demonstrably false, and 2) irrelevant.

I didn't say devs didn't offer sidux support.  In fact, I pointed out that they do.  But it's quite condescending, elitist, and leads to a horrible overall experience.

---

### Post by ThinkBuntu on 2007-06-08
> **CocoAUS said:**
> Uh, your comment is 1) demonstrably false, and 2) irrelevant.

I didn't say devs didn't offer sidux support.  In fact, I pointed out that they do.  But it's quite condescending, elitist, and leads to a horrible overall experience.
How does Sidux support differ from Debian support? Just post your questions at forums.debian.net. Very good people there.

---

### Post by sw1995 on 2007-06-28
I tried out the Sidux live cd earlier today and I have to say that I loved it--as a relative newcomer to Linux I'm still a bit too timid to install it but I'd have to say that this is the first distro that I have used that may entice me to switch over to KDE. I can't say why, it's just one of those things. I am trying to get a debian live cd to work; perhaps I will find it less intimidating.

\m/

---

### Post by MethodOne on 2007-06-28
After using sidux for a while, I had a problem with libcurl3-gnutls and libcurl4 conflicting.  For example, when I try to install xine-ui or git-core, which depend on libcurl3-gnutls, it removes Amarok, OpenOffice.org, Grip, and other applications that depend on libcurl4.

---

### Post by sw1995 on 2007-08-14
Anybody try out the new Sidux live cd? I loved the last one however unfortunately had some problems so had to put it on hold; I am however really excited to try this out!!!

-S

---

### Post by wvmac on 2007-08-16
I installed the new version. It's so fast.  I had been running feisty for a while and it had started getting buggy with all the packages I had installed. I was planning on starting over and then I saw the sidux release.  I had never used it before but I really like it.  the smxi script is amazing.  Hardware detection was on par with feisty for my system.  I accidently installed the x86-64 version first. It was really fast, even faster then the x86 version.  But I wanted all the codecs so I installed the x86 version.  They are seperate cd's so watch out which one you download.  It is a good distro so far. Time will tell.

---

### Post by Engnome on 2007-09-04
Installed it a week ago and love it! I'm in love. Lite version ftw! :KS I now use KDE instead of GNOME as the bloat feeling of other KDE versions I've tried is just gone. This had the unintentional side effect of me being very excited over KDE4 all of a sudden. Wonder how it'll be upgrading...

First I got the impression that it was just an installer for Debian Sid but I's a little bit more than that. Although if people ask I usually say I'm using Debian Sid. I'm not sure if it's really a new distro. To me making a new distro means making something different and new but Sidux is proud to be 100% Debian... or at least Debian compatible. I don't know. Does it matter?

---

### Post by Antman on 2007-09-17
So far I love Sidux on my laptop. I will soon be switching my WinXP Desktop over too (probably a dual boot).

And yes it is pretty darn fast... heck the install on my laptop only took 7 minutes... :lolflag: 

Also the scripts are very awesome and help out a lot; really makes upgrading kernels, video drivers, etc. a cake. 

And I love the fact that I am running bleeding edge rolling release distro (install once and just dist-upgrade via the smxi script). In fact xorg 7.3 just hit the unstable repos... I'm going to wait until I here that all is well with ATI drivers before I upgrade though.

Hmmm....

---

### Post by wilberfan on 2007-09-20
I must confess I've become a really big fan of Sidux...   In fact, I'm using it about 95% of the time now...   Ubuntu is still my go-to, standby distro--but Feisty is working *so well*, it's gotten kind of boring for me!  :)

The only thing I miss in Sidux is gnome.  Well, that and the fact that if you install the 64-bit version and try and get any help in the #sidux irc channel, you will officially be torn several new ones...  :lolflag:  (But, having said that--fairness dictates that I mention that they're all quite friendly and helpful in there...Just be prepared to justify your reasons for having installed the 64-bit version!  I chickened-out and stuck to the 32-bit!)

Still, it took, like, *10 minutes* to install, boots really quickly--and their "smxi" script is just a *wonderment!*   Seriously...:guitar:

Bravo!

---

### Post by danielph on 2007-09-21
> **wilberfan said:**
> The only thing I miss in Sidux is gnome.I have gnome running under Sidux and have not seen any problems. Of course your dist-upgrades will be a little longer and support is primarily for KDE. I agree with the upgrade scripts, easy to use and very solid. They did some good work on this and it is the only dist that really works with this laptop (Dell 8500).

---

### Post by Antman on 2007-09-26
Just put Sidux on my desktop too. Running xOrg7.3 on dual screen 17" flatpanels. :guitar:
I still have WinXP on another partition since I still need to play some games and do some video editing (Adobe Premier).

```
Host/Kernel/OS  "mine" running Linux 2.6.22.7-slh-smp-1 i686 [ sidux 2007-03.1 - &#915;&#945;&#953;&#945; - kde-full - (200708151444) ]
CPU Info        (1) Intel Pentium D clocked at [ 2992.753 MHz ]
                (2) Intel Pentium D clocked at [ 2992.753 MHz ]
Videocard       nVidia NV41.1 [GeForce 6800]  X.Org 1.4.0  [ 1280x1024 @50hz ]
Processes 121 | Uptime 6:04 | Memory 316.9/2026.1MB | HDD Size 570GB (59%used) | GLX Renderer GeForce 6800/PCI/SSE2 | GLX Version 2.1.1 NVIDIA 100.14.19 | Client Shell | Infobash v2.67

```

---

### Post by davtaine on 2007-10-16
Is it me or is this new KDE 3.5.8 a lot faster (than 3.5.7)? it definitely feels "faster" :)

---

### Post by mthei on 2007-10-16
I don't know if Sidux leaves out some things that Kubuntu, Knoppix, and a certain other distro whose name I dare not speak on these boards include by default, but this is by far the fastest I've seen KDE go on a live CD. If things don't work out between Gutsy and me, then I'm moving in with Sidux.
My monitor's pretty old, and so far Sidux is the only liveCD that's properly detected it as well as give me a decent resolution by default. Even Knoppix didn't get it right. The only thing keeping me from installing it is the fact that I have to get used to using KDE on a regular basis, and I'd like to look into file managers that aren't konqueror, as I don't really like it as a file or web browser.

---

### Post by danielph on 2007-10-17
Since I can remember Debian has always been quick and Sidux inherits this and maybe improves on it. Not sure if new KDE is quicker but I know the distro is. There are plenty file managers to choose from and or other Desktop environments too. I use XFCE4 and Thunar is a good file manager. If you want integration with KDE then its konqueror, which is a very good file manager btw.

---

### Post by greymongrey on 2007-10-17
> **davtaine said:**
> Is it me or is this new KDE 3.5.8 a lot faster (than 3.5.7)? it definitely feels "faster" :)
It seems faster to me as well.

---

### Post by angryfirelord on 2007-10-17
> **davtaine said:**
> Is it me or is this new KDE 3.5.8 a lot faster (than 3.5.7)? it definitely feels "faster" :)
What?! KDE is fast?! The world is falling apart! 

But yes, I've noticed this too. :)

---

### Post by b9anders on 2007-10-18
I am using sidux at the moment for a few reasons:

A it's debian through and through, with all the wonders of package management and solid desaign that comes with it
B I want a goodlooking distro
C I want a fast distro

I recently left behind zenwalk because of A and B (package system isn't very good there and no compiz fusion), OpenSuSE over C. Sidux has it all. With that kind of speed on KDE, there's really no need for xfce. It's feels as fast as Zenwalk and KDE, in addition to being a more fullfledged DE, also manages heavy-multitasking much better than gnome or xfce in terms of RAM.

Am very happy with it at the moment. When I ran debian sid on my own, I inevitably ended up breaking my system. Sidux manages things well for me so far. I really like their rolling release implementation. Also, it's very nice to be able to install a kde-lite version and then just add in the few programs I require. Makes for a well trimmed and managed system.

---

### Post by Antman on 2007-10-18
> **b9anders said:**
> I am using sidux at the moment for a few reasons:
C I want a fast distro

Yes, it's pretty darn fast. It's actually faster then all other distros I have tried so far.

> **b9anders said:**
> 
lso, it's very nice to be able to install a kde-lite version and then just add in the few programs I require. Makes for a well trimmed and managed system.

I haven't tried the lite version yet. Maybe i'll install it on my older sub-notebook that is currently running Puppy and AntiX. :guitar:

---

### Post by greymongrey on 2007-10-25
No doubt, Sidux rocks. It's the fast OS I've run to date. I was always afraid of Sid but so far so good.

---

### Post by wilberfan on 2007-10-27
Just had to drop by again and {giggle} over how much I love my Sidux!    I can never get over how cool it is to get the latest kernels (and everything else) with that amazing little "smxi" script!

:)

:guitar:

---

### Post by dralaroc on 2007-10-28
> **wilberfan said:**
> Just had to drop by again and {giggle} over how much I love my Sidux!    I can never get over how cool it is to get the latest kernels (and everything else) with that amazing little "smxi" script!

:)

:guitar:

+1...I have been using Sidux for two weeks now, definitely rocks!   Funny thing also, KDE is starting to grow on me abit :)

---

### Post by Caffeine_Junky on 2007-10-29
hello fellow Sidux users!

Yeah Sidux is a nice distro', ...I am running  ISO Version: 2007-03.1-200708151444-gaia-KDE Full, ...and I must say it is a sweet deal :)

I have only had it installed for 2'days and it is working great, no problems at all.   

In the past I have run Etch with both Gnome & KDE (costom installs/minimal) so I know my way around debian and have always liked the feel of it...

I have been spending a small amount of time reading the forums at Sidux.com (don't want to overload myself :) ) and I have noticed that there is a "maintenance script' called " smxi ",  ...I was wondering if you peep's are using this script?,  ...is it working well for you?

My needs on the PC are simple, I just listen to music and surf the net pretty much (yes I am a distro' junky :p ) ..and my Sidux is working nicely ...so I am in two minds whether I should run the " smxi script " or not?

I would be interested to hear your experiences with the smxi script concerning dist-upgrades and system maintenance in general, ..or do you even use said script at all?


cheers

Ash

---

### Post by danielph on 2007-10-29
> **Caffeine_Junky said:**
> 

I would be interested to hear your experiences with the smxi script concerning dist-upgrades and system maintenance in general, ..or do you even use said script at all?


cheers

Ash
It is the best way to keep your system up to date. I use it about once a week. Keep an eye on the warning messages. Sometimes it is not safe to dist-upgrade, for example when the latest xorg recently hit sid, but it stated clearly that it was better to wait a bit. I have had no problems since using sidux or the script, except the odd X issue. I have been running sidux for around 4 months.

---

### Post by Antman on 2007-10-29
> **Caffeine_Junky said:**
> 
I have only had it installed for 2'days and it is working great, no problems at all.   


Well, even though I love Sidux, I can't say that it isn't without some problems, but I guess all distros aren't 100% perfect.

> I would be interested to hear your experiences with the smxi script concerning dist-upgrades and system maintenance in general, ..or do you even use said script at all?

The smxi script is just plain awesome. It is the bread and butter of sidux. If you don't use it, you will no doubt have more issues since H2 and the team spend time putting some tricky Sid packages on hold in order to avoid breakage. It also allows you to EASILY upgrade your kernel and other things.

---

### Post by wilberfan on 2007-10-29
> **Caffeine_Junky said:**
> I have been spending a small amount of time reading the forums at Sidux.com (don't want to overload myself :) ) and I have noticed that there is a "maintenance script' called " smxi ",  ...I was wondering if you peep's are using this script?,  ...is it working well for you?

My needs on the PC are simple, I just listen to music and surf the net pretty much (yes I am a distro' junky :p ) ..and my Sidux is working nicely ...so I am in two minds whether I should run the " smxi script " or not?

I would be interested to hear your experiences with the smxi script concerning dist-upgrades and system maintenance in general, ..or do you even use said script at all?

smxi is hands-down my favorite part of Sidux!!!   You may be a 'distro junky'--but I am a 'update whore'!   And smxi keep EVERYTHING brand-spanky-new with very little effort (read back through this thread to see my enthusiasm!)!

I've never had anything get messed-up using the script--and I must say that whenever I've gotten stuck in Sidux, there are some very helpful folks (including the guy who wrote the smxi script) in the #sidux IRC channel. 

I think the only thing I miss in SIdux (I may have mentioned these earlier in this thread) is the lack of gnome (unsupported--but you *could* install it)--and the fact that the 64-bit version isn't as fully integrated as in Ubuntu (It's still a fairly young distro--they'll get there?).

---

### Post by Antman on 2007-10-29
Alright... time to play again. :guitar:

See details here:
[http://distrowatch.com/table.php?distribution=sidux]("http://distrowatch.com/table.php?distribution=sidux")

---

### Post by seshomaru samma on 2007-10-30
WOW. I just installed Sidux in 9 minutes!

I was looking for a fast alternative for Ubuntu which was running on my old laptop. I heard Sidux was fast , but 9 minutes ...!

---

### Post by Antman on 2007-10-30
> **seshomaru samma said:**
> WOW. I just installed Sidux in 9 minutes!

I was looking for a fast alternative for Ubuntu which was running on my old laptop. I heard Sidux was fast , but 9 minutes ...!

:lolflag: yeah, Sidux makes most current distros feel like they are running under water.

The KDE lite version (preview 1) installed on my laptop in under 6 minutes...but this **doesn't** include OpenOffice. weird thing is, the full version of Gaia (with Openoffice) installed in under 8 minutes :guitar:

---

### Post by greymongrey on 2007-10-30
Gaia full installed in 6 minutes for me.

---

### Post by davtaine on 2007-10-30
> **Antman said:**
> :lolflag: yeah, Sidux makes most current distros feel like they are running under water.

True words my friend :) Sidux is a piece of true art. I have been using it over seven months and no problems of any kind.  I'm just waiting when those official KDE4 packages are coming to repos.

---

### Post by mindtrick on 2007-10-30
Downloading the preview 1 KDE-lite. It's the fastest distro I've ever seen.

---

### Post by Antman on 2007-10-30
> **mindtrick said:**
> Downloading the preview 1 KDE-lite. It's the fastest distro I've ever seen.

Debian at its best... :guitar:

---

### Post by anticapitalista on 2007-10-31
Sidux is definitely the fastest KDE distro out there. Actually antiX installed faster than sidux-Tartarus-lite on my box, using the fromiso install. 
(Installing antiX from booting livecd fromiso to desktop in installed antiX took about 6 minutes on an AMD 2000 with 512MB RAM and a lot of that was me typing in information such as user name passwords etc)

But I really like sidux and would agree with others here about the smxi script. It has even saved my butt a few times on antiX and Mepis 3.4.3.

---

### Post by angryfirelord on 2007-10-31
[QUOTE=anticapitalista]Actually antiX installed faster than sidux-Tartarus-lite on my box, using the fromiso install. [/QUOTE]
Show-off. :lolflag:

---

### Post by anticapitalista on 2007-10-31
> **angryfirelord said:**
> Show-off. :lolflag:

Yeah I know :lolflag:

---

### Post by Caffeine_Junky on 2007-11-01
OOO-pretty!, ...there be a new colour-scheme:

[http://sidux.com/module-PNphpBB2.html](http://sidux.com/module-PNphpBB2.html)

I found the previous one too be easier on the eyes, but this one is good too *rubs eyes*

[COLOR="Blue"]Update:[/COLOR] The RED+Black Look must have been a test, ..I notice now they have returned to the original colour scheme

---

### Post by mthei on 2007-11-21
2007-4 was officially released today!
Thankfully the day after I bought a bunch of DVD-Rs. Downloading the torrent now from LinuxTracker. Can't wait to give it a spin.

---

### Post by b9anders on 2007-11-22
I am using it now. The artwork is fantastic. Love the seamless integration between kdm and the fully loaded desktop. very smooth.

---

### Post by mthei on 2007-11-23
While I have very few complaints about the previous version, this one improves a lot. The only thing that's really bothering me is that in IceWeasel, every word I've typed so far are being noted as spelling errors. Unlike the previous Sidux, where I was automatically given a resolution of 1024 x 768, which even though it's a very acceptable resolution I would have been happy to live with, the refresh rates were poor (my computer is only one year old, but I've had this monitor for at least six years, and came from my fathers old office after they had upgraded all their computers). This time I've been logged in with a comfortable 1280 x 1024 and a 60hz refresh rate.
All other hardware is being perfectly detected, although if I change the language to Canadian English, my keyboard (which is biligual), doesn't respond as well.
Only complaint: If I were to install this, there are so many programs I'd never use, I`d have to remove a lot.
Still, kudos to the Sidux team for turning out another solid, polished release.

---

### Post by Antman on 2007-11-23
> **mthei said:**
> The only thing that's really bothering me is that in IceWeasel, every word I've typed so far are being noted as spelling errors. 
Sidux's Iceweasel spellchecker is defaulted to de_DE. Just right click a misspelled word and select "languages" > then pick your language of choice.
:)

---

### Post by dptxp on 2007-12-06
I am finding it hard to download Sidux using torrent (from linuxtracker.org). The 64 bit one. Have got 51 MB in 3 days. 
I tried some other torrent too. Hardly any seeders.

Any suggestions ?

---

### Post by Antman on 2007-12-09
> **dptxp said:**
> I am finding it hard to download Sidux using torrent (from linuxtracker.org). The 64 bit one. Have got 51 MB in 3 days. 
I tried some other torrent too. Hardly any seeders.

Any suggestions ?

Yes, try here for the 64 bit ISO:
[64 Bit EROS Iso]("http://lug01.eecs.wsu.edu/sidux/release/sidux64-2007-04-200711210257-eros-kde-full.iso")
:guitar:

---

### Post by angryfirelord on 2007-12-09
> **dptxp said:**
> I am finding it hard to download Sidux using torrent (from linuxtracker.org). The 64 bit one. Have got 51 MB in 3 days. 
I tried some other torrent too. Hardly any seeders.

Any suggestions ?
Yeah, linuxtracker is horrible, hardly any seeders and faulty connections no matter what torrent I use (of course, that's what you get for running Windows Server :wink wink: :)). In this case, downloading via ftp or http is a better choice.

---

### Post by dptxp on 2008-01-07
Sidux installation is fast, the Lite i386 version took just 7 minutes to install after the steps. 

Boots and runs fast too. And it has dynamic CPU frequency scaling enabled. I expect it to be kind on battery.

The only problem is that they have no package manager, and I do not think that they shall put in one. Good for learning but tedious. So UBUNTU stays for serious work.

---

### Post by davtaine on 2008-01-07
> **dptxp said:**
> The only problem is that they have no package manager, and I do not think that they shall put in one.

apt-get install kpackage

---

### Post by dptxp on 2008-01-10
> **davtaine said:**
> apt-get install kpackage

Thanks.
What repositories (or packages) shall I be able to access ?
BTW Can I use Gnome with Sidux ? If yes, How ?

---

### Post by notwen on 2008-01-10
> BTW Can I use Gnome with Sidux ? If yes, How ?

You can install it by installing the norm gnome package through apt-get, but it is not recommended.  sidux does not support any gnome related issues, lots of sidux users tend to use the default KDE, even have a good bit who use xfce.  sid itself tends to have issues w/ GNOME.  What are you after by using gnome? KDE should support all of your GTK++ apps.  If you do install GNOME, be prepared for breakage come every dist-upgrade.  Be sure to post back should you play w/ GNOME on sidux.  I used sidux for a while to run a ftp/nfs/web server on, but fell back to Etch running flux/xfce.

---

### Post by anticapitalista on 2008-01-10
dptxp,

sidux doesn't advise upgrading/installing through kpackage/synaptic either.
They advise a regular dist-upgrade only through apt (no aptitude either) in unit 3.
sidux has its own repos, but it really utilises the debian sid ones (testing/Lenny is not advised).
Once you get used to their conception, sidux is fantastic. The devs really do give you a rolling release debian sid that is 99.9% 'tamed' for 99% of the time.

Apparently, gnome in debian sid is the problem (not Lenny). It is not well prepared (so they say).

I'll finish by pimping my distro, antiX.
There is an antiX-M7.01-base.iso (178 MB) which comes with very
few apps, it uses the debian Lenny and Etch repos, has fluxbox wm, but ant desktop environment should be easy to install. Think of it as a way to build your own distro.

My sig. leads to a link if you are interested.

---

### Post by dptxp on 2008-01-11
> **notwen said:**
> You can install it by installing the norm gnome package through apt-get, but it is not recommended.  sidux does not support any gnome related issues, lots of sidux users tend to use the default KDE, even have a good bit who use xfce.  sid itself tends to have issues w/ GNOME.  What are you after by using gnome? KDE should support all of your GTK++ apps.  If you do install GNOME, be prepared for breakage come every dist-upgrade.  Be sure to post back should you play w/ GNOME on sidux.  I used sidux for a while to run a ftp/nfs/web server on, but fell back to Etch running flux/xfce.

> **anticapitalista said:**
> dptxp,

sidux doesn't advise upgrading/installing through kpackage/synaptic either.
They advise a regular dist-upgrade only through apt (no aptitude either) in unit 3.
sidux has its own repos, but it really utilises the debian sid ones (testing/Lenny is not advised).
Once you get used to their conception, sidux is fantastic. The devs really do give you a rolling release debian sid that is 99.9% 'tamed' for 99% of the time.

Apparently, gnome in debian sid is the problem (not Lenny). It is not well prepared (so they say).

I'll finish by pimping my distro, antiX.
There is an antiX-M7.01-base.iso (178 MB) which comes with very
few apps, it uses the debian Lenny and Etch repos, has fluxbox wm, but ant desktop environment should be easy to install. Think of it as a way to build your own distro.

My sig. leads to a link if you are interested.

Thanks both.

I had done a bit of reading before going in for Sidux, I do not just go and install any Linux though I may try Live. Sidux has very extensive and elaborate documentation, wish Ubuntu had something similar. KDE is fine with me, I run Ubuntu (Gnome) on desktop, so I can get familiar with KDE now. Since Sidux default colors are different, I like the default KDE look in it. 

Anti-X can surely be worth a try. In general I want to settle for those one or two distros for installation which are reasonably stable, have reasonable support, are not bloated, are fast (no fluxbox or XFCE for me, never could like them) with fast boot time and can give good battery life on Laptop. Should detect all my hardware. And Debian.

For I need to do serious work too including programming in Linux.

BTW how do I get to unit 3 (have to learn about units too) ? I think that I see options unit 5 and unit 1 on boot. Shall recheck.

---

### Post by anticapitalista on 2008-01-12
If you are going serious with sidux, read their excellent manual and use the smxi script.

My typo in my previous post. It should be init 3 , not unit 3.

---

### Post by dptxp on 2008-01-13
> **anticapitalista said:**
> If you are going serious with sidux, read their excellent manual and use the smxi script.

My typo in my previous post. It should be init 3 , not unit 3.

I also typed unit , I do not understand init  but i know it is init, not unit. Lot to learn.
Yes, I am going to use the SMXI script.

---

### Post by dptxp on 2008-01-13
I am unable to get to init3. Pressed Ctrl+Alt+F1 to get into console. But when I type init3 it says command not found. tried as root too, did not work. Sidux site is not working. Wanted to upgrade, have installed sidux-scripts.

---

### Post by Antman on 2008-01-13
> **dptxp said:**
> I am unable to get to init3. Pressed Ctrl+Alt+F1 to get into console. But when I type init3 it says command not found. tried as root too, did not work. Sidux site is not working. Wanted to upgrade, have installed sidux-scripts.

```
init 3
```

there is a space after init

---

### Post by Antman on 2008-01-13
*** duplicate post ***

---

### Post by dptxp on 2008-01-13
> **Antman said:**
> ```
init 3
```

there is a space after init

Thanks. Command line operations are like writing in Assembly Level Language, one character mistake and everything changes.

---

