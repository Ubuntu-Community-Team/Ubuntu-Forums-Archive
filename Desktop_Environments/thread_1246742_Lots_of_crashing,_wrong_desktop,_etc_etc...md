---
title: "Lots of crashing, wrong desktop, etc etc.."
date: 2009-08-22
forum: Desktop Environments
---

### Post by w00ly on 2009-08-22
I've just installed kubuntu 9.04 recently on two PCs. One's an older athlon 1600+ w/ 512mb and geforce 5200fx and it seems to run it fine. I started it up after 1 install, did a dist upgrade and have barely rebooted it in a month. It can get a little slow with too many apps open and too many effects on but I cant say windows would have done any better. 

My HTPC on the other hand is an athlon 64 3200+ (x86 install) w/ 1G ram and 7300GT and I've had nothing but problems with it. The main issue i'm having is a "flicker of death". I'll be doing something and the screen flicks black for a split second then comes back and crashes. If i'm watching a video, the video will stop (or jitter then come to a stop). Audio will continue for a few seconds then it stops. I can still move my mouse around but there's no way to exit it (no alt sysrq r/k, no ctrl alt backspace, nor ctrl alt f1). I can only hold the power button until it restarts.

The things I've been doing when it's crashed like this include: mousing over the kickoff menu, adjusting transparency in AWN, flushing cache (or whatever the last step is) while burning in k3b, "writing ISO" when converting an avi file to DVD with BOTH convertxtodvd (in wine) and DeVeDe (edit: and launching dolphin to test prelink after setting it up.) It doesnt happen every time...i can click the k menu most of the time without a crash, and I watched an h264 tv show on there without a hiccup. I'd say it probably would crash on the "writing iso" stage of video conversion 100% of the time since it happened with both programs (but to test would require another hour of video conversion just to fail..). I've tried 180 drivers from the "hardware drivers" application as well as the latest 185 from nvidia's site. Turning off the desktop effects seemed to help (but i think I may have even had a crash then too). I  had to turn desktop effects back on though so I could run AWN.

When I installed AWN I saw that it installed gnome which I thought "ok, I can switch back and forth between them and that'll be neat", even though i've never really liked gnome. When I went to adjust the translucency on AWN it crashed again and this time upon reboot it auto logs me in (I set auto login but KDE never would :confused:) and starts giving me all sorts of gnome-related errors "nautilis cant find this", "gconf sanity check", "something about a panel that needs to be deleted..". Now I cant figure out how to get it to automatically start KDE instead of Gnome (nor switch to it from gnome without using alt sysrq k to get back to the login screen and select KDE). Why would gnome just take over my desktop like that? I never told it to use gnome as my default window manager! /etc/X11/default-display-manager is set to /usr/bin/kdm so why does gnome start? I'd love to remove gnome if I could and still keep AWN.

The last problem i'm having is hanging on reboot. I've never been able to type reboot on either computer or click the reboot button and have it completely reboot. The kubuntu splash comes up but then the screen goes blank and the monitor goes into standby and the cd rom drive's activity light starts blinking. Again the system is unresponsive to any inputs besides holding the power button (and this cant be very good for my system, especially with the amount of times I have to do it now!) 

As you can see, i've been having quite a headache with this system. If anyone can help put an end to this misery, i'd be extremely grateful!

```
htpc@htpc:~$ uname -a
Linux htpc 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
htpc@htpc:~$ lspci|grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GT (rev a2)
```Also, I have no idea how to debug these kinda crashes so whatever commands you guys need me to run to get more info, let me know! TIA!

tl;dr Frequent screen flicker crash, dont know how to start KDE automatically (again), hanging on reboot\

*edit*: another crash...had utorrent off, clicked a torrent and as soon as it got to around 300 kb/sec it locked up and i cant even move the mouse

---

### Post by w00ly on 2009-08-22
Removed AWN and Gnome in favor of cairo...now I just need this crash and the reboot hang fixed :\

edit: crashed twice while watching one video...can someone PLEASE at least tell me what commands to run with xine so I can accurately figure out what's causing this??

---

### Post by krazyd on 2009-08-23
I'm not sure if you have much important data to back up, but I'd go for the reinstall. Those crashes/flickering/video issues sound driver related to me. If you reinstall, try playing video before you install the nvidia drivers to see if you have the issues then.

The nvidia drivers are known to be buggy, and there's not much you can do to debug them because they are proprietary. You could try the forums on nvnews.net, or try a different version from nvidia.

Also, I've never had much luck with AWN in KDE. You could try a similar plasmoid such as Smooth Tasks: [http://www.kde-look.org/content/show.php?action=content&content=101586](http://www.kde-look.org/content/show.php?action=content&content=101586)

---

### Post by w00ly on 2009-08-23
Thank you for the reply! Are the drivers that come from the "hardware drivers" application the same way? It said 180 was recommended but I still had crashes with it. I dont believe I had any crashes before installing the drivers but if I dont install the drivers, will I not be able to get a proper resolution or any desktop effects?

---

### Post by krazyd on 2009-08-23
> **w00ly said:**
> Thank you for the reply! Are the drivers that come from the "hardware drivers" application the same way? It said 180 was recommended but I still had crashes with it.
Unfortunately, yes. Search [nvnews forums]("http://www.nvnews.net/vbulletin/") for your symptoms - someone there may have found a solution.
> **w00ly said:**
> I dont believe I any crashes before installing the drivers but if I dont install the drivers, will I not be able to get a proper resolution or any desktop effects?
That's right, but unfortunately that's the price of proprietary drivers on linux. Again, try nvnews forums as there are a lot of linux users there who will probably be able to help.

---

### Post by w00ly on 2009-08-23
I see. I'm searching through there now and lo and behold the first post on the linux forum is about a flicker/crash lol... He says he's using version 180.60 where I skipped that (after installed .44 with the hardware drivers program) to go straight to 185 so I'll give that one a shot and see if it helps
If that fails are there non-proprietary drivers for the 7300gt that I could find somewhere?

Edit: success! I didnt even know there were 190 drivers out but I found em on that site, installed, turned on full effects and havent had a hiccup! Thanks for pointing me in the right direction sir, you just saved me a ton of money on headache medicine :lolflag:
Now I just have to find a quick vnc viewer/server,  a way to mount a network share after WPA authentication and how to cleanly unmount it on reboot so it doesnt hang and i'll be content. BTW, I found a plasmoid on synaptic that was closer to AWN like I was looking for called "plasma-widget-daisy". It's definitely faster but not nearly as configurable but it'll certainly work :)

Edit2: Grr, another crash! This is so ridiculous and is definitely starting to get old :mad: It seems much more stable with these new drivers and I'm able to go longer without a crash but I was only clicking the multimedia tab in system settings when it happened. SIGH

---

### Post by w00ly on 2009-08-23
Bump!
edit: How anyone can say linux is ready for the mainstream is beyond me. I'm sorry for the rant but I've been using linux about every 2 years since Redhat 5.2 came out in 1998 and every time I install it, I have a major issue such as this that cannot be fixed and i'm forced to reinstall windows. What's your average novice user supposed to do when they have a major issue that makes their system unusable, they post it on 3 different forums (here, nvnews and linuxquestions) and get 1 person to reply with 300+ combined views and not a single view on their bug report between all 3? If 300+ people dont know the answer, how is a novice supposed to??

I just really wanted this to be the final time that I switched from windows but it's sad (and surprising) to say windows is just lightyears ahead, and always has been, in terms of stability. I feel like since installing kubuntu this latest time I've probably restarted this PC more times than I have my entire time using windows (or at least XP where you didnt have to restart every time you installed somethign lol..)

---

### Post by krazyd on 2009-08-23
hey w00ly, I feel your frustration - I have a notebook with a nvidia card too, that doesn's suspend/resume, sometimes crashes when watching video etc.

your problem isn't really linux or ubuntu's fault though: blame nvidia for their dodgy drivers. Nvidia is the only major graphics manufacturer still unwilling to open their hardware and support an open source driver. Intel 3D compiz and video works out-of-the-box on Ubuntu 9.04. Many ATI cards do too, except for some of the more recent ones, and those will probably be working in time for 9.10 (a couple of weeks ago, developers got compiz working on the latest cards with open source drivers).

Basically, nvidia is one of the most linux-unfriendly chipmakers out there. If they were serious about linux and provided drivers with the same stability as their windows drivers, or if they provided developers and hardware documentation for open source drivers like Intel and AMD/ATI, then these forums would be about half as busy.

for more info, see here: [http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS](http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS)
and here: [http://blogs.zdnet.com/open-source/?p=2587](http://blogs.zdnet.com/open-source/?p=2587)

---

### Post by ckonestroh on 2009-08-23
Funny,

1. You insult Linux/Ubuntu users...
2. Tell me how windows is better....
3. You get free tech support....
4. You didn't have to pay any money to get help...
5. You didn't have to bye the OS...
6. You never check the hardware compatibility list....
7. Tech support isn't from India were I can't understand you do to your accent 
8. You claim your a novice linux user???? (scratching my head)
9. You fix the problem       2 thumbs up  :) :P
10. You reply and complain again        2 thumbs down... :( :confused:

Final Thought ----

We are a community of friendly people we didn't rip on you for using windows??? Maybe you should be nice to use???? since we are nice to you!!!

---

### Post by krazyd on 2009-08-24
> **ckonestroh said:**
> Funny,
*snip*
Funny, I don't recall you 'being nice' or contributing anything constructive to this thread at all. Please post your flamebait elsewhere.

---

### Post by w00ly on 2009-08-24
> **ckonestroh said:**
> Funny,

1. You insult Linux/Ubuntu users...
I'm sorry for ranting but can you blame someone for being upset when their system isnt working? I never insulted any "users" and was for the most part trying to be nice and polite..
> **ckonestroh said:**
> 2. Tell me how windows is better....
I dont have to reboot by holding down the power button because watching a video freezes the computer
> **ckonestroh said:**
> 3. You get free tech support....
4. You didn't have to pay any money to get help...
and no one has so far out of 300+ people. 1 person at nvnews looked at my logs... krazyd replies and is trying to be helpful which I appreciate but I've already reinstalled multiple times it seems like there has to be some way to fix this...all nvidia cards cant be having this problem, i'm using one on a different system now.
> **ckonestroh said:**
> 5. You didn't have to bye the OS...
I wouldnt
> **ckonestroh said:**
> 6. You never check the hardware compatibility list....
it's a regular computer from dell with a regular processor from amd and a regular video card from nvidia...what's not to be compatible. What I dont get is the computer with the 5200fx works and the computer with the 7300gt doesnt
> **ckonestroh said:**
> 7. Tech support isn't from India were I can't understand you do to your accent 
...irony?
> **ckonestroh said:**
> 8. You claim your a novice linux user???? (scratching my head)
Yes, as I said I've installed it roughly five times in 10 years. Every time I spend hours upon hours trying to fix major problems so it doesnt last for long. I can do most of the basic stuff but I have no idea how to troubleshoot a failure like this. That's why I'm here...where people who are more familiar with the OS can hopefully help me. Yet every time I install it there are people like you criticizing me when i'm trying to get help
> **ckonestroh said:**
> 9. You fix the problem       2 thumbs up  :) :P
10. You reply and complain again        2 thumbs down... :( :confused:
I said the new drivers were more stable but it was still crashing

> **ckonestroh said:**
> Final Thought ----

We are a community of friendly people we didn't rip on you for using windows??? Maybe you should be nice to use???? 
I said I apologized for ranting but how can someone not be frustrated when their computer hasnt been working for so long :| I just wanted to get some help and I have this on 3 forums but no one will  (besides krazyd's.) I never insulted anyone personally just the OS

> **ckonestroh said:**
> since we are nice to you!!!
What's #7 then?

edit: sorry krazyd, he flamebaited me lol :|

---

### Post by ckonestroh on 2009-08-24
Well after sucking you into this discussion here is the answer...

Found it at a nvida furom ...

[http://www.nvnews.net/vbulletin/showthread.php?t=80888&highlight=7900+linux]("http://www.nvnews.net/vbulletin/showthread.php?t=80888&highlight=7900+linux")

Not sure how you enter this data into the kernel?????


Default Re: Geforce Go 7950 GTX stability problems
Quote:
Originally Posted by netllama
[COLOR="Blue"]Based on that parameter, it seems like the your system needs special GPU tuning to function properly. Unfortunately, that isn't possible in Linux for mobile GPUs right now.
[/COLOR]

[COLOR="Green"]For once, I'm glad to say this: bull[/COLOR]

[COLOR="Green"]I now have a perfectly working nvidia driver in my linux by passing a parameter to the nvidia kernel module:[/COLOR]

Quote:
[COLOR="Blue"]modprobe nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
[/COLOR]
[COLOR="Green"]
I'm not sure if this brings more problems later on or if you can even recommend people to try this, but it certainly fixed my case. 2D works fine, 3D works fine, performance is sweet.[/COLOR]

Thank you


This post from the website seems to imply that all nvidia card series 7000 have this problem....

I also didn't get your video card type first you post it is a 7300 gt and later a 7900 gt... which video card?


make sure you read the entire post!!!!


later



chris....


Also read this

[http://www.nvnews.net/vbulletin/showthread.php?t=124186&highlight=7900+linux](http://www.nvnews.net/vbulletin/showthread.php?t=124186&highlight=7900+linux)

---

### Post by ckonestroh on 2009-08-24
By the way this video card series had incredible problems on both windows and linux... only the nvida drivers seem to be the working copy from the company... In fact some posts led on to say even the microsoft drivers didn't work....

Crazy card I would replace this card with a 8600 series from nvida....

for about $90 to 100 bucks since your not plaining on using windows again are you???




later


chris


know this the 7900 gt out preforms the 8600 gt... But for the price you can't beat the 8600 ... more bang for the buck....

went to newegg.com found this

EVGA 256-P2-N753-TR GeForce 8600 GT 256MB 128-bit GDDR3 PCI Express x16 HDCP Ready SLI Supported Video Card 

Price is around $50 dallors....




User: James

I purchased this card to set up a second monitor. It was the perfect card at the right price for the job. Keep in mind that I don't game. (I did however try out UT2004, which it handled at the highest settings with no problem, nothing really to brag about since that game is old.) I run Linux on a Dell 531, but I did throw it in my Vista box just to see how it would run and it did not have any problems. In Ubuntu 9.04, the restricted drivers found it and install the nVidia software. Setting up Duals in Ubuntu was a snap, the nvidia control creates a x.org file, which you just copy and paste into your current x.org. This card is very quiet. This is a great card for a non-gaming system.

---

### Post by w00ly on 2009-08-24
Wow, I dont know how you found that but thank you! I've got an ugly workaround right now: swapped the 5200fx into the htpc and the 7300gt into the desktop...now neither computer can play HD well lol :) 
I wonder which setting to use though? One says 
> [FONT=monospace]
[/FONT]Option "RegistryDwords" "PowerMizerLevelAC=0x3"[FONT=monospace]
[/FONT]Option "RegistryDwords" "PowerMizerLevel=0x3"While the other says
> Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x1; PowerMizerDefaultAC=0x1"So one's high, one's low. One has PerfLevelSrc and the other doesnt. One sets "PowerMizerLevel" and the other sets "PowerMizerDefault". I guess they should both do the same thing...I'll just set it on 2 for now and see what happens. Would leaving it on 1 be a bad thing? Right now NVIDIA X Server Settings says powermizer's on 0 max performance
I'll swap em back and let you know how it goes! Thanks again!

---

### Post by w00ly on 2009-08-24
The powermizer settings dont seem to want to take. Here's my device section in xorg.conf
> Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x1; PowerMizerDefaultAC=0x1"
EndSectionI got a crash but I checked Nvidia X Server Settings is still sayign powermizer is still set on 0 for max performance. I've tried PowerMizerDefault and PowerMizerLevel and putting the option before identifier and tried it after VendorName as well. I can never get Nvidia X Server Settings to say powermizer's on a different level. Also tried PerfLevelSrc=0x2222 by itself but it's still crashing. This fix seems to be mostly for people using laptops though :| Thanks for the help anyway

---

