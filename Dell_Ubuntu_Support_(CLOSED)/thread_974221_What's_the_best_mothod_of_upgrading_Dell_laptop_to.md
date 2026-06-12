---
title: "What's the best mothod of upgrading Dell laptop to 8.10?"
date: 2008-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by purplepaint on 2008-11-07
I'm currently using a Dell Inspiron 1525 which came with Ubuntu 7.10 pre-installed.  A day or so after I bought it, 8.04 was relesed and I was able to upgrade using the update manager fairly easily.  After the upgrade, I just had the "known issues" mentioned on the Dell Linux Wiki (sound not working, WIFI LED not lighting up etc.) which I was able to fix easily following the instructions on the wiki.  From what I've read on the forums so far, upgrading to 8.10 doesn't seem to be going very smoothly for a lot of people.

I can't find any information on the Dell Wiki about 8.10 at the moment, so I was wondering if anyone using a Dell laptop could share their upgrade experiences and give advice - should I upgrade via the update manager, should I perform a fresh install from a CD (I was considering backing everything up and then trying the upgrade and doing the install if that failed) or should I perhaps wait for more information/a custom 8.10 ISO to be posted on Dell's Wiki?

---

### Post by removesstains on 2008-11-07
I purchased a 1525 over the weekend that came w vista. I have installed 8.10 and i have a few issues. If i update the kernals in the update manager my Wi-fi card no longer works. So i fresh installed 8.10 and haven't updated the kernals. 

Also a huge annoyance for me is when i set it up to hibernate when i close the lid. Instead of going to sleep, it completely shuts down. even if i manually try to set it to hibernate. I haven't found a fix yet. 

last night i downloaded the Reinstallation iso for 8.04.1 from the dell linux wiki and decided to try and install that on my laptop since the specs for main are the same as the 1525n except for the wifi card. But after i get past the installation screen i don't know what to do, it boots up in terminal and i'm such a newb to linux. I just decided to put 8.10 but on it and wait for a lid fix.

---

### Post by timcredible on 2008-11-07
i have a dell vostro 1000, and dual boot with xp.  with 8.04 i had to install via 'safe graphics mode', i had to download ati drivers via the hardware manager, i had to run ndiswrapper and point to my driver for wireless to work, and i had to run gnome-ppp for wireless broadband.  with a fresh install of 8.10, EVERYTHING ran perfect from the livecd.  so, i would recommend just booting with the 8.10 livecd and see what works.  if things look good, do a fresh install.  backup your data first though.

---

### Post by Spooky5 on 2008-11-07
I have a 1525n. I didn't have any problems whatsoever upgrading to 8.10 through the update manager. :KS

---

### Post by purplepaint on 2008-11-07
> **Spooky5 said:**
> I have a 1525n. I didn't have any problems whatsoever upgrading to 8.10 through the update manager. :KS

Ah, now that's interesting.  When I get round to upgrading, I might hold you to that!

Do you mean literally no issues or that there were issues and you've since been able to solve them (or perhaps that there are issues you are yet to encounter :?)?

---

### Post by Spooky5 on 2008-11-07
I had no issues with the upgrade (I did have to re-enter my wi-fi password when it rebooted from the upgrade, though). I haven't encountered any other issues since then. :)

---

### Post by removesstains on 2008-11-07
> **Spooky5 said:**
> I had no issues with the upgrade (I did have to re-enter my wi-fi password when it rebooted from the upgrade, though). I haven't encountered any other issues since then. :)

So when you close the lid your laptop actually goes to sleep or does it shutdown?

---

### Post by Spooky5 on 2008-11-07
I have the sleep function turned off because I turn my laptop off when I'm not using it.

---

### Post by purplepaint on 2008-11-08
Right, I upgraded via the update manager, rebooted, it then told me (while I was looking through my software sources), to perform a "partial upgrade" which I have just done (it didn't require a reboot) and now everything's fine...

...except Firefox doesn't seem to be remembering any of my settings (when I started it up all my toolbars and buttons had ben reset to their defaults and no changes I make are sticking after I restart Firefox).  Presumably something's happened to my Firefox config file (I assume that's how it works).

---

### Post by sirebral on 2008-11-08
I am going to jump on and say this:

Get on the Idea Storm of DELL and ask for a repository from DELL.  Then everyone promote the idea!

If DELL wants to offer Ubuntu on their PCs, and they are doing this because of customer demand, then they need to swing the bat fully and provide the back port drivers for their users.

Trust me on this.  DELL is listening to their community on idea storm.  The Studio Hybrid and the Mini 9 and even offering Linux to more PCs are just some examples of DELL providing what the customer asks for.

I know this isn't a quick fix ... but it will help later on.  I found upgrading to 8.10 on my Studio Hybrid very smooth, and I upgraded my 8.04 distro on my Inspiron laptop with no problems at all.  I even have the WiFi light active.

---

### Post by Wolfhere on 2008-11-08
I have a D620, dual boot..Vista Ultimate on one side and Ubuntu 8.10 on the other. When I called for the support I paid for, told them I was having problems with docking and external monitor not working, they said that would void my warranty. So I told them that Vista was still installed, but they said they do not support Ubuntu on my laptop.
(I open the laptops while docked, and do the Fn-F8 thingy about 2 times...leaving the lid open). So if you come up with a solution for the shutoff... pass it along.
I agree, they are starting to listen. But one thing I know for sure.... I am not alone out here in the sticks. You guys are awesome! Thank you.

---

### Post by purplepaint on 2008-11-11
Right, my Firefox issue has temporarily been fixed by disabling Tab Mix Plus.  On the whole, I'm very impressed with Intrepid Ibex; it now makes my wifi LED flash when something-or-other happens (I think it's during downloads and uploads - which is good) and it also supports a wireless 3G card that I'd previously been unable to get to work - now all I had to do was insert it and click "Next" a couple of times!

---

### Post by notwen on 2008-11-11
Dell generally releases their custom Ubuntu image a month or two after the official release.  This custom image normally contains all extra drivers/packages used in the N-Series models like your Inspiron 1525n.  Check [Dell's Linux Wiki]("http://linux.dell.com/wiki/index.php/Wiki_Main_Page") for more info.  I also made a sticky thread atop the Dell-Ubuntu sub-forum here w/ some useful info.

---

### Post by amendt on 2008-11-11
I am probably one of the few that have update those Dell Inspiron 1525n both via a new install and via the update manager.  It was because I needed Empathy (VOIP) to work.  *I think remote desktop and Jabber is the best think since slice bread was invented*. I found that the dell update worked better, mind you I can only get the built-in camera to work in Skype and not via Cheese.  With a fresh install I can't even get the camera to work in any program.  I haven't checked into it much but there must be a camera kernel update available soon.  Everything else works fine.  I was surprised that the update download over 1.2 Gigs. better keep a good isp handy.

---

### Post by JinStevens on 2008-11-11
> **Spooky5 said:**
> I had no issues with the upgrade (I did have to re-enter my wi-fi password when it rebooted from the upgrade, though). I haven't encountered any other issues since then. :)

This has been my experience as well.  The only thing I had to do is re-add wifi passwords to the two private wireless networks I use.

I updated over a wireless network using Update Manager, upgrading from 8.04. Upgrading was a snap and it went a ways from erasing the bad memories I still have when I upgraded to Windows XP from Windows 98 back in the day (now that was a horrible, horrible upgrade!)

Laptop is an Inspiron 1525 I bought refurbished from Dell.  It came with Windows Vista Basic (which I blew away) and installed with 8.04 and subsequently upgraded to 8.10.

---

### Post by iaskedalice09 on 2008-11-13
I'd say go for the graphical update manager or if you're a geeky type Terminal it.

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

I'm a geek that went with the GUI and had no problems with the update process itself; it was very straight-forward.

---

