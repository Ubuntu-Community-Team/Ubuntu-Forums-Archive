---
title: "Ubuntu on a Dell Windows laptop"
date: 2008-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by clavdivs on 2008-04-22
I'm hopefully going to be buying a laptop in the near future, and aside from the fact that they support Ubuntu, I'm leaning towards Dell because I like their "cafeteria-style" method of buying one online (some other companies I've looked at give each possible configuration a unique model number, and choosing the exactly one you want is a hideous ordeal). I'd considered buying one of their Ubuntu machines, but a) I'd prefer to dual boot, and b) the Windows machines seem to have deeper discounts so it looks like I'd actually save money that way.

However, I'm a mite worried about hardware compatibility. For the pure Ubuntu machines, they've presumably only chosen hardware that they know is compatible with Linux and know it works, but there's no reason they'd do the same for Windows machines. So I'm wondering if there's anything I need to watch out for on those, anything known to be compatible I should look for, anything known to be incompatible I should watch out for, or anything so-so and what it takes to get it working.

In particular I'm concerned about wireless networking; I've heard that this can be especially difficult on Linux, but it's pretty important for a laptop. I figured I'd start with the same basic models as their Ubuntu laptops, and of those I prefer the 1420 (the XPS is more than I need, but I'd like to have a real 3d card for occasional gaming). But the one wireless card available for the Ubuntu version (Intel 3945 802.11a/g Mini-card) isn't even an option for the Windows one. Are the other cards incompatible full-stop, would I need to wrestle with ndiswrapper, or will they just work? I noticed they weren't listed as compatible in the wiki; will this improve with the impending release of Heron? Should I just buy the Linux-compatible card separately and install it myself?

Thanks for whatever help you can give me.

---

### Post by sdennie on 2008-04-22
I would avoid the "Dell wireless" and look for either Intel 3945 or 4965 (I believe Dell calls this Intel nextgen wireless N).  Both of those should work out of the box on Hardy.  I would also personally go with the intel graphics if possible.  On Hardy (and probably Gutsy) it works out of the box and is very good for everyday work.  The nvidia graphics are great for games but, the 8 series cards are not as good as the intel integrated graphics for normal desktop work.

---

### Post by Vaun on 2008-04-22
I've been running Hardy since Aplha 4 on my laptop and it's simply amazing.  I have a Dell XPS m1530 w/ nVidia 8400 GS and Broadcom 4328 Wireless Draft N card and they all work flawlessly.  The BCM4328 will not work out of the box as you have to install ndiswrapper and a few other adjustments.  Compiz Fusion runs amazingly smooth on this releatively low graphics card using the latest beta driver (173.08).  Suspend/resume are working with some minor tweaks as well.  Bluetooth works with my Bluetooth mouse and I'm also able to  connect to my HTC Mogul Smartphone via bluetooth.

I've been very happy with this laptop all for under $900.00 USD.

---

### Post by clavdivs on 2008-04-23
Thanks for the info. My fears have been allayed and my confidence bolstered. It might be a few weeks before I can order my laptop, but I'll definitely be downloading Hardy and trying out the live CD as soon as it goes live tomorrow.

EDIT: Followup question: How are the other Inspiron laptop models for Linux compatibility, or the XPS line for that matter? I'd only really looked at the ones they sell with Ubuntu.

---

### Post by elmoglick on 2008-04-24
> **Vaun said:**
> I've been running Hardy since Aplha 4 on my laptop and it's simply amazing.  I have a Dell XPS m1530 w/ nVidia 8400 GS and Broadcom 4328 Wireless Draft N card and they all work flawlessly.  The BCM4328 will not work out of the box as you have to install ndiswrapper and a few other adjustments.  Compiz Fusion runs amazingly smooth on this releatively low graphics card using the latest beta driver (173.08).  Suspend/resume are working with some minor tweaks as well.  Bluetooth works with my Bluetooth mouse and I'm also able to  connect to my HTC Mogul Smartphone via bluetooth.

I've been very happy with this laptop all for under $900.00 USD.
Vaun - When you close the laptop and re-open, you don't have any problems with the touchpad mouse?   I installed 7.10 and it works fine until I close the lid and reopen.   Then the cursor moves erratically and cannot be controlled.  Plugging in an external USB mouse works fine.   

The new Ubuntu 8.04 release candidate is even worse - the mouse touchpad exhibits this problem at boot.

Thoughts?

Thanks,
Earl

---

### Post by Muflon on 2008-04-24
Hi clavdivs

See my post [http://ubuntuforums.org/showthread.php?t=758505](http://ubuntuforums.org/showthread.php?t=758505) for my expirience with an Inpiron 1525 that I bought a week ago.

The expirience with Hardy is very positive and I agree about getting the Intel Wifi option.

Muflon

---

### Post by grenet on 2008-04-24
if you wait for the custom Dell ISO, all options for wireless will work well.

I use a 1420N, and am looking forward to some of the things Hardy is supposed to offer, like a un-blacklisted Intel video card.

If you are looking for a dual boot, you might be better off to order a win based dell, because when you try to install a win OS, it will blow out your partitions, and you'll need to reinstall Ubuntu all over again any way.

Just a thought.  From what I have read, on these forums, there is no way to get around the Win OS installer.

Wait for the Dell ISO, and you'll be a happy camper.

---

### Post by Muflon on 2008-04-24
Hi grenet

From my expirience with a Inspiron 1525 with Vista installed, you can just go and install the Hardy standard release and everything will work fine including Wifi and Compiz :)

Enjoy

Muflon

---

### Post by grenet on 2008-04-24
Sure, but it's not backwards compatible, meaning.  If you already have a Win OS installed, then Ubuntu is nice, and will partition and install right to the same drive.

If you have a machine with Ubuntu, but no Win OS, if you try and install XP or Vista, the windows installer will blow out your partitions, and you'll need to reinstall Ubuntu after.

So you are correct, a machine with Win OS installed, will take a dual boot Ubuntu install easily.

I'm going to wait for the Dell ISO, it will make things easier for me.  And since I'm going to do a fresh install, I should probably dual boot an XP copy too.

---

### Post by sdennie on 2008-04-24
I don't think a Windows install will actually blast your Ubuntu install (depending on how you partition).  It just overwrites the MBR and so you can't easily boot into linux.  Windows is helpful like that.

Also, I've become a fanboy of Dell.  My XPS m1330 is by far the best linux machine I've ever used.  I subscribe to the Dell linux mailing lists and, I'm blown away.  People ask linux related questions to a major vendor and the vendor responds (quickly) in a meaningful and helpful way.

I hate to sponsor a company but, really, buying a Dell laptop (Vista or Ubuntu edition) and installing Ubuntu on it is a really painless experience.

---

### Post by argraff on 2008-04-24
> **grenet said:**
> 
I'm going to wait for the Dell ISO, it will make things easier for me.  And since I'm going to do a fresh install, I should probably dual boot an XP copy too.

Where does one acquire a Dell ISO? I have an old Inspiron 2500 which I can't get the monitor resolution right on and I can't find any help that works on this little beast. Will a Dell ISO help?

---

### Post by sdennie on 2008-04-24
It might help.  [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) is the link you would want.  Though, I imagine they will update their machines to Ubuntu 8.04 fairly quickly so, it might be worth waiting for that.

---

### Post by notwen on 2008-04-24
> **argraff said:**
> Where does one acquire a Dell ISO? I have an old Inspiron 2500 which I can't get the monitor resolution right on and I can't find any help that works on this little beast. Will a Dell ISO help?

Dell's custom Ubuntu images are only released for the specific models under their N-Series.(ie. the models that come w/ Ubuntu pre-installed)  You can find them available via [Dell's Linux Wiki]("http://linux.dell.com/wiki/index.php/Products/Client").  Some other models tend to include similar hardware, as lots of Vostro users have claimed to get better hardware recognition by using a custom Dell Ubuntu install.  So compare your hardware to some of the similar N-Series models and maybe try that specific custom Ubuntu image on your machine.  **This is just a option, I do not recommend doing this as these custom CDs were made for the model specified on Dell's Linux Wiki**.  You could also check out my Dell Linux Wiki sticky thread here for more useful links and info.

Dell generally gets their custom images released within a month or so of the official Ubuntu release.  So w/ Hardy Heron being released today, I would guess Dell would have their custom images up within 4 weeks give or take.  Just my guess though.

---

