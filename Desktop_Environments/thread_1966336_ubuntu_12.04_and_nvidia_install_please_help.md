---
title: "ubuntu 12.04 and nvidia install please help"
date: 2012-04-27
forum: Desktop Environments
---

### Post by Mia1990 on 2012-04-27
I just have installed ubuntu 12.04 about a hour ago and i can't install the nvidia driver in additional drivers or in the software center. So i installed synaptic and i can't install it from there also. I use the nvidia 173 driver. So does anyone know how to install this driver?

---

### Post by kyletstrand on 2012-04-27
Have you tried manually installing drivers directly from the nVidia website?

[http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")

Just a thought.

---

### Post by Mia1990 on 2012-04-27
Thank you for the quick reply,

No i do not know how to install a run file that what there drivers are and the ones from the software center install other files too.

---

### Post by tomatoe on 2012-04-27
Older drivers from USC have dependency problems.

To execute that driver .run file type in terminal

```
sudo sh (file name)
```

---

### Post by geovino on 2012-04-27
> **kyletstrand said:**
> Have you tried manually installing drivers directly from the nVidia website?

[http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")

Just a thought.

I downloaded the 173 64bit version and its a .run file. How do you install it. It wants to open in gedit. Never seen one like that before. 

There is a nvidia-173 driver in Synaptic. Would that work instead? 

Whatever nvidia driver that Ubuntu wants to install from additional drivers just kills Unity on reboot in an nvidia geforce 6100 which I have. What would work?

---

### Post by Mia1990 on 2012-04-27
Ok if the older cards have dependency problems would it be safe to run it or would  it be better to run the *nouveau *open source Nvidia 3d driver?

---

### Post by geovino on 2012-04-27
> **Mia1990 said:**
> Ok if the older cards have dependency problems would it be safe to run it or would  it be better to run the *nouveau *open source Nvidia 3d driver?

If I installed 12.04 and didn't add any video drivers, what do I have for video? isn't it Nouveau? If not, how do I install Nouveau? With Synaptic?

---

### Post by tomatoe on 2012-04-28
> **geovino said:**
> If I installed 12.04 and didn't add any video drivers, what do I have for video? isn't it Nouveau? If not, how do I install Nouveau? With Synaptic?


Nouveau comes as default driver, so it is already installed.

---

### Post by geovino on 2012-04-28
> **tomatoe said:**
> Nouveau comes as default driver, so it is already installed.

That's what I thought. 

I'm fine with nouveau until I can find a good way to install nvidia-173 or whatever is the best driver for geforce 6100 video.

Thanks.

---

### Post by Mia1990 on 2012-04-28
I was talking about there 3d driver i know ubuntu ships with the 2d driver by default.

---

### Post by rtalcott on 2012-04-28
I may have the same problem...upgraded to 12.04 from 11.10...I cannot install the nVidia drivers AND I cannot get 3D to run...I'm stuck in Unity2D...everything was fine under 11.10.
rt

---

### Post by geovino on 2012-04-28
> **Mia1990 said:**
> I was talking about there 3d driver i know ubuntu ships with the 2d driver by default.

So what is the nouveau 3D driver called?

---

### Post by tomatoe on 2012-04-28
afaik nouveau has no 3D driver. If you want 3D you need to install nVidia's drivers.
To do so in terminal:
```
sudo apt-get install nvidia-current
```

But it is only for newer graphic cards. For example, doesn't work on my FX 5200. I guess it works on 6th series and newer.

---

### Post by geovino on 2012-04-28
> **tomatoe said:**
> afaik nouveau has no 3D driver. If you want 3D you need to install nVidia's drivers.
To do so in terminal:
```
sudo apt-get install nvidia-current
```

But it is only for newer graphic cards. For example, doesn't work on my FX 5200. I guess it works on 6th series and newer.

I just tried to install nvidia-173 which I have used in the past and when I went to apply it in Synaptic, it said to fix broken packages first. What packages are broken? Never seen that before.

---

### Post by searchfgold6789 on 2012-04-28
The news is, apparently nVidia needs to update their driver so that it works with the latest release of the X.org window system. I have inquired about this and will post back if I hear anything.
In the meantime, you'll have to use the noveau driver or no driver.

---

### Post by tomatoe on 2012-04-29
> **geovino said:**
> I just tried to install nvidia-173 which I have used in the past and when I went to apply it in Synaptic, it said to fix broken packages first. What packages are broken? Never seen that before.

It says about those broken packages because of some dependencies.

---

### Post by blitzit on 2012-04-29
I installed NVIDIA-Linux-x86-295 after disabling and blacklisting the default drivers that came along with ubuntu. I need to do this to utilize the dual-monitors that my workstation has.

Everything seems to run fine. Am I missing something?

---

### Post by turbos4 on 2012-04-29
I need nvidia driver i ubuntu desktop 12.04. Fungerte i ubuntu desktop 11.04 og 11.10.

Have tried:

#sudo apt-get install nvidia-current

#sudo apt-get install nvidia-current-updates

Have also tried to install the driver from NVIDIA

#sudo sh NVIDIA*

I get the same 'dmesg' every time!

dmesg:

[   25.539150] NVRM: RmInitAdapter failed! (0x27:0x38:1190)
[   25.539159] NVRM: rm_init_adapter(0) failed
[   25.728026] init: lightdm main process (1354) terminated with status 1
[   40.753750] init: failsafe-x main process (1788) terminated with status 1

Have also tried nouveau open source

#sudo apt-get install xserver-xorg-video-nouveau

But then i don't get '1680x1050_60'

Try to add new mode, but no luck!

xrandr:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  



#lspci | grep VGA

01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560] (rev a1)

How can I fix this?

---

### Post by tomatoe on 2012-04-29
So, after installing nvidia-current it doesn't appear in additional drivers?

> Have also tried nouveau open source

#sudo apt-get install xserver-xorg-video-nouveau

But then i don't get '1680x1050_60

xserver-xorg-video-nouveau is already installed by default, but you have to remove nVidia driver to use nouveau driver.

---

### Post by Mia1990 on 2012-04-29
The driver is called Nouveau and there website says it's a Gallium3D-based driver there from the Mesa drivers. Here's the website   [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/) 

I'm not talking about the driver that ships with ubuntu i know they ship with nouveau 2d driver. There also working on a 3d driver for nvidia cards too.

---

### Post by robertsp on 2012-04-29
> **searchfgold6789 said:**
> The news is, apparently nVidia needs to update their driver so that it works with the latest release of the X.org window system. I have inquired about this and will post back if I hear anything.
In the meantime, you'll have to use the noveau driver or no driver.
Thanks searchfgold6789, like many, I'm going to use Unity2D with the installed nvidia driver until nvidia sort out the problem. Hopefully not too long!

---

### Post by Murphy1138 on 2012-04-29
Download the latest Nvidia driver and stick it in your Downloads folder.

hit ctrl + alt + F2 
logon as your user account.
then
sudo stop lightdm
then
cd Downloads
sudo sh ./NVIDIA-Linux-x86_64-295.40.run 
(you can press tab once you type ./Nv to auto type the rest of the file name)

Go through the prompts (yes yes yes yes ...) then reboot :)
8-)\\:D/

---

### Post by symon1980 on 2012-04-30
I would not recommend manually installing the downloaded nvidia driver website unless you are prepared for a future breakage and know how to fix it...
Installing Nvidia drivers from the website manually will mean you will get xorg updates in future with no nvidia driver updates  because it wasn't installed from the repository.... breakages between nvidia/xorg can and do occur from time to time

If you're not scared of fixing a broken desktop... then go ahead ;)

---

### Post by zecoyote007 on 2012-04-30
Hi guys, 

In order to use nvidia-173 or nvidia-96, please see my post here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/922268](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/922268)

I found a workaround: keep the 11.10 version of the Xorg server :-D
No conflict at all with any package from 12.04 !!!

nvidia-173 drivers are not compatible with Xorg (ABI to be precise) version released in 12.04.
So I stick with 11.10 version of Xorg. I had to make the following changes to backport Xorg:

1) In /etc/apt/sources.list :

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main

2) In /etc/apt/preferences:

Package: xorg xserver-xorg*
Pin: release a=oneiric
Pin-Priority: 1050

3) Note related to nvidia-173/96 on Ubuntu 12.04 (optional if you face slow graphics)
I'm using old hardware with nvidia-173 drivers and I don't like the fact "composite" is mandatory to use Unity correctly (very laggy) I had to force composite to switch it "off" to avoid laggy windows by modifying /etc/X11/xorg.conf:

Section "Extensions"
    Option "Composite" "Disable"
EndSection

Enjoy.

Nicolas

---

### Post by mips on 2012-04-30
Has anybody tried the X-Swat PPA yet? [https://launchpad.net/~ubuntu-x-swat/+archive/ppa](https://launchpad.net/~ubuntu-x-swat/+archive/ppa)

---

### Post by tomatoe on 2012-04-30
> Has anybody tried the X-Swat PPA yet? [https://launchpad.net/~ubuntu-x-swat/+archive/ppa]("https://launchpad.net/%7Eubuntu-x-swat/+archive/ppa")Yep, I have tried it, no good :(

---

### Post by tomatoe on 2012-04-30
> **zecoyote007 said:**
> Hi guys, 

In order to use nvidia-173 or nvidia-96, please see my post here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/922268](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/922268)

I found a workaround: keep the 11.10 version of the Xorg server :-D
No conflict at all with any package from 12.04 !!!

nvidia-173 drivers are not compatible with Xorg (ABI to be precise) version released in 12.04.
So I stick with 11.10 version of Xorg. I had to make the following changes to backport Xorg:

1) In /etc/apt/sources.list :

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main

2) In /etc/apt/preferences:

Package: xorg xserver-xorg*
Pin: release a=oneiric
Pin-Priority: 1050

3) Note related to nvidia-173/96 on Ubuntu 12.04 (optional if you face slow graphics)
I'm using old hardware with nvidia-173 drivers and I don't like the fact "composite" is mandatory to use Unity correctly (very laggy) I had to force composite to switch it "off" to avoid laggy windows by modifying /etc/X11/xorg.conf:

Section "Extensions"
    Option "Composite" "Disable"
EndSection

Enjoy.

Nicolas

Hi!

Thanks, man, worked like a charm for me!

---

### Post by rtalcott on 2012-04-30
FIXED!  Latest updates allowed me to install nVidia current and all is now well!
rt

---

### Post by Pablo Pablovski on 2012-04-30
Really? I don't see any updates. What version are you running? What drivers do you now have installed? What PPA did they come from?

How many beans make five? :p

---

### Post by rtalcott on 2012-04-30
Pablo...I am running a newly installed version of 12.04...installed on Saturday I believe...I saw 6 upgrades maybe an hour ago and one maybe two were xorg...up till now I could only run Unity in 2D and could NOT install nVidia-current...AFTER downloading the updates I was able to install nVidia-current and I rebooted and logged in Unity3D...machine is off now but whatever nVidia-current is...that is what I have loaded...

give me a bit more time to work out the bean question!
rt

---

### Post by draptik on 2012-04-30
@rtalcott msg #28

This update (nvidia-current 295.40-0ubuntu1) did not solve the problem for me.

Ubuntu 11.10 with graphic card "GeForce 9500 GT" and nvidia-173 driver works.

Ubuntu 12.04 with nvidia-current (295.40-0ubuntu1) does not. Screen turns blank. :-(

Ubuntu 12.04 with "aptitude purge nvidia-current" at least boots X. Although I only get 1 of my 2 monitors in low res.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053)

---

### Post by mips on 2012-04-30
> **draptik said:**
> 
Ubuntu 12.04 with nvidia-current (295.40-0ubuntu1) does not. Screen turns blank. :-(


Just out of curiosity what happens if you add the '**nomodeset**' kernel parameter in your grub config? You can temporarily change it when you reboot and hitting 'e' for edit to add that parameter.

---

### Post by draptik on 2012-04-30
> **mips said:**
> Just out of curiosity what happens if you add the '**nomodeset**' kernel parameter in your grub config? You can temporarily change it when you reboot and hitting 'e' for edit to add that parameter.

I've already added the nomodeset option: Sadly, it does change a thing. The screen is blank, and /var/log/* does not give me a clue either.

---

### Post by mips on 2012-04-30
> **draptik said:**
> I've already added the nomodeset option: Sadly, it does change a thing. The screen is blank, and /var/log/* does not give me a clue either.

Hmm, wonder why people are experiencing these problems. I installed xubuntu 12.04 today followed by the nvidia drivers from the x-swat ppa and everything works 100%.

Can only imagine the frustration, not a nice thing to be struggling with.

---

### Post by RJARRRPCGP on 2012-05-01
> **draptik said:**
> @rtalcott msg #28

This update (nvidia-current 295.40-0ubuntu1) did not solve the problem for me.

Ubuntu 11.10 with graphic card "GeForce 9500 GT" and nvidia-173 driver works.

Ubuntu 12.04 with nvidia-current (295.40-0ubuntu1) does not. Screen turns blank. :-(

Something's fishy! Nvidia's web site says that even the GeForce 6 series is still supported! 

Thus, it don't make sense for it to barf on a GeForce 9 series.

(Reminds me of vice-versa, when I tried to use Dapper with GeForce 7 series back in 2007 or 2008 lol)

GeForce 9500 GT is supported, according to Nvidia's web site.

---

### Post by lamawithonel on 2012-05-02
I'm having a similar problem to the extreme.  The Live CD won't even boot.

---

### Post by Pablo Pablovski on 2012-05-03
Nvidia driver **295.49** released...

[http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html)

Not yet in the repositories, it seems, so it was a manual install. Works for me on 11.04. About to try it on my 11.10 Kubuntu installation.

Good luck!

---

### Post by draptik on 2012-05-03
Edit: This is wrong: "This seems to be a problem with Ubuntu's Xorg own API (I think it's called ABI). So, yes, the card is supported by NVIDIA. It results in my graphics card not working."

ABI: Application Binary Interface

The new version of Xorg (used by Ubuntu 12.04) has a new ABI.
NVIDIA currently does not provide drivers for all video cards with this new interface.
From other posts I've read NVIDIA is aware of the problem and they are working hard to resolve the issue.

---

### Post by MoebusNet on 2012-05-05
> **zecoyote007 said:**
> Hi guys, 

In order to use nvidia-173 or nvidia-96, please see my post here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/922268](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/922268)

I found a workaround: keep the 11.10 version of the Xorg server :-D
No conflict at all with any package from 12.04 !!!

nvidia-173 drivers are not compatible with Xorg (ABI to be precise) version released in 12.04.
So I stick with 11.10 version of Xorg. I had to make the following changes to backport Xorg:

1) In /etc/apt/sources.list :

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main

2) In /etc/apt/preferences:

Package: xorg xserver-xorg*
Pin: release a=oneiric
Pin-Priority: 1050

3) Note related to nvidia-173/96 on Ubuntu 12.04 (optional if you face slow graphics)
I'm using old hardware with nvidia-173 drivers and I don't like the fact "composite" is mandatory to use Unity correctly (very laggy) I had to force composite to switch it "off" to avoid laggy windows by modifying /etc/X11/xorg.conf:

Section "Extensions"
    Option "Composite" "Disable"
EndSection

Enjoy.

Nicolas

I'm running Lubuntu 12.04 on an antique Dell Latitude D800 with an Nvidia Geforce4 4200 video card with 32 Mb vram. This worked for me for the 96 driver. Just a couple of "gotchas" for me:
1) The nouveau driver kept locking up my computer after I edited /etc/apt/sources.list but before I could create /etc/apt/preferences with Chromium open to this thread to read the instructions. I used a different computer to read the instructions while I worked on the D800 to avoid the lockups.
2) I was puzzled by the reference to /etc/apt/preferences because it did not exist in my 12.04 file system. I took a chance and created the file as above.
3) I couldn't install the 96 driver through Preferences>Additional Drivers or Synaptic after the above edits, so I used Lubuntu Software Center to download and install it. I had to shut down and log out a couple of times before the driver took effect.

Hopefully someone with more knowledge than I can clean this up just a little to make it clearer for those of us still using antiques.

Thanks, Nicolas

---

### Post by briancb on 2012-05-13
12.04 is dissapointing so far:
Operating System:Linux-x86_64
NVIDIA Driver Version:295.49
Graphics Processor:GeForce 9500 GT

At boot the screen goes black and takes forever to load the unity screen. When trying to run XBMC if you use the mouse it crashes. use the keybord woks in normal videos but choppy. Does not play blue ray downloads at all just sound. Try to exit xbmc you have to use the reboot button.

Movie player works ok but I use my system as a medi centre and I need XBMC which worked perfectly in 11.10

EDIT

I have gone back to 11.10 until this is sorted.



Brian

---

### Post by robertsp on 2012-05-15
Well after waiting around for a while, I have now installed Nvidia driver version 295.49 from the ubuntu-proposed repository. The result:

Unity 3D will run properly, but rather too slowly for my liking.

So I installed gnome-shell (Gnome 3). This runs OK with no noticeable speed problem. So I'm not sure what is causing the Unity slowness, but I have settled into using Gnome 3 quite happily.

Configuration:

64-bit Ubuntu Precise 12.04
Processor: AMD Athlon(tm) II X4 620
Graphics Processor: GeForce 6150SE nForce 430 512MB

Thanks to all who have contributed.

---

### Post by rokky on 2012-06-07
> **MoebusNet said:**
> I'm running Lubuntu 12.04 on an antique Dell Latitude D800 with an Nvidia Geforce4 4200 video card with 32 Mb vram. This worked for me for the 96 driver. Just a couple of "gotchas" for me:
1) The nouveau driver kept locking up my computer after I edited /etc/apt/sources.list but before I could create /etc/apt/preferences with Chromium open to this thread to read the instructions. I used a different computer to read the instructions while I worked on the D800 to avoid the lockups.
2) I was puzzled by the reference to /etc/apt/preferences because it did not exist in my 12.04 file system. I took a chance and created the file as above.
3) I couldn't install the 96 driver through Preferences>Additional Drivers or Synaptic after the above edits, so I used Lubuntu Software Center to download and install it. I had to shut down and log out a couple of times before the driver took effect.

Hopefully someone with more knowledge than I can clean this up just a little to make it clearer for those of us still using antiques.

Thanks, Nicolas

Thanks for the pointers, Nicolas.  I will check it out.  I have a D800, also - "antique",eh?  It was a nice step up for me mainly because of the WXGA 1920x1200 screen :guitar:   

I am looking at D820/830 models on CraigsList since it seems the screens are interchangeable (preferably cheap due to bad or lower-res screens), plus I could get a Core2 CPU to get around the annoying PAE requirement for Kubuntu.  

This is about as crazy as upgrading Windows with all these aggravating hardware gotchas - I thought Linux was supposed to prolong the lives of older PC's  :confused:

---

### Post by Byb on 2012-07-01
Hi MœbusNet and Rokky
I have this antique D800 too, with a native wxga 1680*1050 LCD with a 4200* nv28 chip upgraded from a Fujitsu/Siemens Amilo M7405 + intel 855GM + 11.10 then to 12.04 standard.
I reached to have the nvidia96 to work (with the Xord downgrade trick) far better than nouveau which corrupted my cursor and screen.
Although, now I have both suspend/hibernation that wake up to a dark screen and killing xorg nor ctrl+Alt+F1 won't bring screen back.
Do you have this issue too?

*before I remove XP, I upgraded the video bios with the Dell supplied package  (bad idea?)(I uploaded it [here]("https://bugs.freedesktop.org/show_bug.cgi?id=50403"))

---

