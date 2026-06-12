---
title: "ubuntu 8.10 on Dell XPS M1530"
date: 2008-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by melenor on 2008-10-30
Alright i just installed ubuntu 8.10 on my Dell XPS M1530, I am having two problems.
1. My touchpad doesn't work or when i accidently touch it, it messes up my laptop by sending a weird signal to the computer.
2. I tried to enable the restricted nvidia driver but when i click activate nothing seems to happen, but when i click activate on the boardcomm drivers they activated and work

---

### Post by drsaamah on 2008-10-31
the trackpad on the 1530 has some WEIRD issues, and I have no idea why, because I've installed Linux OS's of various flavors at least 6 or 7 times on my m1330 without any trackpad issues.
I did just install Hardy on my friend's new 1530 two weeks ago, and if the trackpad issue on Intrepid is the same problem that existed on Hardy the solution is to add a parameter to the end of some line in the /boot/grub/menu.lst file.  I can't remember exactly, but just search "1530 trackpad" in the Dell portion of these forums and you ought to find the solution.
Best of luck!

---

### Post by Gausian on 2008-10-31
add
```
i8042.nomux=1
```

to the kernel line in /boot/grub/menu.lst

this will fix your touchpad mouse

---

### Post by Elswood on 2008-10-31
Okay.  I've opened the boot/grub/lst.  Exactly where do I put this command there?  Thanks for your patience!

---

### Post by mihaiv on 2008-10-31
> **Elswood said:**
> Okay.  I've opened the boot/grub/lst.  Exactly where do I put this command there?  Thanks for your patience!

At the end of the kernel line. Something like:
```

kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=FFFF ro quiet splash **i8042.nomux=1**

```

---

### Post by mitchc2 on 2008-10-31
I just upgraded my XPS 1530 to 8.10, and it seems to be working great, except for two things.  First, after the upgrade, my sound disappeared.  I followed the instructions [here]("https://wiki.edubuntu.org/InstallingUbuntuOnADellXPSM1530#Microphone/Sound%20doesn%27t%20work%20or%20Audio%20buttons%20don%27t%20work%20right") to get that working again:

> Reboot. Once you boot back up, open gnome-volume-control (using the applet or from the terminal). Go to Edit -> Preferences, and Turn on PCM, Front, Surround, Center, LFE, Capture, Capture 1, Capture 2, Capture 3, Digital, and Digital Input Source. Unmute them all and turn them all up. Make sure you do the same for the Recording tab. Under the options tab, change the source to Digital Mic 1. Close the manager. 

One of my sound inputs had been muted somehow, so that was fixed.  

The only other thing that is happening now is that my wifi activity light is blinking like crazy now.  Before when I was running 8.04, I didn't even know i had a wifi light.

---

### Post by Frostsongr on 2008-10-31
> **Gausian said:**
> add
```
i8042.nomux=1
```

to the kernel line in /boot/grub/menu.lst

this will fix your touchpad mouse

Can confirm that this fixed my 1530 using Ubuntu 8.10 Touchpad problems as well. 

To disable the touchpad completely after you change your /boot/grub/menu.lst and reboot. Go to Preferences > Mouse. Then click the Touchpad tab and uncheck "Enable touchpad". That's it.

---

### Post by accesshater on 2008-11-01
Does somebody know if the hd issue is fixed in 8.10 (load cycle problem).

---

### Post by jheylin on 2008-11-01
I just put 8.10 on my Dell XPS 1530 and the mic doesn't work either. In the volume control it automatically keeps muting the microphone and un-muting it doesn't work since it automatically mutes it again. Any help?

---

### Post by Jorell00 on 2008-11-01
Upgrading Bios to A09 , solved my touchpad issues

---

### Post by damis648 on 2008-11-01
Visit the wiki for trackpad info:
[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#Touchpad%20speed%20is%20lame](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#Touchpad%20speed%20is%20lame)
or
[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#Touchpad%20is%20totally%20not%20working%20after%20lid%20is%20shut](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#Touchpad%20is%20totally%20not%20working%20after%20lid%20is%20shut)

---

### Post by Makaai on 2008-11-02
Thank you Damis!
That workaround to increase touchpad speed works perfectly on my XPS!
I saw some other tricks on that page, and I tried that one for the fingerprint that needs to type enter after swipping, but unluckly my xorg crashed, I think because my keyboard it's it (italian) ad maybe it's different...

---

### Post by damis648 on 2008-11-02
> **Makaai said:**
> Thank you Damis!
That workaround to increase touchpad speed works perfectly on my XPS!
I saw some other tricks on that page, and I tried that one for the fingerprint that needs to type enter after swipping, but unluckly my xorg crashed, I think because my keyboard it's it (italian) ad maybe it's different...

Thats great! Glad I could help! I love my M1530... anyway, sorry about that fingerprint thing, I hope maybe you can get it to work... I haven't tried it, I don't like the fingerprint reader.

---

### Post by titimoi on 2008-11-02
Same problem with the microphone... anything wrong about that for you to ?

---

### Post by Milesio on 2008-11-02
I had that same problem with the microphone on my XPS 1530 using 8.04, and I fixed it with this:

>    1. Double-click the volume control icon in the top right of the screen.
   2. Select Edit / Preferences.
   3. Add "Digital" and "Digital Input Source" to the list of visible tracks.
   4. On the Options tab, select "Digital Mic 1" for "Digital Input Source".
   5. On the Recording tab, set the volume for the microphone.

retrieved at:
[http://ubuntuforums.org/showthread.php?t=702642&highlight=hardy+howto&page=3](http://ubuntuforums.org/showthread.php?t=702642&highlight=hardy+howto&page=3)

I'm upgrading to 8.10 tomorrow, so I'm hoping this still works :P :D

---

### Post by titimoi on 2008-11-02
> **Milesio said:**
> I had that same problem with the microphone on my XPS 1530 using 8.04, and I fixed it with this:



retrieved at:
[http://ubuntuforums.org/showthread.php?t=702642&highlight=hardy+howto&page=3](http://ubuntuforums.org/showthread.php?t=702642&highlight=hardy+howto&page=3)

I'm upgrading to 8.10 tomorrow, so I'm hoping this still works :P :D

I did it too for 8.04 but it doesn't work anymore for 8.10 unfortunatly... when I untick the mute icon, close the window and open it again, the mute icon has automaticly been ticked...

---

### Post by Milesio on 2008-11-03
Damn... In that case the "upgrade" will have to wait :P 
I'm using Skype these days and I need the computer's microphone.

I was reading around and the problem with the microphone is not limited to the Dell 1530. It happens with other laptops too.

---

### Post by titimoi on 2008-11-03
> **Milesio said:**
> Damn... In that case the "upgrade" will have to wait :P 
I'm using Skype these days and I need the computer's microphone.

I was reading around and the problem with the microphone is not limited to the Dell 1530. It happens with other laptops too.

I know, i've to switch on windows to call now, and it's pretty borring... the intel ICH8 isn't fully supported...

---

### Post by Clockswork on 2008-11-03
How do you get the Nvidia drivers to work after updating to 8.10? Envy doesnt work for some reason and when I activate the restricted drivers and restarts my computer goes into safe mode and I'm forced to deactivate the drivers. 

Any luck for you guys?

(8600m Go card)

---

### Post by titimoi on 2008-11-03
Did you accept to change your menu.lst during the upgrade ?

I had this problem so I went to /boot/grub/menu.lst and I changed the line 
> "/boot/vmlinuz-2.6.24-19-generic root=UUID=f7f8b41c-cd8f-41ab-941f-36abb50aaecb ro single"

replacing by the right kernel (if you style have 2.6.24.. and not 2.6.27.. it means that your menu.lst isn't up to date.)

just go to /boot/ and look at what you have looking like "initrd.img-2.6.27-7-generic" 

then replace in menu.lst the old kernel by the new one (2.6.24-X by 2.6.27-X.. or whatever you have newer in your boot folder)

Don't forget to backup your menu.lst before 

> cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

And please ignore my solution if you have a kernel 2.6.27-X already in your menu.lst

hope to be as clear as possible.

before you had something like :

> [B]title		_Ubuntu 8.04, kernel 2.6.24-16-generic_
root		(hd0,4)
kernel		_/boot/vmlinuz-2.6.24-16-generic_ root=UUID=f7f8b41c-cd8f-41ab-941f-36abb50aaecb ro quiet splash
initrd		_/boot/initrd.img-2.6.24-16-generic_[/B]

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f7f8b41c-cd8f-41ab-941f-36abb50aaecb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f7f8b41c-cd8f-41ab-941f-36abb50aaecb ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic



and after (you can change the title etc..) you should have :

> [B]title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f7f8b41c-cd8f-41ab-941f-36abb50aaecb ro quiet splash i8042.nomux=1
initrd		/boot/initrd.img-2.6.27-7-generic[/B]

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f7f8b41c-cd8f-41ab-941f-36abb50aaecb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f7f8b41c-cd8f-41ab-941f-36abb50aaecb ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic



Good luck

---

### Post by timoman on 2008-11-03
Hey everyone,

I've been messing around with Ubuntu on my XPS forever now... so many hours put in for the smallest things.

Now everything's working great except... I just have one problem left:
a lot of people have been having trouble with their touchpads, and so have I. I've finally gotten it to work well.. but only after the computer resumes from sleep! Does anyone know what could be causing this and how I can fix it?

I'm a complete wannabe and I don't really know much about linux, by the way.

Thanks!

---

### Post by mrojas73 on 2008-11-03
> **Jorell00 said:**
> Upgrading Bios to A09 , solved my touchpad issues

Didn't fix mine.

---

### Post by titimoi on 2008-11-04
> **timoman said:**
> Hey everyone,

I've been messing around with Ubuntu on my XPS forever now... so many hours put in for the smallest things.

Now everything's working great except... I just have one problem left:
a lot of people have been having trouble with their touchpads, and so have I. I've finally gotten it to work well.. but only after the computer resumes from sleep! Does anyone know what could be causing this and how I can fix it?

I'm a complete wannabe and I don't really know much about linux, by the way.

Thanks!

your micr is working fine ??
everything has been said for the touchpad, this nomuw at the end of the line in your menu.lst and the hal modification (check the wiki)

---

### Post by timoman on 2008-11-04
Yeah, I did the nomux and hal modifications (though really I have no idea what those mean)... and now the touchpad works, but only after the computer goes to sleep first, then wakes up.

Yeah, my microphone works... I think what I did was install alsa-oss and alsa-mixer, and i cranked up the volume on basically everything. Then I switched the input from analog to digital (or maybe it was the other way around).

Afterwards, I had some more sound issues, so I wired everything through pulseaudio, but again, I jumbled stuff around so I have no idea what I actually did. Try alsa, and if that doesn't work, I'll try to figure out what I did for you

---

### Post by titimoi on 2008-11-04
ok thank's for the explanation, I'll see what I can find.

For your touchpad it is really wierd, I never saw something like that...  did you change anything in xorg.conf ?

---

### Post by Coort on 2008-11-04
Ok...i have some weird things on my 1530.
On Hardy all was fine, then i've upgraded to intrepid and touchpad gone wild.

First time intrepid kernel was "beeping", no sign of GDM, forced a shutdown and rebooted in recovery mode without problem, eliminated the kernel option "i8042etcetc...", checked that my lines regarding touchpad in xorg.conf were commented.

After, intrepid kernel boots up, but if you hit the touchpad you're ****** and have to reboot.

Then i've upgraded to bios from A08 to A09. No change, if you hit the touchpad you're ******.

I've added the .fdi file for the touchpad, and then something changed, touchpad it's something "wild" to be gentle, but at least if you're lucky you don't have to reboot every time.

At last i've added (again) the kernel option "i8042etcetc", intrepid kernel does not like it, beeps for ~20 seconds and then give me a blank (black) screen instead of GDM (no splash during boot), i'll hit CTRL+ALT+BCKSP and then...tadaa...GDM, in all it's glory. And touchpad works fine...

Someone has hints?
Thanks in advance

---

### Post by timoman on 2008-11-04
> **titimoi said:**
> ok thank's for the explanation, I'll see what I can find.

For your touchpad it is really wierd, I never saw something like that...  did you change anything in xorg.conf ?

Let me know if you get the mic working.

I did change a bunch of things in xorg.conf, but as I was going to copy and paste it in here, i noticed that most of it...disappeared?

So I added some lines and this is what I have now, but the trackpad still is in the same situation, only working (perfectly) after sleep:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option "Device" "/dev/psaux"
    Option "Protocol" "auto-dev"
    Option "LeftEdge" "120"
    Option "RightEdge" "830"
    Option "TopEdge" "120"
    Option "BottomEdge" "650"
    Option "FingerLow" "14"
    Option "FingerHigh" "15"
    Option "MaxTapTime" "180"
    Option "MaxTapMove" "110"
    Option "ClickTime" "0"
    Option "EmulateMidButtonTime" "75"
    Option "VertScrollDelta" "10"
    Option "HorizScrollDelta" "0"
    Option "MinSpeed" "0.45"
    Option "MaxSpeed" "0.75"
    Option "AccelFactor" "0.020"
    Option "EdgeMotionMinSpeed" "200"
    Option "EdgeMotionMaxSpeed" "200"
    Option "UpDownScrolling" "1"
    Option "CircularScrolling" "0"
    Option "SHMConfig" "true"
EndSection
```

To Coort: Sorry, I have no idea what's going on there. I'll try to figure something out, if I can.

---

### Post by scotthammy on 2008-11-05
As much as I want to use ubuntu as a desktop replacement, my XPS m1530 Still has basic issues. like mouse and video and sound card drivers, all that with alot of time and reader and editing config and text files, can get 70% working after making changes.

they almost need a system at install you tell the installer what pc you have and if there is any settings needed they are done for you.

I love ubuntu and the thought of use, but its always a let down when things dont work..

Maybe in the next version...

---

### Post by titimoi on 2008-11-05
.. I just havean issue on my microphone and I have the same XPS M1530 as you.. the nvidia drivers are all right, such as the touchpad.. and the mic driver problem is going to be solved shortly because this bug has been reported in many ways and is qulified as a priority it affects all the intel ICH8.. which is quite a lot of notebooks).. that's the way we like ubuntu.. and don't forget that it's free, better looking and way more sure as cro$oft..

---

### Post by timoman on 2008-11-05
> **scotthammy said:**
> As much as I want to use ubuntu as a desktop replacement, my XPS m1530 Still has basic issues. like mouse and video and sound card drivers, all that with alot of time and reader and editing config and text files, can get 70% working after making changes.

they almost need a system at install you tell the installer what pc you have and if there is any settings needed they are done for you.

I love ubuntu and the thought of use, but its always a let down when things dont work..

Maybe in the next version...

Man, that sucks. Ubuntu is such a good operating system and it's a shame that it's the little things that keep people from using it.

I put in so many hours struggling with mostly sound and video but a whole lot of other things...and finally got most of it working... so if you need any help from a complete newbie, feel free to ask me!

---

### Post by Coort on 2008-11-06
A little update on my problem: actually the kernel "beep" problem is tied with the splash screen in some manner.
I don't know why, but when my PC beep it does not show the normal ubuntu splash screen.

---

### Post by minhaaj on 2008-11-08
> **jheylin said:**
> I just put 8.10 on my Dell XPS 1530 and the mic doesn't work either. In the volume control it automatically keeps muting the microphone and un-muting it doesn't work since it automatically mutes it again. Any help?

exactly my problem on Dell Insprion 6400. Mic won't unmute. any help ?

---

### Post by minhaaj on 2008-11-08
> **Milesio said:**
> Damn... In that case the "upgrade" will have to wait :P 
I'm using Skype these days and I need the computer's microphone.

I was reading around and the problem with the microphone is not limited to the Dell 1530. It happens with other laptops too.

try i got dell inspiron 6400 same problem. although in configured skype to work i can't use online browser-based web conferencing tools like wiziq.com. mic is muted automatically.

---

### Post by timoman on 2008-11-08
I followed the instructions on this page:
[Edit]: apparently this link doesn't work and craps up your driver

but they didn't work for me. I'd give them a shot though, they worked for some people.

Then: I installed linux-backports-modules-2.6.24-16-386 through synaptics, which I believed got everything working.

I don't know if it was a combination of the two that got the microphone working or just one or the other, but I'd give both a shot.

---

### Post by titimoi on 2008-11-08
I'm gonna try that

thanks

---

### Post by timoman on 2008-11-08
Sorry about that, I was talking about the microphone there.

Still haven't gotten the microphone to work right after boot

---

### Post by titimoi on 2008-11-08
crape I followed that tutorial and now I don't have any sound anymore !!

---

### Post by titimoi on 2008-11-08
edit

---

### Post by timoman on 2008-11-09
I'm so sorry!

It didn't work for me, but didn't completely screw up my sound!
Now I feel really bad...

---

### Post by titimoi on 2008-11-09
I had to find new drivers and recompile it manualy to have my sound back, but I still have some wierd noise sometimes that I didn't have before.. it was written before, "use it for 7.10 with a kernel 2.6.24" I was stupid to follow that HowTo as I know that for the moment our Problem is so huge (so many peaple have it) that it will be resolved shortly for sure.. and by people who know what they do (not me !) with a new HowTo just for Intrepid.

---

### Post by Clockswork on 2008-11-09
I've got an issue with my webcam after upgrading to 8.10. When I star Cheese or Skype and try my webcam its just a white frame.. Anyone here with the same issue? Thanks

---

### Post by Clockswork on 2008-11-09
Btw, sence we have this thread, could everyone post their idle Temps of their CPU, GPU and HDD. And also when the fan kicks in... (Celcius)

CPU~43  GPU~62  HDD~40  Fan kicks in when GPU reaches 65

---

### Post by titimoi on 2008-11-09
cpu: 43 in Idle ??? 

I have CPU-55 HDD-42 GPU-63

No idea when the fan kicks.. but approxymatly the same as you.. or maybe when my CPU reaches 60...

---

### Post by Gausian on 2008-11-09
Cpu=50
hdd=38
gpu=59

---

### Post by aikiwolfie on 2008-11-09
> **accesshater said:**
> Does somebody know if the hd issue is fixed in 8.10 (load cycle problem).

Have you tried using powertop?

```
sudo apt-get install powertop
```

start powertop with

```
sudo powertop
```

It'll scan your system and fix lots of problems or at least prompt you to allow it to make a fix.

---

### Post by Clockswork on 2008-11-09
> **aikiwolfie said:**
> Have you tried using powertop?

```
sudo apt-get install powertop
```

start powertop with

```
sudo powertop
```

It'll scan your system and fix lots of problems or at least prompt you to allow it to make a fix.


Oooh, thanks will try that. The HDD Laod Cycle issue is still there but you can fix it with the command

```
sudo hdparm -B 254 /dev/sda
```

---

### Post by Clockswork on 2008-11-09
> **titimoi said:**
> cpu: 43 in Idle ??? 

I have CPU-55 HDD-42 GPU-63

No idea when the fan kicks.. but approxymatly the same as you.. or maybe when my CPU reaches 60...

My CPU can reach those values to, thinking about undervolting it abit..

---

### Post by Clockswork on 2008-11-09
By the way, if you want to lower the threshold for when your fan kicks in I suggest to update your BIOS to A09 (if you havent already). I wrote a guide on how to do this in Ubuntu: [Click to go to the guide!]("http://www.clockswork.org/?p=3")

---

### Post by Clockswork on 2008-11-09
> **Clockswork said:**
> Oooh, thanks will try that. The HDD Laod Cycle issue is still there but you can fix it with the command

```
sudo hdparm -B 254 /dev/sda
```


Tried it and it didnt prompt me about the HDD just the USB and Bluetooth..

---

### Post by timoman on 2008-11-10
> **Clockswork said:**
> I've got an issue with my webcam after upgrading to 8.10. When I star Cheese or Skype and try my webcam its just a white frame.. Anyone here with the same issue? Thanks

I didn't notice it until you brought it up, but yeah, I have the same issue too.

Well, for me, the webcam image doesn't even seem to be a white frame...it's just..not there.

The blue camera light is on though.

Also, update for my touchpad situation: i finally got it to work, cause I'm a dummy. I edited the menu.lst in /boot/grub/, but I use EasyBCD to dual boot, and I didn't update that menu.lst configuration, so it was like I didn't do anything at all.](*,)

---

### Post by Clockswork on 2008-11-10
> **timoman said:**
> I didn't notice it until you brought it up, but yeah, I have the same issue too.

Well, for me, the webcam image doesn't even seem to be a white frame...it's just..not there.

The blue camera light is on though.

Also, update for my touchpad situation: i finally got it to work, cause I'm a dummy. I edited the menu.lst in /boot/grub/, but I use EasyBCD to dual boot, and I didn't update that menu.lst configuration, so it was like I didn't do anything at all.](*,)

The webcam in 8.10 works in Skype but not in Cheese :/ Weird but true

---

### Post by rockorequin on 2008-11-12
Re the webcam issues, check out [https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506). There's a script there to compile and install the latest uvcvideo driver from svn and this fixed the webcam problems for me:

sudo apt-get install subversion build-essentials
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make

sudo install uvcvideo.ko -v -m644 /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko

sudo make install

sudo cp -av /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko /lib/modules

sudo depmod -ae $(uname -r)

I didn't even need to reboot (although I did do a sudo rmmod uvcvideo and sudo modprobe uvcvideo to be sure) and now cheese works at the 1600x1200 resolution, which is much improved compared to Hardy (where I think it was set permanently at 320x240).



I still can't get the microphone to work properly, though. It does record if I enable 'Digital Input Source' in Preferences and set the microphone to digital instead of analog, but it's set to the lowest sensitivity level. In Hardy I just needed to include 'Digital' in the preferences and then I got a digital sensitivity control in the alsamixer recording tab which let me turn up the recording level. But in Intrepid, 'Digital' doesn't appear as an option at all. I can include 'Capture', and muting this stops the microphone working, but when unmuted the 'Capture' level control has no effect on sensitivity.


One other thing I've noticed is that frames per second are significantly lower in Intrepid 3D games compared to Hardy, at least compared to the 64-bit Hardy. For instance, Call of Duty 4 running under wine gets half the framerate in Intrepid compared to my 64-bit Hardy installation on the same laptop, even using the same 173.14.12 driver. I recorded more details at [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/294925](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/294925) .

---

### Post by titimoi on 2008-11-13
still havn't found anyhing about the microphone and its auto-re-mute problem ?

---

### Post by zdux0012 on 2008-11-18
What about the dell media button?
Any rework of that to dual boot?

---

### Post by Twizz on 2008-11-18
I have not been able to set my resolution to 1280X800.  The native resolution on my M1530 is 1440X900.  I was able to set up 1280X800 on 8.04, but for some reason it wont show up on 8.10.  I installed the Nvidia driver for my 8600 manually and with EnvyNG, but no luck.  Anybody know how to fix this?  Until I can get it working I will just have to go back to 8.04.

---

### Post by Milesio on 2008-11-18
> **Twizz said:**
> The native resolution on my M1530 is 1440X900.  I was able to set up 1280X800 on 8.04

Interesting, 'cos on mine 8.04 automatically detected 1440x900. I used EnvyNG too.

Anyhoo, I see there still are some little annoying problems with 8.10 on the XPS 1530. I guess I won't be upgrading until it all works at 100%. 
Right now 8.04 works like a little wonder for me. I spent too much time setting it up to my liking; I don't want to go back to lose my sleep over possible resolution problems, or microphones not working or whatever.

---

### Post by Twizz on 2008-11-18
The good thing is that 8.04 works very well on the 1530.  I'm not sure, but maybe the new resolution problem has something to do with Gnome?  I tried the new RC1 of Mint and had the same resolution problem.  I'll try Kubuntu to see if it works.

---

### Post by Milesio on 2009-01-02
So... are all the known issues solved now with the updates?
Is it 100% save (ok, ok 99% ;)) to upgrade to 8.10 on a 1530 now?

---

### Post by rockorequin on 2009-01-02
I've been using 8.10 for some time now and it's pretty good so long as you use the 2.6.27-11 kernel from the proposed repositories. Older versions of the kernel don't work properly with the webcam, cause lock ups due to the wireless card, and give write errors when writing to the built-in SD reader.

There are still some regressions that need fixing though:

- You need to edit some files to get the microphone working properly (ie to get an ALSA/pulse software boost control because the hardware one either doesn't appear or doesn't work if it does). This workaround is the one detailed in [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998).

- "fdisk -l" doesn't recognise the mmcblk device (the built-in SD card reader any more) so you can't format it using gparted. The workaround is to use parted and specify the partition manually.

- For me at least, compiz sometimes halves the framerate on games like CoD4 under wine, although of course it shouldn't. Switching it off and then back on again usually seems to fix it.

-  The nvidia driver can sometimes cause screen small corruptions because it doesn't update everything it should. The workaround is to turn off loose bindings. I also found that installing the 180.18 beta driver has completely fixed this for me (and the driver seems very stable). The only downside is that you need to reinstall the driver whenever you upgrade the kernel.

- The local mouse pointer in vinagre disappears when you move it out of the vinagre window and back. This is really annoying because you are just left with a laggy remote mouse pointer and hence keep missing menus etc.


Intrepid still has a couple of issues that Hardy also had for me:

- On some (rare) websites with AJAX fade in/out effects, the 173 and 177 nvidia drivers freeze X for 2-3 seconds at a time while the page is being rendered. The 180.18 driver fixes this.

- If you're running compiz, there's a 10 second delay while X starts up due to a Window Manager timeout. You can fix it by removing Window Manager from Sys/Prefs/Sessions and adding compiz or an application like fusion-icon manually. Afterwards X starts in just a few seconds.

- Firefox still has the right mouse click problem. Installing the mouse gestures plugin fixes it, though.


On a positive note, I found I don't need the "hdparm -B 254 /dev/sda" fix for frequent disk park/unparks cycles any more in 8.10, although I did in 8.04. And the new features in Intrepid like tabbed browsing are very nice.

---

### Post by spongypants23 on 2009-01-04
The only complaint I have for Intrepid on my M1530 is the wireless card (Intel 4965) causing kernel panics. Supposedly linux-backports-modules-intrepid fixes this, however I was still experiencing very frequent connection stalls. (I've since downgraded to Hardy).

Is this a problem that has now been fixed? I've been reading around on these forums and Launchpad, but I can't find a clear answer as to the status of this issue...

---

### Post by rockorequin on 2009-01-04
> **spongypants23 said:**
> The only complaint I have for Intrepid on my M1530 is the wireless card (Intel 4965) causing kernel panics. Supposedly linux-backports-modules-intrepid fixes this, however I was still experiencing very frequent connection stalls. (I've since downgraded to Hardy).

Is this a problem that has now been fixed? I've been reading around on these forums and Launchpad, but I can't find a clear answer as to the status of this issue...

Yes, it's definitely fixed in kernels 2.6.27-11 which is only in the proposed repositories. I think it's NOT fixed in the backports, though, so you need to uninstall them.

There was some confusion because it was fixed originally in backports, then I think it was removed from backports and put into kernel 2.6.27-8 in the proposed repository. People who still had backports lost the fix even after upgrading the kernel. It got worse: kernel -9 them appeared in the main repository *without* the fix. -10 appeared at the same time as -9 *with* the fix, but only in the proposed repository. People who upgraded from -8 to -9 therefore lost the fix.

If you want to read more about it, see [https://bugs.launchpad.net/bugs/276990](https://bugs.launchpad.net/bugs/276990). But the short answer is to install 2.6.27-11 from the proposed repository (and uninstall backports for good measure).

---

### Post by spongypants23 on 2009-01-05
> **rockorequin said:**
> Yes, it's definitely fixed in kernels 2.6.27-11 which is only in the proposed repositories. I think it's NOT fixed in the backports, though, so you need to uninstall them.

There was some confusion because it was fixed originally in backports, then I think it was removed from backports and put into kernel 2.6.27-8 in the proposed repository. People who still had backports lost the fix even after upgrading the kernel. It got worse: kernel -9 them appeared in the main repository *without* the fix. -10 appeared at the same time as -9 *with* the fix, but only in the proposed repository. People who upgraded from -8 to -9 therefore lost the fix.

If you want to read more about it, see [https://bugs.launchpad.net/bugs/276990](https://bugs.launchpad.net/bugs/276990). But the short answer is to install 2.6.27-11 from the proposed repository (and uninstall backports for good measure).

From what I read in the comments of the bug report, it seems that the fix comes and goes throughout the kernel versions. Even then, I don't know if I want the proposed updates on, since I tend to be very unlucky with alpha/beta-whatever versions of stuff.

Since I can't have the fix coming and going (I need a stable computer for schoolwork) I suppose I'll have to get a new card or just wait longer.

---

### Post by neelesh_jn on 2009-02-03
hi...can u please help me with how to install the web cam driver....or where to start the web cam....
i am new to linux...so dont really know the basic stuff too....
as a matter of fact i dont even know how or where to post the questions in here...so i am just asking u...please help....

---

### Post by iceman_ch on 2009-02-06
> **spongypants23 said:**
> From what I read in the comments of the bug report, it seems that the fix comes and goes throughout the kernel versions. Even then, I don't know if I want the proposed updates on, since I tend to be very unlucky with alpha/beta-whatever versions of stuff.

Since I can't have the fix coming and going (I need a stable computer for schoolwork) I suppose I'll have to get a new card or just wait longer.

I'm running that kernel and I still have the problem with wireless.

---

### Post by spongypants23 on 2009-02-06
> **iceman_ch said:**
> I'm running that kernel and I still have the problem with wireless.

Ditto. Upgraded again to Intrepid in hopes of the problem being fixed. I have a USB WLAN device in the mail that I'm going to use until the problem is fixed, hopefully in Jaunty.

---

### Post by not a pipe on 2009-02-09
> **Clockswork said:**
> My CPU can reach those values to, thinking about undervolting it abit..
Why?
Core2s should be fine up to 100C, so I don't think even something around 70C is that bad.

---

### Post by neelesh_jn on 2009-02-10
hi...
i have a dell xps 1530...
can you please help me with the finger-print reader and wifi driver...(as they are not working in my system).

---

