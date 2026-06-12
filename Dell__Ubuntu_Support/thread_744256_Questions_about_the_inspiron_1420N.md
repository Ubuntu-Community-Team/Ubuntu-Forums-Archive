---
title: "Questions about the inspiron 1420N"
date: 2008-04-03
forum: Dell  Ubuntu Support
---

### Post by Ptero-4 on 2008-04-03
Hi. I would like to get an inspiron 1420N (currently have a toshiba satellite laptop running linuxmint 4, since no other distro runs at all in this thing), but I would like to know a few things first.
1) Does it dissipate the heat through a vent or through the keyboard area (I used to own a 500MHz iBook and it's screen got a severe burn damage due to the heat flowing up from the keyboard and I have heard that laptops that have vents for dissipating heat doesn't have this problem)?
2) Does it come with a restore partition or disc? and if it's a restore partition, is it accesed via the ubuntu grub or via a hotkey shown at the POST screen?
3) How good and reliable is it (my toshiba has the strange thing that if I'm running gnome or xfce it is excesivelly slow even without compiz and with only one app running, but if I run KDE in it's default configuration it's quite fast even with compiz running and several apps running, also it tends to move the text pointer around when in textfields like the forums reply box or either add characters I didn't type or ignore characters that I typed)?
4) How durable is it?

---

### Post by natehall on 2008-04-03
1)It vents through the Lelt side. Mine does not get very warm. Nice and quite fan.
2) It has a restore partition that you get to through the BIOS. While learning Linux I used it twice.
3) Compiz was blacklisted on mine, so I can't say how much that is going to slow things down.
4)I've dropped it once since I've owned it from about 2 feet. No problems so far.

---

### Post by fragos on 2008-04-03
I love my 1420n. I have the 9 cell battery which even after a lot of use still gives me almost 5 hours. Everything worked with 7.04 and I upgraqed to 7.10 with the Dell 7.10 DVD and it all still works. I also run 7.10 on a DIY desktop and use NFS with Unison to keep my data in sync.

---

### Post by niteshifter on 2008-04-03
Hi,

Happy owner of a 1420N since January (shipped with 7.10)

2) Has two restore means:
A) Via GRUB: boots into a partition (/dev/sda2).
B) An ISO located in /home which you burn to DVD (5GB, need dual layer drive / disk).

3) I ordered mine with the NVidia 8400GM card, compiz was installed and enabled out of the box. Works fine. 

4) Rugged: yes. Rather impressive for a non-metal cased unit. Waterproof: No.

I also spec'd the Intel 3945 for wireless. This box arrived with 3 restricted drives (Conexant modem, NVidia, Intel) already installed. Don't know about the modem, but video and wireless work well.

It has a problem with suspend-resume, but hibernate works. I understand the suspend issue is fixable - but I haven't got around to that yet (I don't use suspend).

---

### Post by aidave on 2008-04-03
It is mostly good but suspend/resume doesnt work!!  To me that is a key feature of a laptop.  I couldnt recommend this laptop to anyone because of that issue.  I would try System76 instead.

---

### Post by Ptero-4 on 2008-04-04
Guess it's good then (unfortunatelly I'm gonna have to wait a bit more 'cause my sister couldn't find a physical retailer anywhere in the USA that have that model, DAMN M$ for hiding stuff, they're always doing this ****).

---

### Post by RetiredInMaine on 2008-04-05
I have a 1420 with 7.04 loaded. fargos said he upgraded to 7.10 with a dell dvd . Where can I get a dell 7.10 dvd?

---

### Post by Speidereyes on 2008-04-05
> **RetiredInMaine said:**
> I have a 1420 with 7.04 loaded. fargos said he upgraded to 7.10 with a dell dvd . Where can I get a dell 7.10 dvd?

You can get the remaster here. Make sure to choose the ISO that corresponds to your video card make:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

I have a Vista preloaded 1420 because I could not get the Ubuntu version in my country at the time (Canada). I wiped Vista off and replaced it with Ubuntu Gutsy and have had almost no problems.:) You can get compiz to work with the Intel card with a tweak provided at the above link. Myself I do not use the remastered ISO but the 64 bit version instead and everything seems to work (flash and WPA wireless encryption included). Suspend also appears to work but I do not use that function a lot so don't take my word on it. Most basic annoyances (they are relatively minor ones at that) can be fixed with the relatively simple tweaks provided at the Dell Ubuntu Wiki. Hopefully Hardy will have everything working out of the box when released.

I am happy with my purchase considering the price. Compiz works fine and isn't slow. The case and keyboard are robust. It probably isn't in the same league as a Thinkpad or Macbook but it is a quality product, particularly when considering it is the current bottom of the line laptop at Dell. Not a gaming platform though.

---

### Post by notwen on 2008-04-06
1. Vent on the left side.
2. Pre-installed w/ a restore option via GRUB.  You can also download Dell's custom Ubuntu iso from the Dell Linux Wiki, they provide images for specific models.
3.  My Intel X3100 chipset is blacklisted, I bypassed this however and use some Compiz features w/o any slowdown in performance that I've noticed.  I generally surf, watch videos, listen to music and chat on irc on my machine.  
4. Wouldn't know, I pamper my laptop.

I throughly enjoy my Inspiron 1420n and would recommend it to others as well.  That said, I believe I've read somewhere on the forums here that the X3100 works w/o any issues in Hardy BETA and that the chipset will not be blacklisted.  Best of luck w/ your future purchase.  =]

---

### Post by skipknyc on 2008-04-06
I hope this finds you well.

Mine runs cool and quiet. Just got **[COLOR="Red"]Compiz[/COLOR]** running on it this week (thanks to the Forums), and it's running quite well. Loaded autoplay for **[COLOR="Red"]vlc[/COLOR]** and that's working like a charm.

I'm a Linux/Ubuntu noob, less than a year old, but I'm so impressed with the performance and features of the system that I'm planning to purchase a new Dell desktop soon after they're available with Hardy Heron pre-installed.

The 1420N is as solid as a rock. It's a bit too big and heavy to take with me on the road on business trips, though. But that's OK ... my little Fujitsu is my road machine ... at least for now.

---

### Post by lofidelity on 2008-04-07
If your really worried, Dell has one nice thing in their warranties for any of their systems.   It's called complete care, and it's only a little extra, but will cover accidental damage.   Anyone complaining their screen got smashed in their laptop bag doesn't have this, or else they'd be laughing. 

It looks like it's $99 for however long the warranty is, and they're bundling in Lojack protection.

I've had one in my hands, they're definitely a sweet system.

---

### Post by aysiu on 2008-04-07
I've read about some people experiencing suspend/hibernate issues, but it's always been with the Nvidia card.

Have there been suspend/hibernate issues with the Intel card, too?

---

### Post by fragos on 2008-04-07
> **aysiu said:**
> I've read about some people experiencing suspend/hibernate issues, but it's always been with the Nvidia card.

Have there been suspend/hibernate issues with the Intel card, too?

Yes. Everything seemed to work except the wireless connection couldn't be restarted without a reboot.

---

### Post by notwen on 2008-04-08
I have had issues w/ hibernate/suspend w/ my Inspiron 1420n(w/ Intel X3100 chipset) in both Feisty and Gutsy, regardless of using Dell's custom images or not.  In Feisty I tried a number of things and was able to get hibernate working, I was in a rush and could not conclude which changes were made in order for hibernate to start working.  I have yet had the need to tinker w/ them in Gutsy and unless I get a free weekend I'll likely continue using it w/o hibernate/suspend.

---

