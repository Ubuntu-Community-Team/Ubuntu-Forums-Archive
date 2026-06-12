---
title: "Latitude D630 with Feisty"
date: 2007-06-22
forum: Dell  Ubuntu Support
---

### Post by apel_2804 on 2007-06-22
Hi,

I'm running Ubuntu 7.04 on my new D630. Intel 965 chipset and X3100. After a little trouble with the integrated Intel X3100 graphics card it's now up and running. ([http://ubuntuforums.org/showthread.php?t=464907&highlight=X3100](http://ubuntuforums.org/showthread.php?t=464907&highlight=X3100))

But there are still several issues:

- Image is clear and crisp but i still think its not running with 24bit color depth
- Sound comes from internal speaker and headphone at same time, or if I boot with headphones plugged there is only sound on headphone even if I unplug it.
- NetworkManager shows "No network devices found" after suspend/hibernate - I already tried to put the network card 3945 in the acpi whitelist but stil same issue
- DVD drive is not working after installation, but there is a workaround with generic ide-drivers ([http://ubuntuforums.org/showthread.php?t=477516](http://ubuntuforums.org/showthread.php?t=477516))

Now I want to know if there any other D630 users with similar issues, or if there users with other notebooks but same chipset with similar problems. And I also hope someone has a solution for these problems.

---

### Post by cnshzj007 on 2007-06-23
yes, I also doubt that My D630 is not running with 24bit color depth.The big evidence for this is the image of the login shows the color block as 16bit color depth.

---

### Post by susan_1890 on 2007-06-23
I'm also trying to get a D630 up and running. I'm setting up a dual boot system.

I'm pretty new to Linux, so it's been a bit of a challenge. I was able to get the basic video working using the alternate CD, but I haven't been able to install the patch mentioned in the thread you linked to, apel_2804. I get an error saying it can't find the package source when I try to install xserver-xorg-video-intel from source. I assume this is because the right repository is missing from /etc/apt/sources.list. Do you know what I need to add to get it?

My screen is definitely not displaying 24bit even though it says it is. There's a link to a color test in this article and I clearly get bands of color.

[http://www.leppik.net/david/blog/?p=58](http://www.leppik.net/david/blog/?p=58)

I'm also having an issue with my wireless card (Intel 4965). I can connect to an unsecured network but not a secured one. I used ndiswrapper and the xp driver downloaded from the dell site.

Any advice would be appreciated!

---

### Post by Kleenux on 2007-06-23
I tried today to install Ubuntu Desktop 7.04 on my new D630.
( as a dual boot with Vista basic )

1. the Server version of Ubuntu installed perfectly, then I tried  the desktop version...

2. Desktop:  I got initially this strange error "Cant Access tty, job control turned off" after 45" of install. 
The casper.log showed "init: 1 / cannot open /dev/sda"

I fixed this by plugging a 2nd DVD drive (USB port) loaded with a copy of the distro (!).

3. Now, while the process lasts for at least 2' it says it cannot open a Xserver... the GM965 driver is not present seemingly (?!).

Did you guys have these problems?
How can I fix the gdm problem,  do I need a special driver for the D630 ? Where can I find it and how can I provide it during install?

Thanks

---

### Post by susan_1890 on 2007-06-23
You're going to have install from the alternate CD. There's a problem with the driver for the new graphics card in the D630 (I'm assuming you have the integrated graphics, right?)

I found a bunch of useful threads that helped me get this working. 
[http://ubuntuforums.org/showthread.php?t=47614](http://ubuntuforums.org/showthread.php?t=47614)
[http://ubuntuforums.org/showthread.php?t=468918](http://ubuntuforums.org/showthread.php?t=468918)
[http://ubuntuforums.org/showthread.php?t=477516](http://ubuntuforums.org/showthread.php?t=477516)

Here are the notes I made on the steps I took.

1. Installed Ubuntu from alternate CD. Graphics don't work.
-Booted into safe mode.
-Ran sudo apt-get update
-Ran sudo apt-get dist-upgrade
-Ran sudo apt-get install-xserver-xorg-video-intel
-Ran sudo dpkg-reconfigure xserver-xorg (could also directly edit /etc/X11/xorg.conf so the video card driver says "intel". Do NOT enter a memory value if using dpkg-reconfigure. Also, the first time I ran this it hung with trying to auto-detect monitor settings so the second time I skipped this.

After that, you'll probably need to do some other work to get your wireless card and your DVD drive working.

---

### Post by apel_2804 on 2007-06-23
Hi,

my sources.list:

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

0. be shure you installed all updates - reboot
1. then install xserver-xorg-video-intel with aptitude...
2. install the patch: [http://ubuntuforums.org/attachment.php?attachmentid=35647&d=1182089873](http://ubuntuforums.org/attachment.php?attachmentid=35647&d=1182089873)
3. reboot or restart xserver
4. use dpkg-reconfigure xserver-xorg and choose intel as driver, dont try to auto find monitor this occures a blank screen, also it is indifferent which monitor settins you use, the driver will detect the required settings and ignore the lines in your xorg.conf

---

### Post by susan_1890 on 2007-06-23
Thanks! My display looks SOO much better. I hadn't actually realized how blurry it was until I fixed it. It's definitely still 18 bit color though.

I do have the same issue with the headphones. I hadn't tried them yet, but figured I would just to see what happens.

I don't know if you run into this, but I also found that the default touchpad behavior was way too slow, so I changed it following these directions [http://ubuntuforums.org/showthread.php?t=229302](http://ubuntuforums.org/showthread.php?t=229302)

---

### Post by apel_2804 on 2007-06-23
Yes the touchpad issue is on many machines not only the D630!

Ok, so we all have the same issues: 
- not 24bit color
- sound on speakers and headphone same time and
- DVD drive not recognized and with the generic ide workaround you cant play DVDs... (no DMA-Mode)
- No network devices after suspend/hibernate

---

### Post by Kleenux on 2007-06-23
Thanks for the valuable info.
Does somebody know when we can expect a new Desktop version including a newer kernel?

---

### Post by apel_2804 on 2007-06-24
Yes in september/oktober 7.10. But I really hope there will be an kernel update in next days/weeks. I installed the beta from gutsy last week, but there are so much other problems with the beta I can't determine which are D630 related!

---

### Post by jonsson on 2007-06-25
Please post your success stories when you get it working. ;) I had more or less decided to order one of these but now I'm a bit worried.

Btw, while googling for info about GNU/Linux compatibility I found [http://www.emperorlinux.com/mfgr/dell/tiger/?tab=details&id=437](http://www.emperorlinux.com/mfgr/dell/tiger/?tab=details&id=437)

They list everything as "full linux support"?

---

### Post by apel_2804 on 2007-06-25
They use own compiled kernels... I tryed this too, after that sound was not working...

---

### Post by sdin on 2007-06-26
I installed Feisty on my d630, reading this thread. Thanx.

Now, I am getting few  bugs other ones mentioned above.

1) In Firefox text rendering is too blurry and hard to read, comparing with how firefox renders in Vista.
2) System hangs when I try out some screensavers and only way out is reboot.

Not that I cannot live without screensavers and also I could temporarily fixed the screensaver thing  but its getting really hard to read on firefox.

---

### Post by zysurge on 2007-06-26
An excellent tutorial!  I was able to install 7.04 on a brand new D830, and I have no Linux experience at all.  Thanks!

---

### Post by apel_2804 on 2007-06-26
Screensavers using GL occuring system to crash. I disabled it. Same if you start other 3D applications. The Intel driver is stil not working properly.

---

### Post by jvalenzuela on 2007-06-27
On my case:

Network runs well (automaticly takes restricted driver for wireless).
After hibernate, networks comes to live without problems.
Alternate installations runs well (assign vesa driver). I've changed for intel driver after without problem.
Any 3D application crush completily keyboard (ctrl-alt-f1, etc. doesn't run) and graphics.
Now I'm trying to configure dual screen.

For 3D problem, I'm waiting for "official" intel driver for Feisty or the new xorg 7.3 which is mandatory for the intel 2.0 driver (theorically they solves our X3100 problems, I don't probe them)

---

### Post by apel_2804 on 2007-06-27
after hibernate my onboard nic works but wireless not, do you change any setting that wireless is working on your system after hibernate? what happens when suspend?

---

### Post by Kleenux on 2007-06-27
By the way, do you install the 32 bits or the 64 bits version?

---

### Post by Lek130 on 2007-06-28
jvalenzuela -

I also got my d630 to work. They key issue was graphic card. And the responses helped (never used ubunto before; apt-get is a great tool). Have VirtualBox with my companies W-XP Image running. BTW very easy. VB has a deb file on the site and you can also add vb.org as an apt-get source. Setup took me 10 minutes (including download ;-) ).

Missing: Dual Monitor (can be clone or anything, just needs to work somehow - especially LCD without much hassle; for the ppt stuff ;-) ). 

Missing 2: Sound. I get the sound on my USB speakers, but ubunto says no sound device. need to configure it. So skype refuses to run, as it checks what has been configured :((( 

Any suggestions?

THANKS

---

### Post by apel_2804 on 2007-06-28
I installed 32bit. Lek130: maybe you schould also look in other forums cause I dont think the usb sound problem is only D630 related

---

### Post by Lek130 on 2007-06-28
> **apel_2804 said:**
> I installed 32bit. Lek130: maybe you schould also look in other forums cause I dont think the usb sound problem is only D630 related

Its not about usb (that works), but the feisty does not recognize the sound card and the build speakers wont work.

---

### Post by davidmorawski on 2007-07-03
Hi all,

I just ordered my D630 yesterday, and have been reading up on many problems encountered when putting Linux on it. This has only partially dissuaded me, as I still plan on taking a stab at it (will most likely dual boot with Windows XP).

I had a couple of questions though:

I wasn't planning on using Ubuntu, only because of past distro choices and the fact that I've never used Ubuntu before (I realize neither of these reasons are very good ones). After doing some minor research on the wildly popular Ubuntu, though, I'm considering it moreso. I'm wondering though, is there any benefit to using Ubuntu in **this case** (when dealing with a poorly supported machine such as the D630) over other Linux distributions?

Secondly, is there any advantage to using the 32-bit version of Ubuntu versus the 64-bit release? Am I likely to encounter fewer issues, or have others chosen to install the 32-bit release just for kicks?

Thanks,

David

---

### Post by jonsson on 2007-07-03
I have ordered one as well (it is *still *in pre-production after more than a week :mad: ). I would like to generalise that previous question even more. What useable distro is most likely to support all the harware now/really soon? Ubuntu Gutsy? Debian unstable?

---

### Post by Lek130 on 2007-07-03
> **jonsson said:**
> I have ordered one as well (it is *still *in pre-production after more than a week :mad: ). I would like to generalise that previous question even more. What useable distro is most likely to support all the harware now/really soon? Ubuntu Gutsy? Debian unstable?


The issue still is that the d630 has some new components ... Device drivers updates for linux are not top prio for HW Vendors, I am afraid. That is an issue in itself.

I tried a few distros OpenSuse10.1, FedoraCore6, Fedora7, etc.
OpenSuse did not at even get close.
FC6 worked well from CD - no issue. But upgrading to F7 killed the system
F7 CD did not recognize the storage controller. 

Feisty Fawn U7.04 was the one I could get quickly working. Only the intel driver was an issue, until I found this discussion. Once I read the good comments here, I got the UI working in a few minutes.

I did NOT yet install WiFi. I did not get sound to work on the standard speakers, but it does work via USB Headset (Important for me, as I am using skype and i am having a 200bucks DSP build in headset for this).

I am using virtualbox as a virutal machine and having my companies windows image in it. Works super. Inclusive VPN out of the VM. 

Actually it is rather cool ... now!

Cheers,
Axel

---

### Post by jonsson on 2007-07-03
> **Lek130 said:**
>  Feisty Fawn U7.04 was the one I could get quickly working. Only the intel driver was an issue, until I found this discussion. Once I read the good comments here, I got the UI working in a few minutes.

Thanks, I'll probably go for that then (which is what I want anyway). :D Getting it to work quickly is a top priority as I really need a replacement for my current computer. As long as I can get it to a usable state quickly I can tweak the rest later.

---

### Post by Lek130 on 2007-07-03
> **jonsson said:**
> Thanks, I'll probably go for that then (which is what I want anyway). :D Getting it to work quickly is a top priority as I really need a replacement for my current computer. As long as I can get it to a usable state quickly I can tweak the rest later.

yepp. i almost gave up, because i tried a few distros and nothing worked. So it was.is a fun project getting linux running on my corp laptop.

for the installer, i used the server mode. Ignore the brSOMETHINGx11 error. Just wait for 30 minutes and it ll continue. Later follow the above on the graphics and you are cool.

The good news on my site: I just updated the system - played with compiz-barryl today, but that was a bad idea and had to do some reinstalling of graphic libs. And now sound works. This is a surpise. Trust me i recomplied the  kernel and nada. 

;) 

Axel

---

### Post by davidmorawski on 2007-07-03
Can anyone attest to how well Compiz/Beryl/Compiz-Fusion works with X3100? If so, how much RAM are you working with?

EDIT: Sorry--found it with a quick Google search:
[http://ubuntuforums.org/showthread.php?p=2935336](http://ubuntuforums.org/showthread.php?p=2935336)

David

---

### Post by Kleenux on 2007-07-05
Ok so I did it, using the Alt CD, downloading updates and applying the patch as described in p.1 of this thread:

It's almost automatic and it works well! (didn't test 100% everything, but X3100, sound, touchpad... are working great).

Seemingly Apache,PHP,Mysql don't come with this distro, have to install them... besides that, happy!

---

### Post by cacycleworks on 2007-07-06
Wow, just found this thread! :P

I got in my D630 and also found that I couldn't install from "normal" CD. I did alternate install and then apt-get install kubuntu-desktop (or something.... google was my friend) 

Unfortunately, due to the fuzzy monitor, the D630 went into a desk drawer and I've been trying to keep up with work on my old Sony Vaio SZ. :(  It doesn't hurt my eyes, so thanks in advance to everyone here as I will re-read the thread in hopes to get 1440x900 working well! The 915 patch seemed alllllmost there. I set the frequency to 50 from 60 and it was quite crisp. Then blank screen upon reboot.

:)

---

### Post by biogon on 2007-07-06
Well, after returning the machine I had with a broken backlight (heh), I've gotten FF running relatively smoothly now, thanks to all the great posts here.

The only problem I'm having is the 16/18-bit problem and how text is all fuzzy.

Hope this gets resolved soon... the less I have to use Vista (and its love of CONSTANT disk access), the happier I'll be.

Thank you everyone!

-jon

---

### Post by biogon on 2007-07-07
Well, another problem.

I use WEP and after Sleep, FF can't seem to figure out how to bring the network back up.

=(

-j

---

### Post by Voland666 on 2007-07-07
Get the latest X3100 driver released by Intel here:

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

Hope this works for everyone
bye

---

### Post by biogon on 2007-07-07
Voland666,

It seems to have worked... amazing! Very nicely done. Thank you. 

I definitely get smooth 24-bit images (or at least correctly "tricked/dithered 18bit ones") now.

The antialiasing technique on text seems to be a little wacky now - a lot of jaggies, but I couldn't tell before with how fuzzy everything was. I'll have to go figure out if I can adjust that too.

Thanks for the new drivers!

-j

---

### Post by Lek130 on 2007-07-09
> **Voland666 said:**
> Get the latest X3100 driver released by Intel here:

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

Hope this works for everyone
bye

hey thanks for the effort. It does wonders to the screen :) 

I am trying to setup a second tft monitor - also dell, but without success. What I like to be happy is to more or less plug and play to the monitor, and at the same time be flexible enough to plug a projector or in.

Right now the 2nd monitor actually works somewhat. Its a clone of the LCD of the Laptop, but with a really low resolution. its blown up 10 times and i can see only 25% of the laptop screen, just in oversize. Laptop screen runs in 1280x800 (the max I can get right now).

I am using the Intel Chipset and your driver. Feisty 7.04 ... Any suggestions???

Thanks!

---

### Post by Voland666 on 2007-07-09
I just tried with a 24" CRT, and all I got is a black screen. Maybe you can get some help on the FreeDesktop/Xorg mailing list.
I'm on a latitude D630, and I get a beautiful 1440x900 video mode. Do not know what is preventing yours to get the same... of course you have a 1440x900 panel, right? :-)
Look at my xorg.conf for inspiration... it is working for me...

```
Section "Monitor"
        Identifier      "Monitor0"
        VendorName      "AU Optronics"
        ModelName       "B141PW01"
#       DisplaySize     305 190
        VertRefresh     50
        Option          "DPMS"
        Gamma           0.75 0.65 0.60  #see also /etc/X11/Xsession.d/95x11-xgamma
EndSection

Section "Screen"
        Identifier              "Screen0"
        Device                  "Device0"
        Monitor                 "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1280x800" "1280x768" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1280x800" "1280x768" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1280x800" "1280x768" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1280x800" "1280x768" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1280x800" "1280x768" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1920x1200" "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1280x960" "1280x800" "1280x768" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

---

### Post by bach on 2007-07-10
Is it necessary to install the 915resolution package in order to get the 1440 x 900 resolution working?

---

### Post by cacycleworks on 2007-07-10
> **bach said:**
> Is it necessary to install the 915resolution package in order to get the 1440 x 900 resolution working?

Doesn't look like it to me:
[http://ubuntuforums.org/showthread.php?t=494943&highlight=X3100+fix](http://ubuntuforums.org/showthread.php?t=494943&highlight=X3100+fix)

Once I get something sorted on my Sony, this is next for my D630. :)

---

### Post by Neuge on 2007-07-11
Has anyone had success installing the 64 bit version?  I'm currently downloading the alternate CD, but I've yet to read anywhere about a successful 64 bit install.  I'll reply with my tribulations tomorrow.

I'd like to be able to use my laptop for more than an SSH box. :(

---

### Post by davidmorawski on 2007-07-11
> **Neuge said:**
> Has anyone had success installing the 64 bit version?  I'm currently downloading the alternate CD, but I've yet to read anywhere about a successful 64 bit install.  I'll reply with my tribulations tomorrow.

I'd like to be able to use my laptop for more than an SSH box. :(
I'm currently posting from the 64 bit release :)

Graphics won't work initially (I'm assuming your D630 has the X3100)--but you're only a few apt-get's away. I was unable to use Voland666's [module]("http://ubuntuforums.org/showthread.php?t=494943") due to the differing architecture, but the picture isn't too bad without it. I'm suffering from less-than-smooth gradients, but am hoping to straighten than out sooner than later (@Voland666: care to shed any light on this issue? :) )

WiFi worked without a hitch, though I did all the initial updates through a hard-wired connection (I think it may have worked anyways). 

Sound works, from what I can gather.

The DVD-RW is the only thing that is still non-operational, but I think that's an issue all across the board?

Let us know how your install goes,

Dave

---

### Post by jonsson on 2007-07-11
My D630 finally arrived yesterday. :) Unfortunately, now *I * am not at home before the weekend.

So, for those of us who have been stuck with older computers for far too long and have not really bothered to follow the whole 64 bit thing. Why should/shouldn't I choose the 64 bit version?

---

### Post by cacycleworks on 2007-07-11
> **jonsson said:**
> My D630 finally arrived yesterday. :) Unfortunately, now *I * am not at home before the weekend.

So, for those of us who have been stuck with older computers for far too long and have not really bothered to follow the whole 64 bit thing. Why should/shouldn't I choose the 64 bit version?


The point of "how many 64 bit apps are there?" kinda lets me go to 32 bit.

---

### Post by davidmorawski on 2007-07-11
> **jonsson said:**
> My D630 finally arrived yesterday. :) Unfortunately, now *I * am not at home before the weekend.

So, for those of us who have been stuck with older computers for far too long and have not really bothered to follow the whole 64 bit thing. Why should/shouldn't I choose the 64 bit version?
There are tons of great links in this thread on the advantages and disadvantages of 64-bit:
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

As for this specific situation, I can say that I chose to install the 64 bit release on my D630 just to take advantage of the processing power. I imagine it will be only a matter of time before 64-bit applications are the norm.

Though, choosing 32-bit probably will be one less headache to worry about..it all just depends on what you want out of your machine.

Dave

---

### Post by Neuge on 2007-07-11
> **davidmorawski said:**
> I'm currently posting from the 64 bit release :)

Graphics won't work initially (I'm assuming your D630 has the X3100)--but you're only a few apt-get's away. I was unable to use Voland666's [module]("http://ubuntuforums.org/showthread.php?t=494943") due to the differing architecture, but the picture isn't too bad without it. I'm suffering from less-than-smooth gradients, but am hoping to straighten than out sooner than later (@Voland666: care to shed any light on this issue? :) )

WiFi worked without a hitch, though I did all the initial updates through a hard-wired connection (I think it may have worked anyways). 

Sound works, from what I can gather.

The DVD-RW is the only thing that is still non-operational, but I think that's an issue all across the board?

Let us know how your install goes,

Dave
I got it running with the graphics, and yes there is a bit of a gradient problem but nothing I can't tolerate.  But the wireless was completely ignored on install.  I haven't yet figured out how to fix it.

---

### Post by cacycleworks on 2007-07-12
> **Neuge said:**
> I got it running with the graphics, and yes there is a bit of a gradient problem but nothing I can't tolerate.  But the wireless was completely ignored on install.  I haven't yet figured out how to fix it.

my Sony laptop has the same wireless card (the intel one) and kubuntu install found it no problem. knetworkmanager had it and i just right-clicked the tray icon. i suspect the D630 would be the same. 

if you have the Dell proprietary one, when i had a D520, it too, was found and automagic in kubuntu install.

i'm in the middle of installing gutsy. gonna compile the kernel before i get too crazy with the install and tweaking, so if i muck it up, i can re-do it all. (having a "spare" laptop is sometimes handy) earlier posts in this thread convinced me of 64 bit even though i likely will never need it with my desktop work.....

---

### Post by Neuge on 2007-07-12
> **cacycleworks said:**
> my Sony laptop has the same wireless card (the intel one) and kubuntu install found it no problem. knetworkmanager had it and i just right-clicked the tray icon. i suspect the D630 would be the same. 

if you have the Dell proprietary one, when i had a D520, it too, was found and automagic in kubuntu install.It definitely didn't install any wifi drivers.  Network manager doesn't have any options for wireless setup, ifconfig brings up no wifi settings, and the little wifi light below the LCD doesn't come on.  I have an Inspiron 640m that has the Dell wifi card and had to use ndiswrapper to get that working.

---

### Post by cacycleworks on 2007-07-12
> **Neuge said:**
> It definitely didn't install any wifi drivers.  Network manager doesn't have any options for wireless setup, ifconfig brings up no wifi settings, and the little wifi light below the LCD doesn't come on.  I have an Inspiron 640m that has the Dell wifi card and had to use ndiswrapper to get that working.

Interesting... the D520 I had with the dell card was already ndis-wrapped from installing kubuntu fiesty. :confused: ah well. that's why i don't sell stuff for computers!

---

### Post by davidmorawski on 2007-07-12
> **Neuge said:**
> I got it running with the graphics, and yes there is a bit of a gradient problem but nothing I can't tolerate.  But the wireless was completely ignored on install.  I haven't yet figured out how to fix it.
What kind of wireless card does your D630 have? Intel or Dell?

---

### Post by Neuge on 2007-07-12
> **davidmorawski said:**
> What kind of wireless card does your D630 have? Intel or Dell?Intel (ipw3945)

On further investigation, lshw -C network brings up an Intel Network controller (other than the broadcom ethernet port) with the pci bus address and io/irq resources, but says it is unclaimed and doesn't list a driver, MAC address, eth1 etc...  There is an ipw3945 driver in /sys/bus/pci/drivers.

---

### Post by mk1970 on 2007-07-13
I have D630 at work with 3945ABG WLAN and X3100 graphics and currently everything except the DVD drive is working. I built 2.6.22.1 kernel myself and the DVD was detected, but then audio and WLAN did not work and I didn't have time to investigate this further. So I'm using the official 2.6.20-16 kernel now.

[http://www.iki.fi/kuparine/comp/d630/](http://www.iki.fi/kuparine/comp/d630/)

---

### Post by CharlieNixon on 2007-07-13
My guess is that Dell does not sell  D630 with Ubuntu preinstalled. Is that correct? If so, is there any hope for more support in the future as far as drivers or anything else? If Ubuntu's display never works the way it should on a D630 it defeats the purpose for me. 

Is there a list of which laptops Ubuntu will run on natively without these kinds of problems?

---

### Post by davidmorawski on 2007-07-13
> **CharlieNixon said:**
> My guess is that Dell does not sell  D630 with Ubuntu preinstalled. Is that correct? 
I believe that is correct, however, they do offer software support/drivers for Ubuntu 7.04 on the D630. Check out [**support.dell.com**]("support.dell.com"), and browse to the D630 section. You should be able to choose 'Ubuntu 7.04' as your OS and view the downloads specific to that set-up. I can't view the page now, in my current browser, but I believe there are only 2 downloads--neither of which look too promising for the people in this thread. Worth a look though.

Dave

---

### Post by biogon on 2007-07-15
Strange.

I'm using 7.04 on a D630 with the Intel 3945.

After waking from sleep, it doesn't want to reconnect to a WEP-based network.

iwconfig gets no wireless extensons on eth1 (none on eth0 either, but that's more understandable.)

Hrm.

-j

---

### Post by jonsson on 2007-07-17
> **biogon said:**
> Strange.

I'm using 7.04 on a D630 with the Intel 3945.

After waking from sleep, it doesn't want to reconnect to a WAP-based network.

iwconfig gets no wireless extensons on eth1 (none on eth0 either, but that's more understandable.)

Hrm.

-j

I successfully installed Kubuntu 7.04 on my D630 yesterday, thanks to this thread. :)

My wifi works after suspend/hibernate but sound does not.

Also, closing the lid does not put the machine to sleep.

Otherwise, pretty much everything seems to work, except for the DVD issue and the smartcard reader which I haven't tried yet.

---

### Post by Neuge on 2007-07-17
> **Neuge said:**
> Intel (ipw3945)

On further investigation, lshw -C network brings up an Intel Network controller (other than the broadcom ethernet port) with the pci bus address and io/irq resources, but says it is unclaimed and doesn't list a driver, MAC address, eth1 etc...  There is an ipw3945 driver in /sys/bus/pci/drivers.
I still can't get this to work.

If I go to System>Preferences>Hardware Information it shows an unknown Intel device on PCIe port 2 which is obviously the ipw3945.

If I go ro System>Administration>Restricted Drivers Manager it says my hardware doesn't require any restricted drivers.

sudo modprobe ipw3945 it brings back "ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection"

I'm really scratching my head here.  Any help would be appreciated.

---

### Post by jebe86 on 2007-07-19
I too installed Ubuntu feisty on a dell latitude D630.

Issue I had:

- used ubuntu-server, then dist-upgrade, then aptitude install ubunut-desktop.

X work fine, sound also.

My wireless card, according to windows I have in dual boot, and to dell support with my service tag, is an Intel 4965AGN, and not an Intel 3945.

I'm able to use ndiswrapper to "see" it, but I can not use it....
I used this 

root@laptop:/data# ndiswrapper -l
netw4x32 : driver installed
        device (8086:4229) present


Should I use something different ?

Also, I can not use the CD drive....nor for reding nor for burning.....
any help ?

thanks already

---

### Post by cacycleworks on 2007-07-19
> **jebe86 said:**
> I too installed Ubuntu feisty on a dell latitude D630.

My wireless card, according to windows I have in dual boot, and to dell support with my service tag, is an Intel 4965AGN, and not an Intel 3945.

root@laptop:/data# ndiswrapper -l
netw4x32 : driver installed
        device (8086:4229) present

thanks already

Google has 2 awesome results on the first page...
[http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi)
[http://lists.us.dell.com/pipermail/linux-desktops/2007-June/000499.html](http://lists.us.dell.com/pipermail/linux-desktops/2007-June/000499.html)

What screen res are you at? I'm pretty bummed at the 1290 res and want the 1440x900. So I started over... my next step is to compile the kernel (why not?). I have little time invested into the install so if I totally muck it up, I've got the ubuntu alternative cd handy. ;)

---

### Post by js.opdebeeck on 2007-07-19
> **jonsson said:**
> My D630 finally arrived yesterday. :) Unfortunately, now *I * am not at home before the weekend.

So, for those of us who have been stuck with older computers for far too long and have not really bothered to follow the whole 64 bit thing. Why should/shouldn't I choose the 64 bit version?

Hello

I've just installed and configured Feisty 64 on my laptop, 

All the previous tips was really well but too many crashes with the X and the session after installing Flash Player for Firefox .

Definitively ... is there some advantage stay/try into 64 ... I ran from the 3 last Ubuntu releases in 32 bits without any troubles (on my D600).

I'm hesitate to go to 32 or to try the next coming 64 Tribe .... :confused:


Js

---

### Post by davidmorawski on 2007-07-19
> **js.opdebeeck said:**
> 
All the previous tips was really well but too many crashes with the X and the session after installing Flash Player for Firefox 
How did you install Flash? Mine works wonderfully in Firefox after using [**Kilz's nspluginwrapper script**]("http://ubuntuforums.org/showthread.php?t=425672"), though I've yet to upgrade since the security warning (whoops).

If you haven't yet, check out the earlier posts in this thread for instructions on how to get all things video running smoothly. Also, installing these [**Intel video drivers**]("http://ubuntuforums.org/showthread.php?t=500668") is very worthwhile.

I'm running a very stable 64-bit Feisty on my D630, but I had to jump through a few hoops to get it that way. I think it's perfectly possible, though you may not want to go through the trouble if you don't really want/need a 64-bit OS.


Dave

---

### Post by Neuge on 2007-07-19
> **cacycleworks said:**
> Google has 2 awesome results on the first page...
[http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi)
After looking through the documentation, I have a 4965 not a 3945.  But this doesn't work and I think because I'm using 64bit.  It can't compile the new kernel to install the mac80211 module.

Ack, I'll never get this wireless working.

---

### Post by Neuge on 2007-07-19
Just FYI for anyone who has a 4965agn wireless card, this tutorial got it working for me under 64-bit

[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

---

### Post by cacycleworks on 2007-07-19
> **Neuge said:**
> Just FYI for anyone who has a 4965agn wireless card, this tutorial got it working for me under 64-bit
[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

This is great! Thanks Neuge! :KS

---

### Post by Neuge on 2007-07-19
> **cacycleworks said:**
> This is great! Thanks Neuge! :KSI should probably add that doing this broke the sound.  I don't really care about that, but you might.

EDIT:  And the current gutsy kernel is 2.6.22-8, so replace every 2.6.22-7 with that in the tutorial.

---

### Post by alecwh on 2007-07-20
Hello, I've gotten Ubuntu up and running. Some of my problems:

- DVD Drive, most having this problem (workaround available)
- WIFI. This is huge, if anyone can help me out on this, 
```
[CODE]alec@aleclaptop:~$ sudo modprobe ipw3945
2007-07-19 22:01:57: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

```[/CODE]
How do you do fix this?

Thanks! (oh, and the color problem affects me too.)

---

### Post by davidmorawski on 2007-07-20
> **alecwh said:**
> Hello, I've gotten Ubuntu up and running. Some of my problems:

- DVD Drive, most having this problem (workaround available)
- WIFI. This is huge, if anyone can help me out on this, 
```
[CODE]alec@aleclaptop:~$ sudo modprobe ipw3945
2007-07-19 22:01:57: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

```[/CODE]
How do you do fix this?

Thanks! (oh, and the color problem affects me too.)
What do you mean by "color problem"? For colors bands versus smooth gradients, check out [this]("http://ubuntuforums.org/showthread.php?t=494943") thread, or [this]("http://ubuntuforums.org/showthread.php?t=500668") one for 64-bit.

Apparently the DVD drive problem is kernel related. Check out this thread on the Fedora forums:
[http://forums.fedoraforum.org/showthread.php?p=828119](http://forums.fedoraforum.org/showthread.php?p=828119)

I'm not about to upgrade my kernel quite yet, but it seems like this is a plausible fix.


Dave

---

### Post by cacycleworks on 2007-07-20
I just started up kubuntu from the gutsy tribe 3 install. 1440x900 @ 24bits no problem. I did alt install then lots of aptitude upgrades and dist-upgrades for anything BUT KDE, which I did last. The xorg server install included 1440x900 and it is crystal clear. MUCH better than my first install. btw, wireless worked too. 

no sound and probably no cd-rom without some tweaks. 

me=happy

A very brief summary of my install:
- alt cd install 
- lots of command line aptitude installs, updates, and upgrades
- on the advice of this thread, I installed the -8 kernel
- rebooted
- lots more updates, upgrades, and dist-upgrades until everything seemed stable 
(except for 5 screwed up dependencies)
- aptitude was awesome at helping me manage the dependencies... I somehow worked myself into a box and it led me out.
- installed lots of little things i wanted.. office, all kinds of kde stuff, knetworkmanager, etc etc

2 hours later (only downloading at 200kbps ;) ) I held my breath and ran startx. 

it worked. it was at 1440x900 out of the box...

wow - i honestly can't believe it. :) Good job Gutsy team!

---

### Post by alecwh on 2007-07-20
Ok, thanks. But any help on the wireless situation?

---

### Post by cacycleworks on 2007-07-20
> **alecwh said:**
> Ok, thanks. But any help on the wireless situation?

Yeah, it worked out of box for me, using knetworkmanager. It signed right on to our WPA-AES secured wlan. First try, even. I was really holding my breath on that one. Now I can ditch the 35' patch cord I made for the D630. BTW, I *removed* all other network utils, leaving only the knetworkmanager. None of the others are WPA capable and I need that for my work.

As an aside, my Sony Vaio SZ220 has the same wireless card... upon startup EVERY time, it has a 90 second timeout and then boot continues. I was dreading that issue with the D630. But it's not there. Either Gutsy or the latest kernel fixed that, as I did nothing special for it. Been looking in to how to compile the kernel on the sony, but now I'll get the D630 working and then update the kernel on the sony.
> 15:18 chris@sz:~$ uname -a
Linux sz 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

Notably wrong on D630 (Gutsy) are:
- right click on power manager and the CPU frequencies are not shown. Both cpus are listed in ksysinfo and performance is fast, so they've got to be functioning.
- it doesn't see the sound hardware (i haven't done anything for this)
- i'm assuming it doesn't see the optical drive. i haven't done anything for this and dont really care. i've got 2 different forms of external drive technology. i bought a 2nd battery to go in that bay anyhow.

Goodies: $199 docking station for $23: [http://www.auctiva.com/stores/viewstoreitem.aspx?loc=5&item=220132692143&site=0&id=374595&format=9](http://www.auctiva.com/stores/viewstoreitem.aspx?loc=5&item=220132692143&site=0&id=374595&format=9)
I got that in today along with a touch screen monitor i bought from them. :) I wonder if the docking technology works for us??? :D

---

### Post by jens.h on 2007-07-21
After playing with different modules I got DMA activated again.
I used the module piix instead of the generic one. After this I got /dev/hda und DMA was active again. :)
Don't forget to add 'piix' to your /etc/modules and remove the entry for the generic module, if you have one.
Good luck!

---

### Post by davidmorawski on 2007-07-22
> **jens.h said:**
> After playing with different modules I got DMA activated again.
I used the module piix instead of the generic one. After this I got /dev/hda und DMA was active again. :)
Don't forget to add 'piix' to your /etc/modules and remove the entry for the generic module, if you have one.
Good luck!
Thanks for the tip! That literally took 5 minutes to set up, and about 25 seconds once I knew which commands to issue.

Now if I only knew what I actually did...Out of curiosity, how did you know to use the 'piix' module?

---

### Post by jebe86 on 2007-07-25
> **cacycleworks said:**
> Google has 2 awesome results on the first page...
[http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi)
[http://lists.us.dell.com/pipermail/linux-desktops/2007-June/000499.html](http://lists.us.dell.com/pipermail/linux-desktops/2007-June/000499.html)


sorry for the late reply....

1) thanks for the links,i'll give it a try...

What screen res are you at? I'm pretty bummed at the 1290 res and want the 1440x900. So I started over... my next step is to compile the kernel (why not?). I have little time invested into the install so if I totally muck it up, I've got the ubuntu alternative cd handy. ;)


I'm running at 1440x990.....
my kernel version (straight from ubuntu dist-upgrade): 2.6.20-16-generic

---

### Post by power3d on 2007-07-25
Hi!
I tried this instructions: [http://w3.ualg.pt/~aanjos/misc.html](http://w3.ualg.pt/~aanjos/misc.html)
They are for Debian but it worked.
Cheers

---

### Post by cacycleworks on 2007-07-25
> **cacycleworks said:**
> Yeah, it worked out of box for me, using knetworkmanager. It signed right on to our WPA-AES secured wlan. First try, even. I was really holding my breath on that one. Now I can ditch the 35' patch cord I made for the D630. BTW, I *removed* all other network utils, leaving only the knetworkmanager. None of the others are WPA capable and I need that for my work.


*groan* wireless is lost again... the gear keeps spinnin and nothing happens. :P I've printed about 40 pages of threads and am going to sort it out for myself. Pondering options... ;)

---

### Post by jebe86 on 2007-07-27
> **jebe86 said:**
> I too installed Ubuntu feisty on a dell latitude D630.


Also, I can not use the CD drive....nor for reding nor for burning.....
any help ?

thanks already

Fixed the CD issue, it was simpler than expected:

installed 

modprobe ata_piix  
modprobe ata_generic

(which were alredy there...)

and added piix to /etc/modules

Now I can read and wrie to CD using K3b, and aslo listen to CDs.....

---

### Post by cacycleworks on 2007-07-28
> **jebe86 said:**
> I'm running at 1440x990.....
my kernel version (straight from ubuntu dist-upgrade): 2.6.20-16-generic

FYI: I just did a clean install of Gutsy Tribe 3 alternate amd_64 (to get 64 bit). To get 1440x900, I removed the existing video driver (I think it was 810i) and aptitude installed xserver-xorg-video-intel. The screen is pretty crisp now. Display tested against the 24bit image page: [http://www.leppik.net/david/blog/?p=58](http://www.leppik.net/david/blog/?p=58)

Now to work on sound, wireless, and dma. Need to get kubuntu running; i can't stand the ubuntu gui: makes me feel retarded. ;P

---

### Post by wty on 2007-07-29
> **jebe86 said:**
> Fixed the CD issue, it was simpler than expected:

installed 

modprobe ata_piix  
modprobe ata_generic

(which were alredy there...)

and added piix to /etc/modules

Now I can read and wrie to CD using K3b, and aslo listen to CDs.....

This works, just needed a reboot and the cdrom works fine. Nce thread, but I got an D630 with nVidia, but I got it to work after a days work ;)

---

### Post by jonsson on 2007-07-29
I've just realised that if I'm running on batteries I get no network after hibernate/suspend but if the power is plugged in both interfaces work when returning from suspend/hibernate. It still kills sound, though.

I think I read in some review of some other Dell laptop when I was looking for which one to buy that it disabled networking when the power was disconnected. Could this all have something to do with power saving?

Anyway, I just noticed this and thought I'd throw it up here. ;)

---

### Post by cacycleworks on 2007-07-30
wow, trying to compile the kernel is really beating me up. Really, all I'm trying to do is follow the mac80211 steps. No matter what packages I install (linux linux-headers, fakeroot, whatever) I keep getting this:

```
root@outside:/lib/modules/2.6.22-8-generic/build# make
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
make[1]: *** No rule to make target `arch/x86_64/kernel/asm-offsets.c', needed by `arch/x86_64/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2
root@outside:/lib/modules/2.6.22-8-generic/build#
```

Config:
installed from Gutsy Tribe 3 AMD64 Alternate CD
used apt-get install to get the kubuntu / kde stuff going
uname output: Linux 2.6.22-8-generic #1 SMP Thu Jul 12 16:09:47 GMT 2007 x86_64 GNU/Linux

I'm a bit done with it all, really. :(  i'll re-read everything and think up a new approach to getting this laptop to work. This thing sat in a drawer for a couple weeks ... and is about to again. I thought I could make it work, but I'm out of time to configure it. Spent about 20 hours on it over the last 3 days.

---

### Post by Lek130 on 2007-08-01
Ok, it seems for now that I have it all working, except Extended Desktop in Dual Monitor Mode. 

- Sound works! I saw a lot of people have issues here. I got it working with Feisty and apt-get and "option snd-hda-intel model=3stack" in the alsa-base file (/etc/modprobe.d/). The tirck to install all lib's you can and to use the generic kernel. I can share details upon request. 

- Beryl & Toys: Work without any issues The full spectrum of effects seem to work. Following the updates out of the forum here. Apt-get latest of everything, incl backports and then go for it ... IN effect beryl is slightly better then Compiz, as it has an auto-fall back mode in case of crashes (it did not crash for me though, but I saw the menu).

- other stuff works as far tried. 

- If anyone has ideas on dual monitor in extended mode - i am all ears :) 

cheers

---

### Post by jonsson on 2007-08-01
> **Lek130 said:**
> 
- Sound works! I saw a lot of people have issues here. I got it working with Feisty and apt-get and "option snd-hda-intel model=3stack" in the alsa-base file (/etc/modprobe.d/). The tirck to install all lib's you can and to use the generic kernel. I can share details upon request. 


Please do! :) Basic sound worked out of the box for me but there are a few issues like no sound after suspend/hibernate and (un)plugging external speakers not switching internal speakers on/off.

I tried adding that line but that did not seem to make a difference. Do I need to replace an existing line with the above?

---

### Post by Lek130 on 2007-08-02
This depends on your /etc/modprobe.d/alsa-base and options files.
I just added this at the end. In effect, one of the issues is that snd-hda-intel has not model for the the d630. If you look at the C Code and the descriptions, it has this for many other laptops (mac, thinkpad, LG, etc.). 

Anyhow, using the GENERIC latest Kernel (i did NOT get the server kernel to work with sound), assuming you have almost all alsa and gstreamer sutff installed, it should work. 

I did not try external speakers and I usually do not hibernate, because shutdown/loading of ubuntu is very fast for me, so that I have not much need. Let me see, when i have time, I can try.

---

### Post by cacycleworks on 2007-08-03
> **Lek130 said:**
> This depends on your /etc/modprobe.d/alsa-base and options files.
I just added this at the end. In effect, one of the issues is that snd-hda-intel has not model for the the d630. If you look at the C Code and the descriptions, it has this for many other laptops (mac, thinkpad, LG, etc.). 

Hi, could you please post your alsa-base modeprobe file? 

My Dell D630 current status:
- Kubuntu Fiesty 7.04 amd64 alternate install
- followed 64 bits video instructions:
   [http://ubuntuforums.org/showthread.php?t=500668](http://ubuntuforums.org/showthread.php?t=500668)
- followed master kernel compile thread
    [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

The compile only takes about 20 minutes... configuring the kernel is about 2 hours.

uname:
Linux 2.6.22.1 #1 SMP Fri Aug 3 04:03:36 PDT 2007 x86_64 GNU/Linux

status: 
works: wired ethernet, cd (assumed, since it's now listed), 1440x900, both cpus, cpu scaling, firefox
doesn't: wireless and sound.

will update with more as I learn it.

---

### Post by Lek130 on 2007-08-03
Hi!

My Kernel is 2.6.20-16-generic #2 SMP June 7th, 2007 i686. 
The only one line I added was the line indicated above - see file below. 
I did nothing in the options file.

I did use synaptic to search for alsa and installed about everything (libs, dev, apps) and did the same for gstreamer and sound. Ok, I knoe its not a very good trouble shooting apporach. But it worked.

I did not upgrade to the latest drive, but used the apt-get version - x13 vs the new x14rc4. I tried so and removed it again. 

Ok: How does your sound not work? aplay -l ? no card in /proc/asound/cards?

There are different ways how it does not work. I found that googling did not help my case (no card found). 

That said a USB based headphone and speaker worked fine in any scenario.

WIRELESS: Did you try ndiswrapper with the original windows driver?

Cheers


ALSA-BASE file / only added last line. 

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=3stack

---

### Post by cacycleworks on 2007-08-03
Interesting! I found info here: 
  [http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x](http://www.mythtv.org/wiki/index.php/Intel_HD_Audio_-_Realtek_ALC88x)

and made their suggested changes to the alsa-base and then recompiled the kernel again, adding some more built in sound options, and the sound works! At this moment, there are entries in /proc/asound which make sense. 

I'm working on another small fix and then once I have wireless working, I plan on making YaKCG. yet another kernel compile guide : but for the D630, and showing the options I'm using. ;)

---

### Post by Lek130 on 2007-08-04
interesting indeed. what kind of benefits you got from this? Both sound and wifi, where do you see the advantages? 

just checking. i did not want to change the kernel myself ... though its probably the right thing to do ...

---

### Post by cacycleworks on 2007-08-04
> **Lek130 said:**
> interesting indeed. what kind of benefits you got from this? Both sound and wifi, where do you see the advantages? 

just checking. i did not want to change the kernel myself ... though its probably the right thing to do ...

Hi! :)  I'm not too sure what benefit there is ... I did run 7.04 32 bit for some time. I *think* the 64 bit is a bit faster ... then add in the compiled / customized kernel and startup is pretty speedy.

I *do* know that I can compile the kernel in what seems 60% of the time many people mention. I have yet to use a stop-watch, but it seems 22 to 25 minutes for full compile and install of kernel. (that is, everything BUT playing around with the options in menuconfig/xconfig).

---

### Post by Nicolae on 2007-08-11
> **cacycleworks said:**
> 
....
Goodies: $199 docking station for $23: [http://www.auctiva.com/stores/viewstoreitem.aspx?loc=5&item=220132692143&site=0&id=374595&format=9](http://www.auctiva.com/stores/viewstoreitem.aspx?loc=5&item=220132692143&site=0&id=374595&format=9)
I got that in today along with a touch screen monitor i bought from them. :) I wonder if the docking technology works for us??? :D

I've tried the s-video out, at least, it works (nvidia graphics though, not intel). I don't have any serial devices or a monitor with DVI input to test, but I'll test the PS/2 ports, USB, VGA, Ethernet, and parallel ports.

EDIT: PS/2 mouse and KB work, so does ethernet. I'll mess with USB, parallel port and VGA out later.

---

### Post by cacycleworks on 2007-08-11
> **Nicolae said:**
> I've tried the s-video out, at least, it works (nvidia graphics though, not intel). I don't have any serial devices or a monitor with DVI input to test, but I'll test the PS/2 ports, USB, VGA, Ethernet, and parallel ports.

EDIT: PS/2 mouse and KB work, so does ethernet. I'll mess with USB, parallel port and VGA out later.

omg, just this instant is the first time I've booted my D630 in the docking station. VGA out works. Ethernet for me, too. And so does USB mouse. I just noticed the PS2 inputs, thank you!! I actually like the crappy wheel mice that dot-coms throw away!! :D

Now to figure out how to turn off the framebuffer on the laptop and switch to native resolution of the 19" monitor I have here... 

This is so cool! I can have the keyboard of the laptop where it belongs and the monitor up high where it belongs, too. I've had neck-back problems, so ergo setup is important for me.

---

### Post by davidmorawski on 2007-08-11
Has anyone gotten 2 monitors/displays to work with the Intel GMA? I'm not having much luck, but will post back later with more details.

---

### Post by cacycleworks on 2007-08-11
I posted to the main forum this (tho I typo it to D620)

I stumbled upon a way to install 64bit and there is no compiling and very little "voodoo" to perform!

Read thread here:
[http://ubuntuforums.org/showthread.php?t=518702](http://ubuntuforums.org/showthread.php?t=518702)

Simple account of the steps repeated here (much useful newbie-info I learned omitted):
> **cacycleworks said:**
> 7.04 kubuntu alt amd64 install cd
**Update Grub**
upon initial boot, I hit esc to enter grub. Press e twice to edit top entry to add pci=assign-busses

To make the Grub edit "stick", you will need to do these steps:
Edit your menu.lst manually, on the "# defoptions" line add the pci option, then run "sudo update-grub".
**update distribution**
apt-get update
apt-get upgrade
apt-get dist-upgrade

before restarting, check your grub menu.list that pci=assign-busses is still there!! If not, repeat above steps.

**edit modules**
Added the three lines to BOTH files **/etc/modules** and **/etc/initramfs-tools/modules**:
piix
snd_hda_intel
agpgart

After the edits, you must run [FONT="Courier New"]**update-initramfs -u**[/FONT] to update the initramfs.

**fix the video**
download and install the two files from here: 
[http://ubuntuforums.org/showthread.php?t=500668](http://ubuntuforums.org/showthread.php?t=500668)

dpkg-reconfigure xserver-xorg

special options I used:
no autodetect  -enter-
i entered in 256 for the memory    -enter-
-no- to autodetect monitor     -enter-
I named the monitor dell 1440x900 laptop     -enter-
I selected:
[*] 1440x900 
[*] 1280x800   (i don't know if this is valid, who cares, really)
[*] 1024x768
[*] 800x600
and cleared all other resolutions.   -enter-
-medium-           -enter-
1440x900@100hz      -enter-
Write monitor sync changes to config file?  -yes-     -enter-
24 color depth     -enter-

I'm so glad I found a solution. I've spent way too much time on this instead of loving family or working at work!

---

### Post by biogon on 2007-08-12
How can I reinstall GRUB after XP installs its own bootloader, on a D630, *using the Alternate/Install CD*?

Every single FAQ/tutorial says to use the LiveCD, which, as all of us D630 users know, drops back to BusyBox shell halfway during the boot process.

I burned a SuperGRUB disk and went through the process to restore GRUB, but it seems to have done utterly nothing.

Thank you for your help!

-j

---

### Post by cacycleworks on 2007-08-12
Here's a "how to" that seems pretty comprehensive and has a section about two PageDn "My computer only boots to windows"

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#16](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#16)

Give that a whirl??

:)

---

### Post by biogon on 2007-08-12
> **cacycleworks said:**
> Here's a "how to" that seems pretty comprehensive and has a section about two PageDn "My computer only boots to windows"

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#16](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#16)

Give that a whirl??

:)

Yep, I tried booting off a SuperGRUB disk to restore GRUB, but after I select the partition (after selecting Fix GRUB), I don't get a "SGD has succeeded" message. Instead, it just reboots immediately and automatically.

I don't know why -- maybe it can't find the D630's SATA drive or something?

I do get a single device showing up (hd5,4) or something odd like that, which really confused me.

-j

---

### Post by cacycleworks on 2007-08-13
hmmmm. check out the few steps I needed to do to install ubuntu on my D630... then think if they can apply to booting your live CD... that pci=assign-busses may contribute to not seeing it. Also, there is a way to tell the boot process to load piix... there's a command to get a prompt mid boot and you can modprobe piix to load it. (I read that today, but didn't archive the link...)

Did you try knoppix live CD? I used that to shrink vista partitions (before later just clean sweeping!)

---

### Post by jonsson on 2007-08-19
Has anyone figured out how to disable the touchpad?

I only use the pointing stick and would like to disable the touchpad completely to avoid accidental mouse movements. Or at least prevent mouse clicks by tapping the touchpad. I suppose the scrolling function could be usefull to keep but I doubt that I would use even that very much. I don't like to have to move my hands from the keyboard. ;-)

Btw, I'm assuming the extra two mouse buttons are just duplicates? It would be neat if they could be used as additional mousebuttons... My old Thinkpad had three buttons and I really miss the middle mousebutton. Clicking both buttons emulates the third but I have found that it's actually not that easy to click both at once and I often end up with a left or right click instead of the intended middle click.

---

### Post by cacycleworks on 2007-08-20
Have you tried removing it from the xorg.conf file? Heh, it's really easy to screw it up and not have video start, so must be able to make other things not work. ;) You likely could simply go to the bottom portion and remove the synaptic entry...

Save a back up of the file and familiarize yourself with all text/cli editing (like nano or vi) ... try it and Ctrl-Alt-Backspace to restart X. ... if it "breaks" you can alt-f2 to get a terminal window.

worst case, you can't ever get it to work and cp the backup to xorg.conf and you end up where you are now...

---

### Post by davidmorawski on 2007-08-21
I'm in the opposite situation..I'd like to disable my pointing stick. 

I've removed all of the input devices from xorg.conf, exception for the "Configured Mouse" (/dev/input/mice) and the "Synaptics Touchpad" (/dev/psaux) but my pointing stick still works.

Also, it'd be nice to have them all disabled when I have an external mouse plugged in (which takes about 5 seconds in WinXP :() I wish there were some nice piece of software that would simplify this whole thing, as the X server seems to be a bit inconsistent.

Dave

---

### Post by TheBlackCat13 on 2007-08-22
I am getting a latitude D830 (nvidia graphics, so dealing with intel graphics drivers is not an issue).  I am going to install kubuntu x64 on it (I have some software that I use a lot that will benefit from the 64-bit support).  I understand the installation procedure well enough.  The question I have is whether it would be better to install the current Kubuntu Feisty or install Ubuntu Gutsy Tribe 5 (or 6, depending on when the computer arrives) and then download KDE after installation.  What are the relative advantages and disadvantages of the two approaches?

---

### Post by jonsson on 2007-08-23
> **davidmorawski said:**
> I'm in the opposite situation..I'd like to disable my pointing stick. 

I've removed all of the input devices from xorg.conf, exception for the "Configured Mouse" (/dev/input/mice) and the "Synaptics Touchpad" (/dev/psaux) but my pointing stick still works.

Also, it'd be nice to have them all disabled when I have an external mouse plugged in (which takes about 5 seconds in WinXP :() I wish there were some nice piece of software that would simplify this whole thing, as the X server seems to be a bit inconsistent.

Dave

I can't imagine why you would want to disable the pointing stick? ;-) Except maybe if you connect an external mouse. Anyway, there is a setting in the BIOS that is supposed to achieve that. I haven't tried it (since I don't even own a mouse) but I think you could choose if and how the touchpad and pointing stick (yes, both of them, not individually :sad:) react when a mouse is connected. 

I tried commenting out the synaptics section in my xorg.conf and also found that both the stick and the pad still worked afterwards. :confused:

---

### Post by TheBlackCat13 on 2007-08-23
> **davidmorawski said:**
> I'm in the opposite situation..I'd like to disable my pointing stick. 

Doesn't the nub just come off?

---

### Post by jonsson on 2007-08-23
> **TheBlackCat13 said:**
> Doesn't the nub just come off?

I've used pointing sticks for years on my two previous laptops (Thinkpads) and never had any problems. The Dell one seems slightly less sturdy and has already seemed to be a bit loose a few times. But it has never come off and it has been easy to fix. I assume the next day on site service that they would not let me buy the computer without will take care of it if it really breaks.

Once you get used to it you'll never want a touchpad again! But I suppose this is not the place for that debate... ;-)

---

### Post by TheBlackCat13 on 2007-08-24
I don't mean accidentally, I mean if someone doesn't want the track stick they can remove it entirely instead of worrying about messing with the bios or xorg.conf.  I think it is designed that way so it can be replaced if it wears down or breaks.  I know my old D800 came with an extra nub.

---

### Post by jonsson on 2007-08-25
> **TheBlackCat13 said:**
> I don't mean accidentally, I mean if someone doesn't want the track stick they can remove it entirely...

Aah...

By the way, sound is still a bit of an issue. Apart from the suspend/hibernate problems mentioned above, I have not managed to use the built in mic (I assume there is one?) or the mic input. Obviously this makes VoIP a bit difficult. :neutral:

(My bluetooth headset works without problems, though)

---

### Post by Nicolae on 2007-09-01
> **jonsson said:**
> Has anyone figured out how to disable the touchpad?

...

You can do it with synclient.

You'll need to add ```
Option "SHMConfig" "on"
``` under the synaptics input device section of xorg.conf. Restart X, open a terminal and do ```
synclient TouchpadOff=1
```. Should disable it. I threw it in a simple script in KDE's autostart directory, I assume there's a similar way to do it in Gnome.

EDIT:

And, on a completely unrelated note: With Alsa 1.0.15rc1, the headphone jack works properly (mutes speaker when plugged in, unmutes when not). I followed the directions [here](http://ubuntuforums.org/showthread.php?t=530374), replacing .14 with .15rc1 where needed.

---

### Post by crinos on 2007-09-01
> **Nicolae said:**
> And, on a completely unrelated note: With Alsa 1.0.15rc1, the headphone jack works properly (mutes speaker when plugged in, unmutes when not). I followed the directions [here](http://ubuntuforums.org/showthread.php?t=530374), replacing .14 with .15rc1 where needed.

It would be better if you can make DEB packages so that it could be properly managed by APT :)


I just spent this weekend setting up my new D630 with Kubuntu 7.04 and its working pretty well now. There were a few things I had to tweak to make it work but not too many things.

I got the nVidia graphics option, so I had to install the newest driver from nvidia.com, rather than use the nvidia-glx-new package, and it works great now, with Twinview and everything.

As far as the sound goes, at the moment the inbuilt speakers don't work at all, but the headphone jack does(which suits me anyway), since I only ever use it with headphones, and the sound quality is awful from inbuilt speakers anyway. I got it to behave like this with "options snd-hda-intel model=laptop" at the end of "/etc/modprobe.d/alsa-base". Other options in the "model" field cause it to behave differently, but "laptop" works the best for me personally(headphones only).

The DVD-RW drive wasn't detected by default, but that was as simple as adding "piix" to "/etc/modules", which then allows you to set DMA on the drive("hdparm -d1 /dev/hda") which makes a heck of a difference when playing DVDs!

Haven't had a chance to test out wireless networking yet, but it looks like it will be fine, with native support.

I had and issue with guidance-power-manager.py crashing on startup, but that was easily fixed with the DEBs from here: [https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/112120/comments/6](https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/112120/comments/6)

So all in all, it's working nicely, which is great because it's a really sexy laptop, which is nice and light but packs a bit of punch with performance :)

---

### Post by jonsson on 2007-09-02
> **Nicolae said:**
> You can do it with synclient. 

Yes, that does it! Thanks! :-D

Btw, does the new ALSA stuff also make sound work after suspend and hibernate?

---

### Post by Nicolae on 2007-09-02
> **jonsson said:**
> Btw, does the new ALSA stuff also make sound work after suspend and hibernate?

Seems to. Well, hibernate, anyway. Suspend just shuts the laptop down when I try to resume (and I have to restart X after hibernate, because it starts taking 100% CPU-- wonder if it's an issue with the nvidia drivers....) but sound and wifi still work after hibernate. I'm going to see if I can get suspend to work today, I think.

EDIT: Scanning back on the earlier part of the thread, it seems wifi not working on hibernate may be related to NetworkManager. I've switched to using [wicd](http://wicd.sourceforge.net/) and it works fine.

---

### Post by jonsson on 2007-09-02
I don't have any nvidia hardware or drivers and I don't have those problems so there may well be a connection. Hibernate and suspend work fine, but they kill sound and, if running on batteries, networking.

Those are the only problems left and I can live with them until they hopefully disapperar in some update. ;)

I think the fans seem to run a lot, though? Has anyone else noticed this? I can't imagine that they actually need to run (audibly) close to all the time and I assume this affects battery time.

---

### Post by Lek130 on 2007-09-04
Quick Tipp: For the people who are using Virtualbox. Version 1.5.0 (just released yesterday) It has seemless Guest Integration. What happenes is that you can change the VM into seemless mode and the applications run like normal windows in the host. 

For example, using ubuntu and WinXP guest, I can see outlook as a single window on my ubuntu desktop. very cool!

It also works great with beryl 

Cheers!

---

### Post by Kleenux on 2007-09-05
Following a couple of posts from the beginning of this thread, I must admit, it is amazing how it works well! Even the battery indicator, wireless, sound ... the stuff I thought they would be a pain : flawless install - just one small pb with the mic:

Skype is available for feisty fawn 7.04. It works. However the microphone doesn't seem to work. 
- is there something to unlock somewhere
- a sound mixer where mic is mute?
- or a driver problem?

Thanks

---

### Post by melco on 2007-09-05
I have almost the same issues with sound after hibernamet and internal mic.
All other things looks like works good
P.S. Any1 nows how to use smartcard reader? Any success with it?

---

### Post by pepsun on 2007-09-06
Hi, everyone,

My D630 should arrive at the end of September, so i'm following this thread with great interest :)

On the laptop i'm currently using, i have the very same problem with the fan --> no matter what it just keeps spinning :) Which is kind of annoying... 

Is it the same with the D630? Has anyone else the same "problem"?




pepsun@bilot1:~$

---

### Post by cacycleworks on 2007-09-06
> **pepsun said:**
> Hi, everyone,

My D630 should arrive at the end of September, so i'm following this thread with great interest :)

On the laptop i'm currently using, i have the very same problem with the fan --> no matter what it just keeps spinning :) Which is kind of annoying... 

Is it the same with the D630? Has anyone else the same "problem"?
pepsun@bilot1:~$

These have a fan?? 

;)  I can't tell it's running.  :D

---

### Post by eddie-newbie on 2007-09-08
This post HOW TO is for a clean install of Ubuntu 7.04 Feisty Fawn on Dell Latitude D630 (and maybe a D830) with an NVIDIA 135M NVS Quadro video card.

This guide only is what I have done to get x window working and the video drivers installed.  Lan Networking, touchpad, USB, work fine after the initial install

ASSUMPTIONS
-you have 1 copy of Ubuntu Feisty Fawn 7.04 (i386 Alternate CD Version)
-you have an ethernet connection to the internet with DHCP 
-you have a dell D630 with a NVIDIA 135M Quadro video card
-you know how to create partitions and can install the Ubuntu CD.

Steps
Install the Feisty Fawn CD on your laptop. (Make sure you have your computer plugged to the internet so your computer will setup the DHCP settings for you) After you finish the installation process, your system will reboot and you should get a blue screen with some text that says "Screen Failed to start X server"  Click No, Ok.

You are now at the text Login Screen.  Login and make sure your laptop is connected to the internet.  

At the prompt type  (the sudo command will need your password)

[I] sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot[/I]

After the reboot, you will get the blue screen again.  Login to the prompt as before and type to download the NVIDIA drivers:  (the drivers might be different if newer versions are availabe, you can go to the nvidia website and find the linux drivers for IA32)

[I] wget [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)
[/I] 

Then type the following commands at the prompt.  I will use parentheses for comments.
[I]
sudo Aptitude Install Make[/I]  (did nothing for me but I was told to do it on Nvidia's forum)
* sudo Aptitude Install gcc*   (did nothing for me)
* uname -r*                    (this tells you the version, mine was 2.6.20-16-generic)
* sudo Aptitude Install linux-headers-'version #'*  (replace version number with info from uname -r, e.g. "sudo Aptitude Install linux-headers-2.6.20-16-generic")

* sudo Aptitude Install pkg-config* (did nothing for me)
* sudo Aptitude Install xserver-xorg-dev* (actually did something)

* sudo Aptitude Purge nvidia-glx*  (did nothing for me)
* sudo Aptitude Purge nvidia-glx-new* (did nothing for me)
* sudo Aptitude Purge linux-restricted-modules* (did nothing for me)
* sudo Aptitude Purge linux-restricted-modules-common* (did something)

* sudo rm /lib/linux-restricted-modules/.nvidia_new_installed* (did nothing for me.)

* sudo Aptitude Install g++  *(installs libc6 which you will need for the Nvidia Drivers later on)

if you get a CD Rom error, go to the bottom of this post and I will show you the workaround for installing g++.

* sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run*  (This installs the downloaded NVIDIA drivers on your laptop, a basic screen will pop up and ask you accept a licence, click the following Accpet, Yes, Ok, Yes to let Xconfig Utility, Ok.)

* startx* (and magically, you should be done.  You can change your monitor settings by going to Applications -> System Tools -> NVIDIA X server settings)

--------------------------------------------
CD rom work around.  You should be at the prompt after getting out of the CD Rom error.  We will have to go to X window to use the package manager to download off the internet the g++ libraries.  You can't skip this step otherwise NVIDIA's drivers can't compile to the kernel.  Do the follwoing.
[I]
sudo dpkg-reconfigure xserver-xorg[/I] (this brings to a configuration screen, type in the next few commands, I might have missed an ok or two.)

"Yes, Vesa, Ok, Ok, Ok, No, No, Ok, Ok, Ok, Ok, Ok, Ok, Ok, Ok, Ok, Ok, Ok, Ok, Yes, Ok, Ok, Yes, No, Ok, (choose your monitor resolutions) Ok, Simple, (screen size, I used 15" though it is 14.1") Ok, No, Ok."

After all this, you should be at the prompt again and type:

* startx  *(you will go into the graphical interface for X window, kind of ugly for now.)

choose System->Administration->Synaptic Package Manager  (window opens for the package manager)
choose Settings->Repositories  (settings window pops up.)

Check "source code" box.  (not sure this is needed by the kernel but I did it anyway)
Uncheck "CD Rom with Ubuntu.  (this is in the box at the bottom of the window.)
Close Settings Window.

Select from the package list "g++" and choose "mark for installation"  (this should install 4 different things)
Click "Apply"  (the program will then download and install from the internet -- quite a work around for the cd rom huh?)

Then go to the top right shutdown button and logout.  

At this point, I think you should be at the prompt and can continue with the "sudo sh NVIDIA...." step from above.  ***If X Window is still on,  press Ctrl-Alt-F2, login to the prompt, type "sudo /etc/init.d/gdm stop" and that should kill X window so you can continue with the install of the Drivers.
---------------------------------------------

Hope this helps, it took me a long figure out everything since I didn't know what I was doing at all.  I listed a lot of steps that didn't seem necessary to me but I think it is better to be thorough than leave something out that might be important later on.  Best of Luck and enjoy!



***********************************************************************************
HOW TO add CD Rom Support for D630.

In a terminal screen or at the prompt type:
[I]
modprobe ata_pixx
modprobe ata_generic

sudo cp /etc/modules /temp
sudo echo piix >> /tmp/modules
sudo cp /tmp/modules /etc/modules
sudo reboot
[/I]

*******************************************************************
INTEL Wireless 3945 now works

What I had to do was go into the Synaptic Package Manager and reinstall the following
linux-restricted-modules-2.6.20-16 (Non-Free linux 2.6.20 modules on x86/x86_64).  This package contains the drivers for the the wireless card.

Unfortunately, this process also reinstalls our previous NVIDIA drivers that don't work.  So we have to delete the old restricted modules manually by:
[i]
sudo rm -r /lib/linux-restricted-modules/2.6.20-16-generic/nvidia    
sudo rm -r /lib/linux-restricted-modules/2.6.20-16-generic/nvidia_new
sudo rm -r /lib/linux-restricted-modules/2.6.20-16-generic/nvidia_legacy
[/i]

Then recompile the new NVIDIA drivers again.
Press Crtl-Alt-F2 to go to a terminal.
[i]
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run[/i]

**of course, feel free to replace the 2.6.20-16 if you are using a different version.  Find your version by using *uname -r *

---

### Post by jonsson on 2007-09-13
The problem with no network after suspend seems to have gone away! :) I haven't tried hibernate recently but I have now several times in a row put the computer in suspend, woken it up and used wifi. :) I haven't done anything to fix this myself so I suppose this is due to some update I didn't even notice.

---

### Post by jonsson on 2007-09-13
> **cacycleworks said:**
> These have a fan?? 

;)  I can't tell it's running.  :D

Well, on mine it's pretty obvious... But it was about the same with my old thinkpad. Maybe I have some incorrect settings? CPU usually runs @ 800 MHz so it really shouldn't get very warm, should it?

---

### Post by Lek130 on 2007-09-19
Anyone tried to upgrade to Gutsy T5 or beta and sticks to it?

I tried a live CD with Gutsy Tribe 4, but it got stuck on the tty issue (same as on the feisty live cd). I did not want to try to install it then, because its a work Laptop.

Appreciate some comments and anyone who is trying!

---

### Post by apel_2804 on 2007-09-20
Tribe 5 works but without sound.

:(

---

### Post by Lek130 on 2007-09-20
Well even Feisty has its sound issues. Although I got it working for me eventually. The ALSA driver did not change ... That said, does USB (head phones vis usb for instance) sound work for you? this always worked on Feisty

---

### Post by TheBlackCat13 on 2007-09-20
Don't meant to nitpick but it should be *modprobe ata_piix*

I'm currently getting everything set up.  I'll have a more complete overview later.

---

### Post by arjanhs on 2007-09-26
I'm using a D830, and having trouble installing Feitsy, i could try the alternate cd, but i think i will wait for the 7.10 release, hopefully the problems are fixed in this version. Can someone confirm this?

Arjan

---

### Post by cacycleworks on 2007-09-26
> **arjanhs said:**
> I'm using a D830, and having trouble installing Feitsy, i could try the alternate cd, but i think i will wait for the 7.10 release, hopefully the problems are fixed in this version. Can someone confirm this?

Arjan

I believe the 7.10 will not be simple install. I also did a full write up of how to install 64bit OS onto Dell D630/830.  That post is here:
url ---
[http://ubuntuforums.org/showthread.php?t=518702](http://ubuntuforums.org/showthread.php?t=518702)

( [clickable link]("http://ubuntuforums.org/showthread.php?t=518702") )

Since we already did the research, if you follow one of the guides put together, installing on the D630 should be "easy".

---

### Post by TheBlackCat13 on 2007-09-28
Has anyone tried installing the Gutsy beta on ther D630/D830?  I am thinking of giving it a try, I haven't done enough with it to make a clean install that damaging, but I was wondering if anyone had bad luck with it.

---

### Post by cacycleworks on 2007-09-30
> **TheBlackCat13 said:**
> Has anyone tried installing the Gutsy beta on ther D630/D830?  I am thinking of giving it a try, I haven't done enough with it to make a clean install that damaging, but I was wondering if anyone had bad luck with it.

I did during my process for trying to get software installed and it seemed similar to fiesty. I'm quite certain it would install just fine if you follow the few simple steps I detailed which worked for me.

:) Chris

---

### Post by crinos on 2007-10-01
I've been running Gutsy(Kubuntu) since Tribe5 was first released. I've had various breakages since then, but non too severe for someone familiar with Ubuntu.

The latest nVidia drivers are broken for me running dual screens(with port replicator). Downgrading to 100.14.11 fixes the problem.

Most things that have broken after upgrades I've been able to fix by reinstalling the broken package. ie, kicker has failed to work a couple of times after upgrades, but 'sudo aptitude reinstall kicker' has fixed it both times.

Apart from that, the power management stuff was broken with the Nvidia drivers, but fixed by some DEBs in the relevant bug report(I think I've posted them in this thread).

I can't say Kubuntu is really very different to Feisty, other than newer packages... my short look at Ubuntu seemed like it was significantly different to Feisty though.

---

### Post by TheBlackCat13 on 2007-10-01
I installed it.  I can't compile compiz correctly, monitor detection still isn't working properly so I am still using the less-than-optimal Xinerama, and grub didn't recognize my vista partition.  However, the system recognized my audigy 2 zs right away and the automatic Nvidia driver installer is a welcome addition.  For the most part it is working really well, no worse than Feisty and better in many ways.

---

### Post by tturrisi on 2007-10-01
> **TheBlackCat13 said:**
> Has anyone tried installing the Gutsy beta on ther D630/D830?  I am thinking of giving it a try, I haven't done enough with it to make a clean install that damaging, but I was wondering if anyone had bad luck with it.
I have debian sid on a d830 and made a page about it here:
[http://members.cox.net/tonyt/d830/](http://members.cox.net/tonyt/d830/)

---

### Post by new_user_00 on 2007-10-08
hello guys, 

has anyone of you NOT experienced the fan issue?`i just bought a d630 and now i am very concerned, because constant fan noise would be a no go... 

and to those who are having thus problem: is your configuration with _dedicated_ or with _integrated_ graphics?

regards

---

### Post by ntaylor0909 on 2007-10-08
I have been running a D630 with Feisty and now the Gutsy beta and had no fan issues whatsoever. In fact, I have only heard the fan once or twice. I didn't like the way Feisty ran on the laptop, but gutsy is saweet(fast, stable, and gorgeous). The only thing that doesn't work is the audio which I expect will be fixed in the final version, or there will be a decent work around later. My 4965ABGN card is recognized out of the box and everything runs great. I am running with the Nvidia graphics card which the restricted driver manager in gutsy recognized and installed the driver for. I have also installed feisty on a D620 and had no issues at all including with the fan. Now that machine also had the nvidia graphics card. Grub automaically recongized my vista(blegh, yuck, lame, have to use it sometimes for work), and the DELL Diagnostics partition. 

)Hope that helps.:)

---

### Post by new_user_00 on 2007-10-09
thank you for your reply. *THUMBS UP

---

### Post by skiski on 2007-10-09
Hi,

I've just received my d630 yesterday, after 2 months of waiting...

I've tried to install ubuntu but since Vista, Dell utility and Recovery already take 3 primary partitions, I had to set the root partition as a logical partition and as I've learn, you cannot boot from such a partition.

So the question is: can I remove the "recovery" partition without problems?

For the fan, as far as I've heard, my fan is very quiet with vista, so I assume it would be the same with ubuntu. 

And for the sound, it seems that the cvs version of alsa solves the problem. But, obviously, I haven't tried yet.

---

### Post by meastp on 2007-10-12
RC is out...

What is the status on sound, suspend, fan etc. ?

---

### Post by skiski on 2007-10-15
I haven't tried ubuntu yet (I'm waiting for 7.10), but with fedora 7 everithing works fine. After a big yum update, the nvidia video card was working fine and I didn't had to do anything to have soud. Wi-fi is also working after some quite workaround.

It seems that after pluging and unpluging a jack, the soud stops to works with the speaker, but the headphone line keeps working, which is fine by me.

The only annoyance I've noticed is that sometimes, the "windows" key does not work and I need to reboot to use it.

It also seems that after supsend, networkmanager fails to connect using wifi, but system-config-network still works, so it's not a big deal.

And the fan is very quiet.

---

### Post by mk1970 on 2007-10-15
I'm running 7.10 RC and everything seems to be fine. Here's my hardware configuration: [http://www.iki.fi/kuparine/comp/d630/](http://www.iki.fi/kuparine/comp/d630/)

---

### Post by jhernandez1270 on 2007-10-15
Lek130,

try undocking the CD/DVD on your D630 and using a USB CDROM (just during the install)...that is how I got around the tty error during install.

---

### Post by Lek130 on 2007-10-16
hi! 

I upgraded to Gutsy on Sunday! It took about 2+ hours for my d630. I did try gutsy so on my 2 year old desktop PC.

I went the ubunto.org recommended way of using the update manager. That worked without issue and after the final reboot the system came up again in almost working condition.

I have to praise the update manager. Going from anything to anything in Windows (XP to Vista etc) is lengthy and unhappy, but compared to ubuntu ... NICE.

I knew that Gutsy has issues with d630 sound and so I dont have sound anymore (similar to my initial feisty installation some month back). I knew that, I am not worried about it (USB headset always does the trick, which is more important to me).

The 3d effects - compiz fusion did not work initially. in effect this graphic chip set has been blacklsited and an easy file change to not blacklist make it work - NO ISSUES. Beryl was nice but Fusion is the killer.
 
WIFI now is easy as it has a restricted driver there. No issue at all. 

DUAL MONITORS - my main motiviation for the upgrade - did not work at first. It took some reading and then I found a how to with the easy answer.

Look at [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
It explains the issues with the intel graphic driver very well. I got it working in 3D highest possible resolution on monitor and laptop screen, but only with monitors being virtually below each other. There is an issue with the addressable memory in the driver ... read it there. I tried it and it works!

:KS

Its really cool. In effect using 3d and the cube. Gives you a big super cube. For each workspace you get a 2nd one on the 2nd screen. With CTRL ALT CURSOR you see both flpping by. NEAT! :guitar:

and gutsy is faster. 3d at any rate. although it was fast before. 

BTW I did of course do a full backup (using tar and a big USB disk), just to make sure I can go back. After all I am working on this thing.

Very cool. 

If you have some time. Go for it. I would recommend a weekend, just in case so that you have time revert back, in case you use it for your work.

Its not difficult upgrading or even going back for that matter, just time consuming.

Cheers!

UPDATE I tried this link [http://ubuntuforums.org/showthread.php?t=575653](http://ubuntuforums.org/showthread.php?t=575653) and got sound working instantly. :) Now Gutsy for me is the better feisty and I would recommend people the upgrade.

---

### Post by ntaylor0909 on 2007-10-18
I am running Gutsy final release on my d630. It works great. My 4965 wifi card is recognized out of the box, my Nvidia card was recognized, and everything is running GREAT. I had 2 issues that I had to work through and here are the solutions:

Gutsy sound problem on D630. Still no sound, but there is a post on the Ubuntu wiki with the solution. Use Method G about halfway down the page. It worked perfectly for me:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)


D-port port replicater/docking station. I was having trouble getting the computer to use the monitor on the docking station. What I ended up having to do was run:

sudo nvidia-settings

in the display configuration, while on the docking station, I disabled the on-board screen,and set the monitor on the docking station as the main monitor It works great. When I boot the laptop on the docking station, that monitor turns on, and when I boot up away from the docking station, the built in monitor works. 

Hope that helps someone.  Gutsy is an awesome release and a great accomplishment. Keep up the good work.

:KS

---

### Post by Lek130 on 2007-10-19
You can use xrandr to activate both monitors at the same time. Follow the link above.

If you type in xrandr into the shell you will see the max resolution of both. Based on my link above you need to set a VIRTUAL setting in the xorg.conf. 

After that restart and use xrandr to set as per link above, the monitors.
the new displayconfig-gtk seems useless to me and does not work. I saw some project starting to work on xrandr graphical front ends, which I think is the better way.

BTW xrandr and corg now support hot plug and play.

---

### Post by mzi on 2008-01-03
I think you can dl a bootable CD containing the Dell partition (mainly diagnostics) on their website. So it is safe to remove it.

---

