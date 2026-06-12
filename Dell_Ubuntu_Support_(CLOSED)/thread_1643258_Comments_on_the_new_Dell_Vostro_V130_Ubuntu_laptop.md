---
title: "Comments on the new Dell Vostro V130 Ubuntu laptop?"
date: 2010-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by linuxforartists on 2010-12-11
When I checked Dell's Ubuntu page recently, all the computers were removed except for a desktop tower system.  I'm only interested in laptops.

Then I read about this: [Dell's new Vostro V130 laptop]("http://www.omgubuntu.co.uk/2010/11/dells-new-vostro-v130-ultra-thin-ubuntu-laptop/")

I went to the Dell page to check it out.  Kinda annoyed that the customization options are non-existent.  I would've liked an Intel i3 processor, at least.

Is the Dell wireless card any good?  I've heard Intel and Atheros wireless cards work well.

---

### Post by carignan.boy on 2010-12-23
I got this laptop a few days ago. I've been travelling a lot recently and my previous laptop was a fat 15.4" Inspiron 6400. I think the small reduction in screen size is worth the major reduction in weight. I mean this thing is slimmer than a MacBook. (I stared at those specs for a long time, in disbelief)

I got it with the i5 and 4GB RAM. Wiped Windows right off and Ubuntu runs great. Compiz and advanced effects work. OGL graphics can be a bit sluggish, but they work.
Fullscreen Youtube 720p videos run great. 

The 2 finger scroll on the trackpad doesn't work but that's probably a driver issue. It's a new laptop so I wasn't expecting everything to work out of the box. My 6400 worked better over time, after all.

Keyboard is a decent size, the Home, PgUp, PgDn and End button are weirdly positioned, but I'm sure I'll get used to that. The keys are bigger than they were on my 6400 which is good news.

As for your question about the wireless card, it's got N in it and I've had no problem whatsoever connecting to networks in Ubuntu.

Hope this helps you make a decision.

---

### Post by chunky bacon! on 2011-01-10
Hello,

I ordered the Ubuntu Vostro V130 last night.  Not the upgraded version, but the base version that Dell ships with Ubuntu 10.04 installed on it.  Expected delivery date is 2-2-11.

I'll do my best to post a review shortly after I receive it.  I can't really find a review on the base model, it seems that every google search comes back with something like the poster above me--an upgraded flavor that perhaps someone wipes windows on, which is great, but I know some folks want to know how the very basic celeron cheapie that has no Windows Tax on it performs.

I know I did, but I figured at this price, and due to what I am replacing (an Dell D600), I couldn't go too far wrong. 

I was running Linux Mint on the D600, so this will be my first foray into Ubuntu, but apparently a similar foray since Mint is a fork of Ubuntu, right?

Later I guess I'll figure out if I need to upgrade to 10.10 or not.

---

### Post by chunky bacon! on 2011-01-21
It finally came in today.  I'll have more hopefully in the next few days, although my weekend is unfortunately kind of busy (want to play more with new toy).

In short, I'm happy with it.  Keyboard feels great, and Ubuntu 10.04 out of the box works great.  One of my very basic tests is do I have to go in and write something in a config file in order to get wireless to work.  The answer was, nope, everything works fine! 

And I think the machine is dead sexy.



More in the  next few days.

---

### Post by jabryl on 2011-01-27
I've had this laptop for a few weeks now. I bought the $430 version. The Celeron isn't exactly a powerhouse but the price was right. I've been pretty pleased with it.
For battery life I've been getting 2.5-3 hours. 
720p video performance is fine, for both flash and .mkv files. 1080p video is a mixed bag. The 1080p version of Big Buck Bunny plays smoothly. 1080p flash is nigh unwatchable. Most other 1080p video is somewhere in between. As mentioned above 3d performance is sluggish.

It took me about an hour to get Compiz running. Not because of any incompatibility, but rather because it literally wasn't there. I had to install it through Synaptic. Since it's a standard part of an Ubuntu installation it didn't occur to me that it might not be installed, so I spent an hour trying to figure out how to enable the proper driver to make it work. Since it comes with Ubuntu Dell had to have deliberately removed it form the system. If any Dell reps read this forum I would really love to know the reasoning behind that decision.
Anyway, once it was installed it just took a couple of clicks in the appearance settings to enable it, and it works great.

The touchpad works fine. Edge scrolling works out of the box. Two finger scrolling can be enabled by installing this package.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+attachment/1771346/+files/synaptics-dkms_1.1.1_all.deb](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+attachment/1771346/+files/synaptics-dkms_1.1.1_all.deb)
Once it's installed you can enable it on the touchpad tab in the mouse settings.

That's all for now. Any questions feel free to ask.

---

### Post by carignan.boy on 2011-01-31
> **jabryl said:**
> 
The touchpad works fine. Edge scrolling works out of the box. Two finger scrolling can be enabled by installing this package.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+attachment/1771346/+files/synaptics-dkms_1.1.1_all.deb](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+attachment/1771346/+files/synaptics-dkms_1.1.1_all.deb)
Once it's installed you can enable it on the touchpad tab in the mouse settings.

Thank you!!! I've really gotten used to two finger scrolling and I love it. Was kind of bummed that it didn't work. Now it does!

---

### Post by chunky bacon! on 2011-01-31
I do have to update with the fact that bluetooth on this machine does not work if you make the mistake of turning it off.  You will NOT be able to turn it back on, and nobody can help you.  I have given a more detailed description in the networking/wireless forum.

An immense amount of troubleshooting has yielded no answers, and Dell tech support will transfer you an infinite number of times until they finally disconnect you, and of course not call you back even after taking that number to call you back.

I'm on hold with their supposed ubuntu support again for the umpteenth time today.  Terrible way to spend 2.5 hours so far.

---

### Post by chunky bacon! on 2011-01-31
Edit:

See my post [here ]("http://ubuntuforums.org/showpost.php?p=10420998&postcount=4")for further explanation of the issue.

In short, the Bluetooth device shipped with the Vostro cannot be turned up in Linux, so far.

---

### Post by daspliff12345 on 2011-02-07
Hey I have been reading your posts concerning this laptop. I am considering buying one due to the price. However, I am apprehensive about the performance those specs are going to deliver. Do u think it will be able to run windows virtualized smoothly. I am presently running Ubuntu 10.10 with windows on virtualbox on a 4yr old Compaq Presario 1.7 celeron and 2Gig ram for the last six months (I am a linux newbie ). It struggles mightily and freezes a lot, hence my need for a new system. I like the portability and look of this system but need to be a bit more informed. Share your thoughts?

---

### Post by Agent69 on 2011-02-08
Can anyone tell me what chipset the wireless uses? Can't seem to find it via Google.

---

### Post by perolad on 2011-02-08
Hi,

I tried to install the two-finger scrolling package you recommended below on my Vostro V130, but the terminal window informed that the package failed to install.  Twice.  Any further advice?

Thanks,

-p


> **jabryl said:**
> 

The touchpad works fine. Edge scrolling works out of the box. Two finger scrolling can be enabled by installing this package.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+attachment/1771346/+files/synaptics-dkms_1.1.1_all.deb](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+attachment/1771346/+files/synaptics-dkms_1.1.1_all.deb)
Once it's installed you can enable it on the touchpad tab in the mouse settings.

That's all for now. Any questions feel free to ask.

---

### Post by chunky bacon! on 2011-02-28
.

---

### Post by chunky bacon! on 2011-03-01
> **daspliff12345 said:**
> Hey I have been reading your posts concerning this laptop. I am considering buying one due to the price. However, I am apprehensive about the performance those specs are going to deliver. Do u think it will be able to run windows virtualized smoothly. I am presently running Ubuntu 10.10 with windows on virtualbox on a 4yr old Compaq Presario 1.7 celeron and 2Gig ram for the last six months (I am a linux newbie ). It struggles mightily and freezes a lot, hence my need for a new system. I like the portability and look of this system but need to be a bit more informed. Share your thoughts?

Man, I wish I could tell you.  I'm really not a hardware guy, per se.  I've been doing some reading, and it seems that the biggest problem would be your memory--2 gig.  Well, this box is the same--2 gig.  I'm not sure if I can get to it to expand it, but for me that hasn't been a problem.  

I don't ever intend to run Windows on it, so it does OK for me for what I use it for, mainly.

Although last night I had to call Dell tech support because the laptop got stuck in an eternal reboot with nothing on the screen.  I was walked through how to bring up the Dell diagnostics on this machine--hold down the F2 key and the power button at the same time.  Somehow, just running the diagnostics got the reboot to go back to normal.

They said I got next day business support in buying the Vostro line, in terms of parts and things, so I guess I'm going to cross my fingers that this thing doesn't break in a year.

---

### Post by chunky bacon! on 2011-03-01
> **Agent69 said:**
> Can anyone tell me what chipset the wireless uses? Can't seem to find it via Google.

Dell Wireless 1702 802.11n/BT3.0 Networking Combo Card Vostro

the bluetooth is "handled" (fails in ubuntu) by an Atheros AR3002

---

### Post by fatpandasays on 2011-03-06
> **chunky bacon! said:**
> Dell Wireless 1702 802.11n/BT3.0 Networking Combo Card Vostro

the bluetooth is "handled" (fails in ubuntu) by an Atheros AR3002

Dell 1702 (in this case) is an Atheros AR9285.

--
Panda

---

### Post by chunky bacon! on 2011-03-07
> **fatpandasays said:**
> Dell 1702 (in this case) is an Atheros AR9285.

--
Panda


Am I misunderstanding the 1702, or are you on the wrong thread?

---

### Post by mylh on 2011-04-05
thanks for the link. 2finger scroll started to work

---

### Post by chunky bacon! on 2011-04-28
> **chunky bacon! said:**
> Edit:

See my post [here ]("http://ubuntuforums.org/showpost.php?p=10420998&postcount=4")for further explanation of the issue.

In short, the Bluetooth device shipped with the Vostro cannot be turned up in Linux, so far.


Found a fix for the bluetooth issue (finally).  Resolved by this gentleman in this post on the bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/comments/10](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/comments/10)

Follow his steps exactly, and download those files, and fixes this issue.  I feel like I hit the lottery today.

Also, as noted in the bug report, I upgraded to 10.10, and then went to 11.04, and the laptop handles it fine.  The load time for the desktop after you log in is a bit longer, but otherwise things seem fine.

Oh, I did have to change screensavers, but I like the Electric Sheep screensaver better than Ubuntu's default options anyway.

---

### Post by jostmey on 2011-05-05
I recently purchased a dell v130 vostro (with Ubuntu on it of course). It will be a week before it ships. Let me if anyone has had any hardware failures with their machine. I am always concerned about my new purchases, and want to make that this purchase is worth the money.

- Jared

---

### Post by roberts3000 on 2011-05-17
> **jostmey said:**
> I recently purchased a dell v130 vostro (with Ubuntu on it of course). It will be a week before it ships. Let me if anyone has had any hardware failures with their machine. I am always concerned about my new purchases, and want to make that this purchase is worth the money.

- Jared

I Have had mine for about two mouths now. works great, no problems at all. Running xubuntu 11.4.

---

### Post by ffeingol on 2011-05-17
What kind of battery life are you getting?

---

### Post by jostmey on 2011-05-19
Just over two hours, and that is with CPU scaling turned on and with the screen brightness turned down.

---

### Post by chunky bacon! on 2011-05-19
> **jostmey said:**
> I recently purchased a dell v130 vostro (with Ubuntu on it of course). It will be a week before it ships. Let me if anyone has had any hardware failures with their machine. I am always concerned about my new purchases, and want to make that this purchase is worth the money.

- Jared

Can't believe I've had mine since February.  Good times.  I'm running 11.04 on it now, with no real issues.

Lately, I've been busy both professionally and personally, so I haven't done much with it other than surfing and music playing, so I haven't been kicking the tires as much, so to speak  

While not a logical thing, I do love the form factor of this laptop.  So light, and nice.  The red is dead sexy, imo.

Battery life is not the best, all the reviews are correct--if you travel a ton, or are in places where you can't plug in every 2 hours or so, this machine is not for you.  When I say "2 hours," I'm going by what the Ubuntu (gnome?) power indicator states that I have left.  I've never run it all the way down to find out.

---

### Post by ffeingol on 2011-05-20
Yea, I'd love to go with this one (size, price etc.) but 2 hours is just not enough.  I'd really hate to see what it's like in a year or so when the batter doses not hold a charge as well as it did when it was new.

The hunt continues.

---

### Post by banff2010 on 2011-06-21
To OP:

Are you happy with it? Are you using MS Office on vine? If yes any comments?


Thanks

I ordered it, estimated delivery date is July 4, 2011; including all the taxes it cost me $315.21. I was looking at other laptops and Mac book pro. I chose this based on my need. I want to use Office (Excel and Word) when I travel. This will tell me how good open office  compared to MS office. 2hr battery life is not a big deal for me.My last laptop Fujitsu T4020 (one of the very first tablets) died a few months ago. I think I paid ~$2800 for it. Before, it died it made lots of noises; I was able to get some noise out by removing adobe. Never had chance to install ubuntu. I will stay way from adobe.  Thank you for reading.

---

### Post by bubblehead74 on 2011-07-25
I bought a V130 few weeks ago. I am very happy with it. CPU is better than the Core 2 Solo I had in my V13 before. A 720p Flash video runs smoothly. The only gripe I have is that the monitor colors are way off to the blue. I have to use xgamma to adjust colors to have neutral gamma 2.2.

---

### Post by heyted on 2011-07-30
> **chunky bacon! said:**
> See my post [here ]("http://ubuntuforums.org/showpost.php?p=10420998&postcount=4")for further explanation of the issue.

In short, the Bluetooth device shipped with the Vostro cannot be turned up in Linux, so far.

The bluetooth device can work as expected including being able to be turned on after being turned off in 10.04 with kernel 2.6.32-33.

---

### Post by wh1zz0 on 2011-07-30
Please guys I would appreciate any help on this...

Thanks in anticipation of any swift response....

```
http://ubuntuforums.org/showthread.php?t=1814836&highlight=dell+1310+hibernate
```

Kind regards,
Wh1zz0

---

### Post by Erzzzz on 2011-08-08
For the folks that got this rig - was the upgrade to 11.04 smooth or should I just leave with the older system that Dell will ship it with?

---

### Post by daspliff12345 on 2011-08-09
i did not go the usual upgrade path...i did a fresh install. Worked out great. Still cannot get the bluetooth to work....any ideas...i am on the latest PAE kernel

---

### Post by heyted on 2011-08-10
> **Erzzzz said:**
> For the folks that got this rig - was the upgrade to 11.04 smooth or should I just leave with the older system that Dell will ship it with?
If you are looking for stability, stick with 10.04.  If you are looking for the latest features and speed, go with 11.04.  A fresh install of 11.04 should go smoothly, but the next release is coming out in just a couple more months.  11.04 is faster than 10.04, and it is faster than Windows 7 and OS X 10.7 according to [http://www.expertreviews.co.uk/general/1286485/ubuntu-11-04-vs-windows-7-vs-os-x-10-7-lion](http://www.expertreviews.co.uk/general/1286485/ubuntu-11-04-vs-windows-7-vs-os-x-10-7-lion) .  I am keeping 10.04 until the next LTS is released (with a few tweaks such as installing Compiz).

---

