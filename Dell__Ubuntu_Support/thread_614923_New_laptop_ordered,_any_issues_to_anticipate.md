---
title: "New laptop ordered, any issues to anticipate"
date: 2007-11-16
forum: Dell  Ubuntu Support
---

### Post by anjilslaire on 2007-11-16
Hey everyone,
I just ordered my wife a new 1420 for Christmas, and I'm just checking in early to see if I should anticipate any issues when I flatten the drive & install Kubuntu Gutsy (currently running on my desktop)
You may be wondering, "why not just order the Ubuntu version?". Well, i wanted to upgrade the GPU, and going Windows was the only option, so I'll just wipe the Vista off, and start clean. BTW, there's an online coupon for $225 off any Inspiron over $950, so...

Specs:
Inspiron 1420, Intel Core 2 Duo T5450, 1.66GHz, 667Mhz, 2ML2 Cache
Premium Deep Rich Red with Soft Touch LCD back color - (wife said "ooh! pretty red" at one of the comercials on TV)
2GB, DDR2, 667MHz 2 Dimm
High Resolution, glossy widescreen 14.1 inch display (1440x900
NVIDIA (R) GeForce TM Go 8400M GS with 128MB dedicated graphic memory
80G 5400RPM SATA Hard Drive
Integrated 10/100 Network Cardand Modem, for Inspiron
24X COMBO CD-RW/DVD for Inspiron
Integrated High Definition Audio 2.0
Intel 3945 WLAN (802.11a/g) Mini Card

Any tips would be great. Should I expect Suspend/Hibernate to work? What about the hard drive cycling issue I've read a bit about?
If all goes well, I'll probably order myself something similar in the spring.

Thanks!

---

### Post by inchaos on 2007-11-16
That's got pretty much the same hardware as my 1420n.

Granted, it came preloaded with Feisty, HOWEVER, when I upgraded to Gutsy I did a fresh install from a live CD and it worked flawlessly.

Let me think...the only things that didn't work for me were desktop effects (but I have intel integrated graphics, which is blacklisted in Compiz-fusion, but I managed to work around that), the wireless driver is buggy, but I heard there's an alternate driver, and there's an issue with the automatic screen dimming feature...it tries to mimic a mac by having the screen dim when there's no mouse action, but it dims and brightens randomly when you have it enabled. 

Other than that, I had no major issues.  X worked, but again, you have a different graphics card...you should be fine though, nvidia's are very common and pretty well supported.

I'd say you should be good to go.

---

### Post by saru411 on 2007-11-17
im not sure of which wireless card you are going to be running with but the forums normally pop up good info on those searches. as for the video card, you will have to install the graphics drivers yourself. i believe they are part of the restricted modules that can be upgraded through ubuntu itself but if you can't seem to get it to work in know envy works fine([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) for this card. as for the hdd cycling...well every hdd in ubuntu does an fsck every 25 or so reboots. the thing is that for some reason the laptops do not show anything while running it...so it looks like your screen is dead(or bsod). i have easily worked around it by shutting down the laptop and rebooting into recovery(safe graphics mode) and letting it do the scan while i watch it. after i have booted i restart the laptop and everything works fine.

oh and if you happen to be running the dell wireless(aka broadcom 1390) this is the link to solve your problem([http://ubuntuforums.org/showthread.php?t=405990&highlight=1390](http://ubuntuforums.org/showthread.php?t=405990&highlight=1390))

hope your wife enjoys her new lappy!

---

### Post by piousp on 2007-11-17
:KS

I do have a Dell I 6400 with Kubuntu Gutsy, and only have some issues with some Function Keys and the boot screen, but everything else is working really well.

---

### Post by anjilslaire on 2007-11-17
Great! I've ordered the intel wifi card, so I should be good there, too.

Thanks everyone!

---

### Post by inchaos on 2007-11-17
Yes, my intel wifi card worked out of the box. :)

---

### Post by anjilslaire on 2007-11-21
whoo-hoo!

Its arriving today :) Can't wait to see how it's going to do!

---

### Post by anjilslaire on 2007-11-21
Ok,

Since it has Vista pre-installed, I'm also reading about the MediaDirect. It appears to be in its own partitions. I see its been causing some problems, rendering Ubuntu unbootable. 

From what I gather, to keep the MediaDirect functionality, I should
1. boot the new system in Vista, setup, 
2. reboot in MediaDirect and let that setup.
3. After everything is functioning correctly, then boot a Live CD & remove Vista & install Gutsy.

Correct? If possible I want to keep the MediaDirect bootable, but not have it hose ubuntu, and not be dual-booted with Windows (esentially keep ubuntu & mediadirect both functioning).

Thoughts? Thanks :) !

---

### Post by m1xram on 2007-11-23
The biggest thing I didn't like was the shipping date. Every week it became a week later. When I told Dell it was their last chance and mentioned I'd be posting on the forums it suddenly arrived.
Had fun with the touchpad until I got a patch .deb from Dell and was able to turn off the touch to click feature. Now both scrolls work properly.
Some audio breaks up and / or pour quality.
Got WAP2 working with my new Netgear 102 Wap by following some Internet instructions dealing with the gnome network app.
Have a message in to Joker2of5 asking about his upgrade to 7.10 on the 1420. See [[COLOR="RoyalBlue"]forum[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=615875&highlight=inspiron+1420")for message from Oct, 2007.

Overall, I'm very happy with the system.

System: Dell 1420 Inspiron
Core Duo T5250
AlpsPS/2 ALPS GlidePoint
Mobile Integrated Graphics Controller (1280 x 800)
Round Tux sticker over DELL from A G Enterprises

---

### Post by jdelaros1 on 2007-11-24
Check out the Dell Ubuntu Wiki at [http://linux.dell.com/wiki/index.php/Ubuntu_7.04](http://linux.dell.com/wiki/index.php/Ubuntu_7.04)

---

### Post by fragos on 2007-11-24
I've had a 1420n for over a week and everything works great.  Wireless roaming is ever so cool.  I'll wait until Dell blesses an upgrade to 7.10.  I can't wait for that since I run 7.10 on my desktop.

---

### Post by deserthowler on 2007-11-25
I got my 1420n with Ubuntu installed in August and all works that I tried.  I installed the codecs and audio/video works fine.  

The WiFi (Intel chip) worked out of the box (after I turned on the switch), I installed wicd which I like better than the original WiFi manager.  

There are differences in the Dell setup and a "Normal" Linux setup ... location of boot partition, etc.

I run 7.04 and haven't updated yet.  I don't see any reason to as all works.

I haven't tried desktop effects and don't plan to.  I have the Intel graphics card.

Media Direct doesn't work.  I don't care.

You might want to get the 7.04 Dell iso from the Dell site just in case.

Earl

---

### Post by fragos on 2007-11-25
> **deserthowler said:**
> I got my 1420n with Ubuntu installed in August and all works that I tried.  I installed the codecs and audio/video works fine.  

The WiFi (Intel chip) worked out of the box (after I turned on the switch), I installed wicd which I like better than the original WiFi manager.  

There are differences in the Dell setup and a "Normal" Linux setup ... location of boot partition, etc.

I run 7.04 and haven't updated yet.  I don't see any reason to as all works.

I haven't tried desktop effects and don't plan to.  I have the Intel graphics card.

Media Direct doesn't work.  I don't care.

You might want to get the 7.04 Dell iso from the Dell site just in case.

Earl

My two week old 1420n came with a Dell ubuntu CD but it self installed from one of the extra partitions Dell created.

---

### Post by anjilslaire on 2007-11-26
Well, I decided to just zero the drive to wipe any remnant of the Media Direct, then installed Kubuntu Gutsy on clean. Everything seems to be running perfectly. Since I upgraded to the Intel wifi, it's great. I've also enabled teh restricted drivers for the Nvidia 8400, and it all seems good. Also, I'll have a few weeks to get it set up perfectly & tweaked for the missus in time for Christmas.

If I run into anything while tweaking, I'll let you all know.

PS- I haven't checked the hard drive cycling issue yet. Does anyone know if the 1420 (not 1420N) has this problem?

---

### Post by mlsquad on 2007-11-27
> **anjilslaire said:**
> PS- I haven't checked the hard drive cycling issue yet. Does anyone know if the 1420 (not 1420N) has this problem?The hard drive problem will not crop up unless you manually edit a configuration file and intentionally set a specific value to laptop mode.  So unless you did that (and you would know if you did) then you shouldn't have that problem.

---

### Post by saru411 on 2007-11-27
> **anjilslaire said:**
> PS- I haven't checked the hard drive cycling issue yet. Does anyone know if the 1420 (not 1420N) has this problem?

this problem will not surface until you have rebooted the laptop at least ~25 times. ubuntu automatically checks the hdd every ~25 cycles. there is a thread that allows you to change it to more if you like.

---

### Post by brownicb on 2007-11-28
> **anjilslaire said:**
>  BTW, there's an online coupon for $225 off any Inspiron over $950, so...


So how do you get this extra $225 off?  I've been thinking about getting the 1420N.

---

### Post by anjilslaire on 2007-11-29
Thanks for the heads-up about the drive issue.
The $225 off coupon expired on the 21st, just before Thanksgiving. However, a quick google shows the following new deals:
[http://www.couponmountain.com/Dell-coupons-deals.html](http://www.couponmountain.com/Dell-coupons-deals.html). All you really need is the online coupn code, which you put in when ordering. You don't usually need to use their link. :)

Either way, it worked for me when I ordered.

---

### Post by inchaos on 2007-11-30
The hard drive issue for me, at least, if we're talking about the same one, is that the motherboard essentially cuts the power to the HDD before the heads have a chance to park on the drive.  Every time you shut down is like if you kill the power by holding down the power button for four seconds.  The HDD makes a terrible noise.  

For me, this was resolved by a kernel update when I first got the computer and Feisty was the most recent distro, but now it can be resolved by installing the recommended updates and/or updating to Gutsy.

---

### Post by anjilslaire on 2007-12-22
No, I'm talking about the Load_Cycle_Count issue, as documented here: 

[http://ubuntuforums.org/showthread.php?t=591503 ]("http://ubuntuforums.org/showthread.php?t=591503")

which apparently is greatly reducing the life of laptop hard drives. 
Any thoughts?

---

### Post by natehall on 2007-12-22
> **saru411 said:**
> ...well every hdd in ubuntu does an fsck every 25 or so reboots. the thing is that for some reason the laptops do not show anything while running it...so it looks like your screen is dead(or bsod).! My 1402 N does the disk check every 39 boots ( Why 39 I may never know) It takes awhile but it does have a terminal screen that displays the amount of scan completed.

---

### Post by anjilslaire on 2007-12-26
bump...

Any thoughts/experience on the 1420 and Load_Cycle_Count?

Thanks

---

### Post by natehall on 2007-12-27
> **anjilslaire said:**
> bump...

Any thoughts/experience on the 1420 and Load_Cycle_Count?

Thanks

I downloaded  smartctl (just to see if I'm affected) It parks every time at shutdown for mine. Not a loud noise or anything like that, I tried a shutdown patch and it made no differance.

---

### Post by trooperchix on 2007-12-27
Dood, I ordered the same system, have had it for over a month now.  Slick as fresh snot.  You'll eat this sucker up.  I even have my non-computer savvy partner getting it now...  Enjoy!!!

---

### Post by anjilslaire on 2007-12-28
yup, got this one for the wife. I'll order another for myself in the spring :)

So no problems with the Load_Cycle_Count issue, then?

---

