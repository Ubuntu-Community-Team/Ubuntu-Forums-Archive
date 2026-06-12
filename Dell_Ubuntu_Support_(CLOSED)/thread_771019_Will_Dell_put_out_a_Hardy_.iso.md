---
title: "Will Dell put out a Hardy .iso?"
date: 2008-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by WBL on 2008-04-27
I have a Dell Insprion 1525N from Dell.  Everything was working perfectly when Dell shipped it to me.  I ugraded to Hardy, and now I have problems-no sound (at all!) and no DVD playback.  I tried the fix to sound on the Dell Wiki site, but it didn't work.  

Will Dell release a Hardy .iso so my system will work again?  It's very frustrating having a brand-new laptop that doesn't work properly.  :mad:

-WBL

---

### Post by notwen on 2008-04-27
I don't see why they wouldn't.  If I had to guess, I would geuss Dell will have a custom Hardy image out within a month.  Feisty's custom image came out a a little over a month after Dell began offering their N-Series machines.  Gutsy's custom image followed just 3 weeks after Gutsy's official release.  Give Dell time to test Hardy on their production machines and work out the kinks.  I am also looking forward to a custom image for my Inspiron 1420n.  =]

---

### Post by enchantedsky on 2008-04-27
In my opinion, Dell does not care about its customers. They will not put out a Hardy .iso to run Ubuntu on your Dell hardware. The only reason why started selling Linux machines on their computers was to appeal to a niche market.

Dell does not even go out of its way to make Linux drivers ----- my sister in law had to remove Ubuntu on her Dell and install Windows XP because her Dell Printer A920 only had Windows drivers made by Dell. 

Anyway, please post your problems, and let's get them fixed! The DVD problems are likely caused by Dell's Linux DVD player being incompatible with 8.04, so you have to google up "medibuntu" and install DVD software manually. Also, they changed the sound system in 8.04 to "pulse", and there are ways to remove this software (just do a search on this forum) Slowly, but surely, everything will work again

---

### Post by LMP900 on 2008-04-27
> **enchantedsky said:**
> In my opinion, Dell does not care about its customers. They will not put out a Hardy .iso to run Ubuntu on your Dell hardware.

I'm just wondering; what makes you so sure they're not going to do it for Ubuntu 8.04 when they've provided a custom image for every release since they've offered N-versions of their products?

---

### Post by grenet on 2008-04-27
I can't believe there is anything but love for the Dell Ubuntu team.  Not only is there a direct dell Ubuntu Technical Service number: 866 622 1947, but they also provide a Dell wiki with custom iso's.

Dell has done nothing but impress me with their support for Ubuntu.  Ubuntu is a niche market used mostly by techs, so if you, or your sister cannot find the right driver for a certain printer, the Ubuntu forums would offer you support in a couple hours I would guess.

The Dell Hardy iso will be out soon.

---

### Post by LibertyShadow on 2008-04-28
> **enchantedsky said:**
> 
Dell does not even go out of its way to make Linux drivers ----- my sister in law had to remove Ubuntu on her Dell and install Windows XP because her Dell Printer A920 only had Windows drivers made by Dell. 


Take a look here: [http://www.openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920]("http://www.openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920")  OpenPrinting says this printer works "Perfectly." Good luck!

---

### Post by Jammin80503 on 2008-04-28
Give it a while, and if they don't put one out, just post your problems in the support section. We have plenty of really smart people here :P

---

### Post by notwen on 2008-04-28
> In my opinion, Dell does not care about its customers. They will not put out a Hardy .iso to run Ubuntu on your Dell hardware. The only reason why started selling Linux machines on their computers was to appeal to a niche market.

Let's try and keep this support forum opinion free.  =]  If you wish to bash Dell and their support for Linux of lack there of, please do so in the [appropriate place]("http://ubuntuforums.org/forumdisplay.php?f=103").

I have no doubt in my mind Dell will eventually get a custom Hardy image out for the supported N-Series models.  Just have patience and let them work out any new issues introduced w/ Hardy and it's new packages/kernel.

---

### Post by drsaamah on 2008-04-28
Honestly... I'm not too impressed by the Dell Ubuntu iso's.  Unlike some of the above, I think Dell's intentions with the N-series computers are nothing but good, HOWEVER, the Dell iso's are really just Ubuntu + stuff that the open-source community already figured out themselves.  I would search the forums and/or google the problems you're having.  The DVD playback is most likely related to the region settings.  Have you looked into 'regionset'?  As for sound, what kind of sound card do you have?  I have the intel sound card that I believe comes standard with most Dell's and mine works perfectly with Hardy.
Put simply, give US your problems and we'll work to solve it.  The open-source community is great with figuring out stuff and we tend to do it faster than Dell or any other company :)

---

### Post by NineKnuckles on 2008-04-28
Hey WBL, try doing the Dell workaround a second time, it worked for me - not sure why.  The only reason I tried a second time is because I wanted to make sure I pasted the right info into the terminal.  Also make sure your sound isn't just very low.  I added a sound applet thing to my top panel (I usually just use the physical buttons on my laptop, and have no need for the applet) to access sound setting to fix the problem and kept getting errors. I didn't realise the repeated workaround worked for about 10 minutes untill I glanced at the panel and saw the sound icon unmuted.  Like I said earlier tho - the sound was very low, almost silent and I thought the workaround definately didn't work for me, but I remembered people posting about low sound output, so set everything to max (from 75% - which was very quiet for some reason?) and it worked.  I've got no idea why this didn't work the first time round but the second time was the charm for me.

---

### Post by Nico0020 on 2008-04-29
Are these custom dell images only for the N series?  I bought my Dell Inspiron E1505 about 2 years ago, and was thinking about trying these on a separate partition.

---

### Post by fragos on 2008-04-29
From what I can see the only difference with the "n" series is that optional hardware that isn't supported well in Linux isn't offered.

---

### Post by pormogo on 2008-04-29
Just wondering does dell post packages normally installed in their DVDs on the launchpad repository. I checked in my sources.list file and found an extra "dell team" repository 

[i]deb [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main
[/i]

Originally these where commented out when I upgraded since the version was set to gutsy. However I checked and there is a section for hardy there as well but there does not appear to be anything in it. I was wondering what these package repositories where for?

---

### Post by fragos on 2008-04-30
Dell has put a lot of effort into Ubuntu on their hardware. I doubt that will stop. I believe there will be an 8.04 release from Dell. Undoubtedly, changes to open source made by Dell will and have been integrated into the distrobution we all run. Dell licenses a DVD player that isn't open or free. Items like that have to be integrated by Dell.

---

### Post by niteshifter on 2008-04-30
I believe Dell is committed to Linux on the desktop. See this article:

[http://linux-foundation.org/weblogs/press/2008/04/24/linux-foundation-reports-highlights-from-annual-collaboration-summit/]("http://linux-foundation.org/weblogs/press/2008/04/24/linux-foundation-reports-highlights-from-annual-collaboration-summit/")

Would be nice if Dell would give a hint ... or update the wiki :o

---

### Post by WorldTripping on 2008-05-01
According tho Dell:

[http://www.ideastorm.com/article/show/10086436/Provide_ubuntus_next_LTS_iso_100_compatible_with_Dell]("http://www.ideastorm.com/article/show/10086436/Provide_ubuntus_next_LTS_iso_100_compatible_with_Dell")

> Dell's Linux engineers are working very closely with the Ubuntu developers to ensure the systems we sell will work "out of the box" with Ubuntu 8.04. The customization is happening in the release itself, not after the fact. 

Ubuntu also has a large list of mirror servers around the globe, many with faster network connections than Dell could easily offer. If Dell releases an Ubuntu CD, modified in some way to make installation easier on our systems, we'll post them on linux.dell.com as we always have. 

---

### Post by fragos on 2008-05-01
> **WorldTripping said:**
> According tho Dell:

[http://www.ideastorm.com/article/show/10086436/Provide_ubuntus_next_LTS_iso_100_compatible_with_Dell]("http://www.ideastorm.com/article/show/10086436/Provide_ubuntus_next_LTS_iso_100_compatible_with_Dell")

This is the ideal way for Dell to provide Ubuntu support. They become well integrated into the development community and fully use rather than duplicate the Ubuntu upgrade path. Continuing to ship pre-installed Unbuntu everybody wins.

---

### Post by aidave on 2008-05-01
Dell is probably just overburdened with politics and bureacracy.  I think they are going the right direction though, and am glad they offer an Ubuntu laptop.  I bought a 1420n and it actually did not work properly with Gutsy, even preinstalled.  I was really upset actually.  But Hardy is out and it has solved all (well almost all) of the bugs that annoyed me.  

Like suspend/resume actually works now, but there are still some glitches.  And every 1/20 times or so it reboots.

---

### Post by grenet on 2008-05-02
you will need to download the Dell iso for 7.10 Gutsy, and reinstall it.  Then wait for the Dell Hardy iso, which should be out soon.  I have no idea when though. 

You could go through and solve all your issues yourself, but that would take a bunch of work, and it's probably easier to use the Gutsy iso.

---

### Post by RedRat on 2008-05-04
I must admit that I have found my 530n did upgrade to 8.04 with some glitches but I was upgrading 7.10 vanilla--not Dell's version. Another comment that appeared here concerning the SATA and Raid setup should clear up the problem. I did get my 8.04 working and am very pleased with it. 

While for years I was not a fan of Dell, I have certainly come around with their Linux machines. The combination of Ubuntu and Dell have produced a machine that simply works. So far, I have found that 8.04 seems a bit faster and it certainly is much, much better when I want to attach to my Windows XP machine with the NTFS file system. This is a far cry from 7.10, which seemed to have difficulties. A big Cheer to the 8.04 team. So far, knock on wood that the good news will continue.

The two comments that are critical of Dell in regard to Linux I think are really off base. I have certainly not seen any indication that "Dell does not care about its Linux users". I think these two bloggers have engaged in a bit of hyperbole.

---

### Post by FrankVdb on 2008-05-05
I bought my M1330 last year when it wasn't bundled with Ubuntu yet.
Dell offered other laptops with Ubuntu but not that one. At first, I wouldn't believe the Dell lady from the Netherlands telling me that they hadn't tested Linux on the M1330 yet, so they didn't want to put it out until tested. Later on, I became convinced that Dell was serious about Linux.

Of course, they're in for the money, let's be clear about it.
But if money can be made with desktop Linux systems, it will open up a new world of companies writing their own Linux drivers and  software.

So without being a die-hard Dell fan: kudos to Dell for jumping into the cold water.

With Vista, the M1330 s*cks. With Ubuntu, it just rocks.

---

### Post by Orion2000za on 2008-05-05
this is an emai to Dells Linux mailing list and for all I understand it means the dell-iso of Hardy is being worked on:

"I would recommend waiting a few days to upgrade to Ubuntu 8.04. When you upgrade, you may have some issues with sound, which will require you to remove some packages. Also, your modem will no longer work, but we will make a new driver available as soon as we can.

 

We will publish these gotchas and new drivers on our Wiki at [http://linux.dell.com/wiki/index.php/Products/Consumer](http://linux.dell.com/wiki/index.php/Products/Consumer) as soon as we can.  In the mean time, please continue to enjoy Ubuntu 7.10!"

---

### Post by gbrainin on 2008-05-05
> **RedRat said:**
> So far, I have found that 8.04 seems a bit faster and it certainly is much, much better when I want to attach to my Windows XP machine with the NTFS file system.

This is a bit off topic, but what are you referring to here in terms of attaching to the XP machine?  I ask because I am attaching to an XP machine at work, via a VPN, and I'm wondering if there's a difference in this sort of setup.

I'm still using 7.10 (downloaded 8.04, but haven't had the time to upgrade yet) on my Inspiron 530.

---

### Post by phenest on 2008-05-05
> **enchantedsky said:**
> ...Dell does not even go out of its way to make Linux drivers ----- my sister in law had to remove Ubuntu on her Dell and install Windows XP because her Dell Printer A920 only had Windows drivers made by Dell. ...

I don't think Dell make printers. They're just rebranded Lexmark printers which are well known for their lack of Linux support.

---

### Post by RedRat on 2008-05-05
> **gbrainin said:**
> This is a bit off topic, but what are you referring to here in terms of attaching to the XP machine?  I ask because I am attaching to an XP machine at work, via a VPN, and I'm wondering if there's a difference in this sort of setup.

I'm still using 7.10 (downloaded 8.04, but haven't had the time to upgrade yet) on my Inspiron 530.

I have an XP machine on my home network. I have several NTFS folders that I share on that machine. Under 7.04 and 7.10 Ubuntu, when I would try to connect to those folders, it would sometimes take minutes for Ubuntu to finally "see" those shared folders (using "Network" under "Places" in the menu bar). Now, 8.04 seems to see those folders immediately, connects, and the icon appears on my desktop.

However, I was and am now using the standard vanilla Ubuntu, not the Dell version. Through a mistake on my part, I dumped Dell's version unintentionally! My Bad. Nevertheless, I have not had any real issues with Ubuntu other than the upgrade to 8.04, but this seems to have been resolved. Keeping my fingers crossed.

---

### Post by phenest on 2008-05-05
I have a Precision M90. Is it worth me getting Dell's Hardy release? That is to say, would it support my laptop better? This laptop is essentially an XPS M1710.

---

### Post by caro on 2008-05-06
My Inspiron E1505n came preloaded with Feisty, but I downloaded both Hardy and Gutsy from the Ubuntu site.  No problems.  Didn't know Dell was even publishing a Dell-specific .iso.

---

### Post by gbrainin on 2008-05-06
Most of the modifications in Gutsy had to do with laptop hardware.  See [http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Known_Issues]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Known_Issues")

---

### Post by willfarr on 2008-07-30
It has been months now since 8.04 came out and I am still waiting on a Dell specific ISO to fix my brand new 1525N. If any body has a new 1525 with factory installed Hardy please copy it over and post somewhere. Otherwise, to heck with Dell ubuntu-I am putting XP on there so the thing will finally work properly. Then I will just have to settle for my Eee for any linux work...ugghh

---

### Post by fragos on 2008-07-30
Truth is that the strait from Ubuntu ISO works just fine on my 1420n. I've been running it for some time without any glitches. All the Dell work that went into 7.04 and 7.10 has found it's way into 8.04. I'm not sure what Dell can add or change. Check this link.

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

---

### Post by RedRat on 2008-07-30
> **willfarr said:**
> It has been months now since 8.04 came out and I am still waiting on a Dell specific ISO to fix my brand new 1525N. If any body has a new 1525 with factory installed Hardy please copy it over and post somewhere. Otherwise, to heck with Dell ubuntu-I am putting XP on there so the thing will finally work properly. Then I will just have to settle for my Eee for any linux work...ugghh

Have you checked the Dell support page:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)
Read all of the issues and work arounds for 1525.

---

### Post by swisscow on 2008-07-31
> **willfarr said:**
> It has been months now since 8.04 came out and I am still waiting on a Dell specific ISO to fix my brand new 1525N. If any body has a new 1525 with factory installed Hardy please copy it over and post somewhere. Otherwise, to heck with Dell ubuntu-I am putting XP on there so the thing will finally work properly. Then I will just have to settle for my Eee for any linux work...ugghh

Why not just install the normal hardy? I did on a windows xps machine and had no problems at all. Only had to add nvidia drivers (gnome did it automatically) and turn the sound up.

Maybe I've just been lucky. What problems are you having? Maybe they can be fixed quickly.

I hear what you say though about the Dell version of 8.04 and the length of time it is taking to arrive, though personally with it's partitioning scheme and the lack of problems with a normal hardy install I don't think it's worth waiting for.

By the way, if you do decide to revert to XP, make sure you've got all the drivers etc. I wiped vista but kept a little partition for xp (I have a few peripherals that only work with windows). When I tried to put xp on, I realised I had no drivers for it. The ones from dell were just vista drivers and they had no xp drivers for the xps. Had to hunt around for ages just for a video driver. Haven't bothered with sound etc.

Hope this helps

---

### Post by RedRat on 2008-07-31
> **swisscow said:**
> Why not just install the normal hardy? I did on a windows xps machine and had no problems at all. Only had to add nvidia drivers (gnome did it automatically) and turn the sound up.

Maybe I've just been lucky. What problems are you having? Maybe they can be fixed quickly.

I hear what you say though about the Dell version of 8.04 and the length of time it is taking to arrive, though personally with it's partitioning scheme and the lack of problems with a normal hardy install I don't think it's worth waiting for.

By the way, if you do decide to revert to XP, make sure you've got all the drivers etc. I wiped vista but kept a little partition for xp (I have a few peripherals that only work with windows). When I tried to put xp on, I realised I had no drivers for it. The ones from dell were just vista drivers and they had no xp drivers for the xps. Had to hunt around for ages just for a video driver. Haven't bothered with sound etc.

Hope this helps

I would agree. As I posted before, I installed vanilla Ubuntu 7.10 on my Dell 530n, I wiped out all the original factory Dell stuff accidentally, but found that 7.10 went on and worked well except for nVidia drivers etc. However, after allowing Synaptic to upgrade to 8.04 all has gone very well. Now this is a laptop and you are dealing with a laptop so things might be slightly different, but why not just give it a try. Backup all your data files of courese.

---

