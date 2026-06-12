---
title: "Ubuntu Jaunty crashes"
date: 2009-04-25
forum: General Help
---

### Post by Deatzo Seol on 2009-04-25
After upgrading to Jaunty, every four to six hours or so, Ubuntu randomly crashes: everything becomes suddenly completely unresponsive, and I need to reboot the computer.
Today, however, after yet another crash and subsequent reboot, Ubuntu decided to crash right after loading Gnome, leaving me with a completely unresponsive login screen (oddly enough, with a blinking cursor) and no way in hell to use the computer ...
I tried to boot with another kernel, but seemingly initramfs fails to automatically load it (I'm stuck with an '(initramfs):' bash like screen...).

So, now I'm like, what the fu&#1089;k??? :confused: 
Any help?
Thanks!

---

### Post by The Squig on 2009-04-25
cant help but what you described happend to me ~10mins after the upgrade. Surprised me but it hasnt happend since.

---

### Post by Deatzo Seol on 2009-04-25
Okay, I went into recovery mode, and edited /etc/gdm/gdm.conf to automatic login, so now I get the 'Your session lasted less than 10 seconds [...]' but '.xsession-errors' in completely empty!
I think it may be an X or Gnome issue, since the problem never happens on the ttys...
What should I try? Reinstall X or Gnome?

---

### Post by Deatzo Seol on 2009-04-28
Right ... I completely reinstalled Jaunty from scratch.
Turns out the same fu&#1089;king problem still exists! Only it got worse! Now, Ubuntu randomly freezes already after one or two hours!
Plus, the bloody shagging logs don't seem to give me any help!
</rant>

Any help? Free :popcorn: for anyone who can!

---

### Post by Meow27 on 2009-04-28
are you using restricted drivers?

---

### Post by pokogr on 2009-04-28
> **Deatzo Seol said:**
> Right ... I completely reinstalled Jaunty from scratch.
Turns out the same fu&#1089;king problem still exists! Only it got worse! Now, Ubuntu randomly freezes already after one or two hours!
Plus, the bloody shagging logs don't seem to give me any help!
</rant>

Any help? Free :popcorn: for anyone who can!

It seems to me that it is a graphics problem. Have you installed your vendor's driver? Try disabling compiz to see if this keeps going on. If not then it is definitely the g.card. You can have music playing in the background an see if even the music stops when it crashes.

---

### Post by Deatzo Seol on 2009-04-29
To answer your questions: I'm using Metacity, when it freezes, sound 'hangs', and I'm using Ubuntu's radeon driver, since fglrx has been obsoleted (I have a X1300 Radeon card, btw)...

---

### Post by Meow27 on 2009-04-30
ok ive confirmed this on my dell e521

useing a restricted driver with nvidia 7300 LE will freeze the system when running flash for 4 minutes

---

### Post by Deatzo Seol on 2009-05-04
... any solutions?

---

### Post by Gck2702 on 2009-05-04
I have exactly the same problem! And I cannot do anything correct it. I'm very very very close to giving up...

---

### Post by schickb on 2009-05-04
I have the same problem with 9.04. My system hard-freezes sporadically so that it can't even be pinged. 

I have an nVidia 7300 GS running the binary drivers and Compiz set to "Normal". I'm going to try with Visual Effects set to none, and if that doesn't work go back to the open source drivers.

I was running my system for a while without problem on the open source NV driver without visual effect, so I am fairly certain the problem is either the binary driver or Compiz.

---

### Post by schickb on 2009-05-04
> **schickb said:**
> I have an nVidia 7300 GS running the binary drivers and Compiz set to "Normal". I'm going to try with Visual Effects set to none, and if that doesn't work go back to the open source drivers.

Well I tried running with no visual effects, and hit the same hard-freeze. I disabled the binary nVidia drivers and the rest of the day was free of problems. Sort of a bummer because Ubuntu really looks nice with the "standard" compiz effects enabled.

I really wish the graphics card makers would either significantly improve the quality of their binary drivers or just open source them once and for all.

---

### Post by Nycticorax on 2009-05-06
We're also getting hard-to-diagnose system freezes with jaunty on a laptop (Thinkpad T40). I've disabled wireless in BIOS and turned Compiz off, and they still occur. It seems to happen less frequently with the 2.6.27 kernel, but I haven't got much data to base that on. This is with an ATI Radeon Mobility 7500 Graphics Card -- what exactly is the procedure for switching between the different graphics card drivers and what choices do I have? There's a thread with possibly similar problems at 

[http://ubuntuforums.org/showthread.php?t=1145879]("http://ubuntuforums.org/showthread.php?t=1145879")

---

### Post by kemorc on 2009-05-06
I get lockups too... and I've got a ATI Radeon HD 3870 (soon to find the garbage bin).  Glad to see that everything seems to point to graphics drivers.

The second I load up display properties... my CPU starts heating up and one core hits 100% and will not drop even after managing to shut down display properties.  Some of my issues were fixed by getting rid of CCC... that was the BIGGEST headache right there.

---

### Post by schickb on 2009-05-07
> **Nycticorax said:**
> what exactly is the procedure for switching between the different graphics card drivers and what choices do I have? 

Try disabling the proprietary driver. Select the System -> Administration -> Hardware Drivers. Then when the dialog opens select your video driver and click "Disable". 

This will disable the "restricted" proprietary driver and switch to open source driver instead. I think you have to restart X (or reboot if you don't know how), for that to take effect.

---

### Post by sb. on 2009-05-09
same problems here.  sudden and random crashing.
desktop effects have always been disabled.

ati radeon x1650
not sure about the restricted drivers but will look into it.

---

### Post by Nycticorax on 2009-05-09
When I go to System -> Administration -> Hardware Drivers it searches and then says "No proprietary drivers are in use on this system". So I guess I'm already using open source drivers for the ATI Radeon graphics card. (I can see a loaded kernel module called "radeon" that seems to be a GPL'd driver for ATI Radeon). So doesn't look like that's going to be a solution for me.

---

### Post by Nycticorax on 2009-05-09
This is a serious problem now: the machine is almost unusable. I hope this really is a software problem and not a hardware problem. We are finding that after a crash the laptop often requires a few attempts before it starts to boot (i.e. pressing the power button just brings a few LEDs on but won't even bring up the BIOS splash screen). Also once it agrees to start it can crash during the Ubuntu boot sequence while there is the Ubuntu splash screen, but before the X graphics have properly been started (Afaik). This is with a Thinkpad T40. Is anyone having similar experiences? Does anyone believe that our problem could be a software problem?

(Why) is there nothing written to any log file? Does anyone know whether/where this is receiving attention as a bug by Ubuntu developers?

---

### Post by zbeekman on 2009-05-09
I have similar issues on my Thinkpad T60 2007 63u with an 128MB ATI Mobility RADEON X1400 card.  It seems that my card gets extremely hot when watching online video etc. and causes the computer to freeze or auto-shutdown.  This could explain some of these issues people are having if they try immediately to reboot their machine: perhaps let some of that silicon cool off first.  Since 8.10 the proprietary ati drivers are no longer available by default.  (They seemed to do more harm than good anyway.)  Either way it seems to me that either the thermal management/ati hardware is not up to par, or that the drivers need more work.  My graphics card gets up to around 200 deg. F before my machine powers down.  :cry:  If any one finds a solution please let me know.

Thanks
Z

---

### Post by The Cog on 2009-05-09
Are you using EXT4? There have been suspicions that EXT4 might be the cause of lockups. Others are sure it's traffic on their wireless adapters that causes it.

---

### Post by Deatzo Seol on 2009-05-12
I'm using ext4, yes.
I thought ext4 lockups were a thing from the past (which was the reason to actually upgrade to it *slaps self*)...
Plus, it happens about three or four times *per day* ... I dunno, but that does sound a little much to me?

---

### Post by schickb on 2009-05-12
> **sb. said:**
> same problems here.  sudden and random crashing.
desktop effects have always been disabled.

ati radeon x1650
not sure about the restricted drivers but will look into it.
For me at least, just disabling desktop effects was not enough. I had to stop using the restricted driver entirely. Although it sounds like that hasn't solved it for some. Its been a week without a lockup for me... big improvement over 3-4 times a day!

---

### Post by mr.thraz on 2009-05-23
I'm having the same problem.

I installed jaunty ubuntustudio on my hp dv 9000 ,amd64 x2, 4 gigs of ram.

ram passed, home folder is unencrypted, brodcom wireless drivers is not installed yet, nether is  restricted navida drivers. 

reason being it won't stay stable long enough to update the machine.

is jaunty just not working on laptops wats going on?

---

### Post by Cherry Cotton on 2009-05-23
Yes, Jaunty has been a disaster for my ThinkPad X61 Tablet. I thought it was something specific to my machine, so I made [a thread about it here]("http://ubuntuforums.org/showthread.php?t=1167523"), but it looks like this is a general problem. (I’m not using any proprietary drivers, ext4, or Compiz, incidentally.)

How can we get this to the attention of the Ubuntu devs? It’s making my computer nigh unusable.

---

### Post by mr.thraz on 2009-06-02
> **mr.thraz said:**
> I'm having the same problem.

I installed jaunty ubuntustudio on my hp dv 9000 ,amd64 x2, 4 gigs of ram.

ram passed, home folder is unencrypted, brodcom wireless drivers is not installed yet, nether is  restricted navida drivers. 

reason being it won't stay stable long enough to update the machine.

is jaunty just not working on laptops wats going on?




still nothing on this?

---

### Post by arupgowda on 2009-06-03
I have had the same ****** prob man. I am thinking about installing KDB and entering the debugger some how. I have HP DV6000 which worked beautifully with IBEX and prev versions. Jaunty came in and spoilt the party. I use restricted drivers too Nvidia 7200. AMD 64bit. 

Any help ?

---

### Post by johndoe48239 on 2009-06-05
Hi,
I have the same problem on my asus laptop (integrated intel card)... The system freezes and is totaly unresponsive, except for the mouse (only movment). The only way out is a hard restart. The crashes seem to be random...

I have been looking at the log files and every time prior to the crash this is what's going on: (this is from the kernel log file)

```
[drm] Initialized i915 1.6.0 20080730 on minor 0
[drm:i915_setparam] *ERROR* unknown parameter 4
[drm:i915_getparam] *ERROR* Unknown parameter 6
[drm:i915_getparam] *ERROR* Unknown parameter 6
```

every time after those messages there are these two messages in the kernel log:
```
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: no IPv6 routers present
```

one time I also had this in the kernel log between the drm:i915 error messages:
```
mtrr: no MTRR for f0000000,8000000 found
```

The way I see it, this crahs problem is related (at least in my case) with xorg and the intel graphics driver.
I didn't have this problem on previous Ubuntu releases and I have all the same things installed like I had on 8.10

Usually the crash happens when firefox is opened (both whan flash content is present and not)...

Any idea how to fix this problem?

---

### Post by Entropy_Sam on 2009-06-05
> **Meow27 said:**
> ok ive confirmed this on my dell e521
 
useing a restricted driver with nvidia 7300 LE will freeze the system when running flash for 4 minutes
 
Does the mouse cursor respond to movement, but nothing else at all responds? Do you get some flickering on the screen?
 
I recently switched to an nVidia card from an ATi card and started to get these crashes. In both Ubuntu and XP. I had the card replaced, reinstalled it last night and got it all running. This morning, it happened again.
 
One thing I've noticed is that I've pretty much always got Firefox open when it happens. That shouldn't really be remarkable, given that Firefox is easily my most-used application, and I haven't noticed particularly that I've had Flash running, but I'll look out for that possibility now. I'm running the latest nVidia proprietary drivers on AMD-64 Ubuntu.
 
Wondering if it's a driver bug...?
 
Edit: Should add that after getting these crashes with the nVidia card, I switched back to my older ATi card/open source drivers for a few weeks while awaiting my replacement card and crashes stopped again completely. :-p Wish I'd just stuck with ATi now - I only went the the nVidia card because the proprietary support was supposed to be better...

---

### Post by betete on 2009-06-05
johndoe48239, I have the exactly same problem. I experience random crash and the only thing working is the mouse cursor. I use the Alt+Print Scrn+r-s-e-i-u-b to reboot the system.

I see the same lines in kern.log:
[drm:i915_setparam] *ERROR* unknown parameter 4

I read that this is a bug related to intel driver, and some one suggested adding the following line in xorg.conf in Device Section:

        Option "ExaOptimizeMigration" "off"

After doing so, I had no crashed for a day (yesterday). But today the system crashed again.

Here is the link to the bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/363900](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/363900)

Please, can anyone help us?

---

### Post by johndoe48239 on 2009-06-05
betete, I'll give it a try with the editing of the Xorg.conf file...

A few hours ago my system crashed again... this time no application was runing (like firefox), the screen saver was activated and shortly after that the system just froze. I was able to move the mouse, but the keyboard was not responding...

---

### Post by felixfurtak on 2009-06-07
Yep, I had exactly the same problem. It's been driving me mad, thinking there was some hardware problem. It seems to be random, but happens mostly when adobe flash is playing or there is some input on the touchpad or keyboard. I can leave the computer idling for a long time and it's fine, but any kind of window manipulation seems to result in 'random' but regular hard crashes.

I was using an Acer laptop with Composite disabled and no restricted drivers, Intel 915 integrated graphics and Intel 2200BG wireless card. The last 3 entries in kern.log pointed towards either the 915 graphics or the touchpad or some networking problem. I tried reverting to previous intel xorg 2.4 drivers and this didn't work. 

Basically I gave up on the Jaunty kernel and upgraded to Karmic. I can confirm that the problem has now completely gone with 2.6.30-8-generic kernel.

It's pretty easy to do the upgrade in case you're wondering. Just edit your /etc/apt/sources.list and change every reference to 'Jaunty' to 'Karmic'. Then 'sudo apt-get update' followed by 'sudo apt-get dist-upgrade'.

Obviously this work-around is slighly off-topic, but it works for me so I thought I would share it.

Good luck Ubuntu family!

---

### Post by AlexsAntidote on 2009-06-07
> **felixfurtak said:**
> Yep, I had exactly the same problem. It's been driving me mad, thinking there was some hardware problem. It seems to be random, but happens mostly when adobe flash is playing or there is some input on the touchpad or keyboard. I can leave the computer idling for a long time and it's fine, but any kind of window manipulation seems to result in 'random' but regular hard crashes.

I was using an Acer laptop with Composite disabled and no restricted drivers, Intel 915 integrated graphics and Intel 2200BG wireless card. The last 3 entries in kern.log pointed towards either the 915 graphics or the touchpad or some networking problem. I tried reverting to previous intel xorg 2.4 drivers and this didn't work. 

Basically I gave up on the Jaunty kernel and upgraded to Karmic. I can confirm that the problem has now completely gone with 2.6.30-8-generic kernel.

It's pretty easy to do the upgrade in case you're wondering. Just edit your /etc/apt/sources.list and change every reference to 'Jaunty' to 'Karmic'. Then 'sudo apt-get update' followed by 'sudo apt-get dist-upgrade'.

Obviously this work-around is slighly off-topic, but it works for me so I thought I would share it.

Good luck Ubuntu family!

I was just about to post a question here on the general help forums regarding upgrading to the karmic kernel, and to see if anyone else had overcome their system halt issues by doing so... Thank you for answering my question before I even asked it!

and for anyone else looking for answers about this issue (and not quite ready to just upgrade your kernel), I too have been having problems with Jaunty crashing. It's not just X crashing, it's a kernel crash. And it happens on Ext3 not just Ext4. From everything I've read as well as test for myself it seems to be a combination of hardware/kernel problems (graphics card and/or wifi card w/Jaunty kernel).

Thanks again!

---

### Post by sabmo on 2009-06-10
hmm.. I was going to start a new thread because I figured I was all alone but then decided to search and I can see I'm very much not alone with this.

I am also seeing regular crashes and its really pissin me off.

Jaunty-AMD64 default
Restricted Drivers
EVGA Geforce GTS-250 video card
Intel Core2Duo CPU 
ext3 

I'm glad to hear that karmic fixes the problem, but how long till karmic comes out? I hate running bleeding edge software, I hate crashing, I need a solid system.

edit: removed whining ;P

---

### Post by Crunchy the Headcrab on 2009-06-18
I'm crashing often in 9.04 as well.  After much troubleshooting the problem seems to come down to my NVIDIA 9800M GS.  Whenever I update the graphics driver, either using Ubuntu's restricted drivers, or by using the drivers available at Nvidia.com the computer becomes unstable shortly after.  Usually what happens is that firefox crashes.  Then if I try to open any programs I just see a window open but nothing is in it.  If I open terminal, for example, I just see a blank window that says Terminal at the top.  Nothing runs.  If I hit ctrl + alt F1-F6 to bring up the command line, it usually works fine, but not always.

Update:
I think I've narrowed it down to using desktop effects for my machine.  I can use the drivers from Nvidia's site perfectly as long as I don't enable desktop effects.  If I do that then things start getting sketchy.  At least I can run my display at a decent resolution.

---

### Post by Deatzo Seol on 2009-06-27
Anyone has other thoughts?

I noticed [this thread]("http://ubuntuforums.org/showthread.php?t=859798") had exactly the same problem, and the solution of using the RT kernel popped up but, unfortunately, it seems the RT kernel is a bit outdated, so I can't test it.

---

### Post by philcamlin on 2009-06-27
graphics issue :(

---

### Post by Deatzo Seol on 2009-06-30
All right then, I agree it's probably a graphics problem :( ...
but, is there a solution?

---

### Post by Danbo19 on 2009-07-01
I am having the same problem on a Dell Latitude D630. Jaunty ran perfectly fine for about two months until random crashes started occurring. Rarely at first, but slowly they became more and more frequent. This week I haven't been able to keep it on for over a day and right now it refuses to boot at all. I get a couple of LEDs on, but no BIOS screen. 

I noticed last night that there were  two entries for Ubuntu in GRUB, one with the older kernel. I booted into that one and it ran all morning fine while I was in class. I shut it down when I left for home and now it won't boot at all.

Also when running mem-test I got a similar result as above. At the top it said it was only about 88% done, but at the bottom it said it was all finished and no errors were found.

Edit: When it crashed the screen does flicker. Or more like flash crazily.

---

### Post by johndoe48239 on 2009-07-04
It's been a month since my last post in this topic... I didn't have time to play with this problem so I went back to 8.10

These crashes are actualy kernel crashes that happen on systems with intel integrated video cards.

As far as I have seen, a possible solution is to downgrade the intel driver. You can find the instructions here: [https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Reverting%20to%20the%20intrepid%20version%20of%20the%20driver](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance#Reverting%20to%20the%20intrepid%20version%20of%20the%20driver)

I hope this helps!

---

### Post by Deatzo Seol on 2009-07-15
Well, I have good news. The 2.6.28-13 kernel seemed to have solved (most) of the problem. I only get crashes about once per week or so... which is quite good compared to four or five per *day*.
Let's hope the next kernel completely solves the problem.

---

### Post by Stan_1936 on 2009-07-19
I get complete screen lockups.  It does not seem to be X crashing.....it's just that the entire screen is just frozen.  I can't do anything.

I also get a beep when restarting/shutting down the system.  This is not as big a problem as the lockups, but worth mentioning in this thread, I think.

I will not be using Jaunty on this machine.  Sorry.  I will not be using Ubuntu on this machine for atleast 2-3 years.  From my experience, Ubuntu works better with older(not too old) hardware.  Sigh!

---

### Post by thijsz on 2009-08-03
same issue

mostly happens when running firefox

- using the RT kernel : 2.6.28-3-rt #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:11 UTC 2009 i686 GNU/Linux
- no restricted drivers installed
- no log entries
- integrated intel graph card : 00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
- visual effects : None
- system : dell PIV (service tag h680v1j)

how do i check what graphics drivers i have installed ?
i would like to try this : [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4#Rolling%20back](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4#Rolling%20back)

cmon guys, lets not give up !!!
yet :P

---

### Post by schenckel on 2009-08-26
Hey guys! Has anyone tried to simply change the hardware drivers from version 180 to 173? I'm using a Nvidia 7300 Go and haven't had any crash since then( before it did so 10 times a day..). Maybe one could also try to use the 8.10 kernel.

Good luck!


edit: just wanted to confirm that no more crash occured.. :-)

---

### Post by Stan_1936 on 2009-08-26
Moving backwards is not the way to fix the problem.

---

### Post by mr.thraz on 2009-09-13
i installed the a/v linux custom rt kernel and all problems have disappeared.

---

### Post by jovianchiron on 2009-09-17
downgrading to 8.1 does not seem to help this hardware issue. i would go with it being a driver and/or kernal bug. i am having more random crashes in hardy than i did in jaunty.

---

### Post by mr.thraz on 2009-09-17
use a different kernel, i'm telling you.

---

### Post by AlexsAntidote on 2009-09-30
Add X-Updates to your repository list (found here: [https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/) (don't forget to add the key), and then do

```
sudo apt-get update && sudo apt-get upgrade
```

Then do (if you have a non 64-bit processor):

```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb

```

Or (if you have a 64-bit processor):
```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb

```

and finally:
```

sudo dpkg -i linux-headers-2.6.30-*.deb linux-image-2.6.30-*.deb

```

---

### Post by thijsz on 2009-10-05
hey Mr.thraz !

can you be a little more specific about the rt kernel you are using ?
on all my systems i have the rt kernel installed that comes with the ubuntu studio (a/v) package, but i still have the crashing issue, so ...

i'm using ubuntu studio 9.04 and xubuntu 9.04 with the 'studio' packages added (including the rt kernel)

grtz
Thijsz

---

### Post by mr.thraz on 2009-10-05
> **thijsz said:**
> hey Mr.thraz !

can you be a little more specific about the rt kernel you are using ?
on all my systems i have the rt kernel installed that comes with the ubuntu studio (a/v) package, but i still have the crashing issue, so ...

i'm using ubuntu studio 9.04 and xubuntu 9.04 with the 'studio' packages added (including the rt kernel)

grtz
Thijsz


you can find the kernel and headers im using [here]("http://www.bandshed.net/AVLinux2/kernel-rt-highmem/") 

its a dabian avlinux rt kernel with pae for high memory.

that way you can run up to 64gb of ram.

you can find more info [here]("http://www.bandshed.net/AVLinux.html")  


for months nothing worked and i had to *gasp* reinstall xp

then i installed this kernel + its header with the debs i linked to and all of a sudden i had a usable system that didn't crash.

it throws an error every time i install something but everything seem to work so i'm good.

one weird thing i noticed is that my  system still doesn't see all my ram.

that is more annoying than i can really stand.

but at least i can use ubuntustudio now

---

### Post by CedarSeagull on 2009-10-23
I'm having a similar problem.  I experience complete system lockups (mouse unresponsive, keyboard unresponsive; not even SysRq magic keys work, music/movies skips at current position if it's playing).  It usually happens while watching movies, but not exclusively.  I'm not really sure what to look for in the system logs; there is nothing obvious (eg. ERROR:....).  Any suggestions?  Wait a week for new version and hope for the best?


Dave

---

### Post by CedarSeagull on 2009-10-23
Desktop effects have been completely turned off and I'm using nVidea G Force GTS 250 with proprietary drivers, in case any good souls are wondering :)

---

### Post by pveurshout on 2009-10-26
> **CedarSeagull said:**
> I'm having a similar problem.  I experience complete system lockups (mouse unresponsive, keyboard unresponsive; not even SysRq magic keys work, music/movies skips at current position if it's playing).  It usually happens while watching movies, but not exclusively.  I'm not really sure what to look for in the system logs; there is nothing obvious (eg. ERROR:....).  Any suggestions?  Wait a week for new version and hope for the best?


Dave

Sadly, yes. There are numerous people who experience seemingly random freezes in Jaunty, even when previous versions (or Windows) worked flawlessly (myself included). Unfortunately, nobody seems to have found a solution and I'm doubting it's related to one single issue (although that's just a personal impression). In my case it seems like kernel 2.6.28-15 works quite allright, whereas -11 [SIZE="1"]*(**edit:** actually I'm not sure about this one, I don't think I ever really used it)*[/SIZE], -13, -14, and -16 make the system freeze (might be related to handling larger files, though I can't say for sure). Anyway, long story short: your best bet is probably Karmic (atleast that's what I'm desperately hoping for..)

**Update:** The 2.6.28-11 kernel might work for you as well, in case -15 does have problems after all. At least it worked for someone in this other thread on Jaunty freezing [(click)]("http://ubuntuforums.org/showthread.php?p=8178056#post8178056").

> **dspisak said:**
> With 8.10 I had no problems for many months.  I then upgrade to 9.04 by using Update Manager plus the suggested upgrades.  That is when my problems started.  No matter which kernel or xserver-xorg-etc. I tried nothing worked.

Next I created a partition on the HDD and did a clean install of Linux Mint Gloria x64 which is based on 9.04.  It was at least as easy to install as ubuntu.  It has worked without a hitch.  What's better is that Flash and java were already added to Firefox.

While reading the Mint installation guide I noticed the statement to the effect of "don't upgrade the kernel for a particular installation".  I have heeded this admonishment have not upgraded the kernel.  As I said Mint has worked without a hitch.

I then decided to give ubuntu one last try.  I downloaded the 9.04 x64 iso file.  However, before loading ubuntu I used the Gparted disk to reformat the old ubuntu partition.  I then did a clean install and so far all is well.  I did apply all of the recommended upgrades EXCEPT for the kernel and related upgeades.  So far, ubuntu 9.04 has worked without a hitch.

From my perspective the solution is: a clean install on a freshly formatted partition and DO NOT upgrade the kernel.

I hope this works for you as well.

PS As you know 9.04 used kernel 2.6.28-11.  Mint Gloria also uses 2.6.28-11.

---

### Post by Stan_1936 on 2009-10-30
Did anyone try Karmic?

Has it magically fixed this issue?

---

### Post by sergius248 on 2009-11-02
I experienced these random kernel crashes and system freezes after installing a new graphic card based on a Nvidia GeForce 7200GS (on a amd64 x2, 4 gigs of ram rig).
It seems that it is a general problem see "http://news.softpedia.com/news/Available-Now-Nvidia-Linux-Video-Driver-180-60-113022.shtml" but there are a number of articles on the topics. I installed the latest NVIDIA graphic package directly fron the NVIDIA site "http://download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg0.run
" and installed them (nice tutorials at "http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+freezes").
Since them for over 48hs no crashes.
It may be not a solution for everyone but for NVIDIA card users it may help.

---

### Post by pveurshout on 2009-11-02
> **sergius248 said:**
> I experienced these random kernel crashes and system freezes after installing a new graphic card based on a Nvidia GeForce 7200GS (on a amd64 x2, 4 gigs of ram rig).
It seems that it is a general problem see "http://news.softpedia.com/news/Available-Now-Nvidia-Linux-Video-Driver-180-60-113022.shtml" but there are a number of articles on the topics. I installed the latest NVIDIA graphic package directly fron the NVIDIA site "http://download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg0.run
" and installed them (nice tutorials at "http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+freezes").
Since them for over 48hs no crashes.
It may be not a solution for everyone but for NVIDIA card users it may help.

Sounds promising! Did you do this on Jaunty or on Karmic?

---

### Post by pveurshout on 2009-11-10
I've read about several positive experiences with Karmic from people who had Jaunty randomly freeze on them all the time (haven't tried myself yet, though). However, do **not** upgrade as it leads to trouble (do a clean install instead).

---

### Post by CedarSeagull on 2009-11-11
> **pveurshout said:**
> I've read about several positive experiences with Karmic from people who had Jaunty randomly freeze on them all the time (haven't tried myself yet, though). However, do **not** upgrade as it leads to trouble (do a clean install instead).

A week ago I tried to update via 

```
apt-get dist-upgrade

```

The upgrade failed while attempting to build an nvidia package, locked  keyboard (completely, even REISUB; which I didn't know was possible short of unplugging) and mouse.  After a hard reset and fsck I completely upgraded to karmic.  Now running...
```

dave@Doom:~$ uname -a
Linux dmitchellLinuxDesktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

```

After half hour with the nVidia binary drivers I had the same keyboard/mouse lock.  I'm starting to think this is a serious problem.  Could this be (gasp) an Ubuntu bug?

---

### Post by Stan_1936 on 2009-11-13
I have Xubuntu installed on an older(8 years old), significantly less powerful, sub-1.0Mhz 32-bit system and it crawls but works.  I'll have to satisfy myself with using that system.

> **CedarSeagull said:**
> ..After half hour with the nVidia binary drivers I had the same keyboard/mouse lock.  I'm starting to think this is a serious problem.  Could this be (gasp) an Ubuntu bug?

Very disappointing.  On a second, newer(3.5 yrs old), system I upgraded from a sh**y ATI card to NVIDIA SOLELY for installing Ubuntu on that machine.  It hasn't worked out.

That was the last time that I will try to install Ubuntu on a machine where I don't know if it would work or not, hoping that it would work.  My Ubuntu experience has changed from positive(on an old machine) VERY NEGATIVE because of the problem outlined in this thread.

**[SIZE="5"]The problem has NOT BEEN SOLVED.  It is VERY DISAPPOINTING![/SIZE]**

---

### Post by pveurshout on 2009-12-27
> **CedarSeagull said:**
> A week ago I tried to update via 

```
apt-get dist-upgrade

```

The upgrade failed while attempting to build an nvidia package, locked  keyboard (completely, even REISUB; which I didn't know was possible short of unplugging) and mouse.  After a hard reset and fsck I completely **_*upgraded*_** to karmic.  Now running...
```

dave@Doom:~$ uname -a
Linux dmitchellLinuxDesktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

```

After half hour with the nVidia binary drivers I had the same keyboard/mouse lock.  I'm starting to think this is a serious problem.  Could this be (gasp) an Ubuntu bug?

That could be the problem.. upgrading from Jaunty to Karmic = crap. I don't understand why they keep offering that possibility. I have *never* heard anyone successfully upgrade an OS. Vista -> Win7 also led to major trouble. IMHO they should just get rid of the upgrade functionality altogether..

---

