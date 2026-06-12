---
title: "Dell XPS 14 Ultrabook Compatbility"
date: 2013-02-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pablo180 on 2013-02-16
Before purchasing a Dell XPS 14 Ultrabook in the UK I searched these forums and the internet for confirmation that it would work with Ubuntu (seeing as that is my primary prerequisite) and for any possible problems, however although I found some people with this laptop state that they were running Ubuntu, I was unable to find anything definitive about how well it would run. It isn’t mentioned on the certified hardware website, although similar Dell laptops are. 

So after taking a chance and buying one, I thought that I would post my experience of it so that anyone else looking to purchase this laptop would have a clear idea of what works and what does not. Although in a nutshell, everything works and arguably better than it does in Windows 8, with just a slight installation workaround and an easily solvable problem with the Nvidia card being the only negatives. 

Tested on Ubuntu 12.10 64bit

**What Works:**
Graphics - Ivy Bridge
WiFi - Both 2.4GHz and 5GHz
Keyboard - Including all of the Function keys (sound, brightness, keyboard backlight etc)
Trackpad - It is a little sensitive and will need turning down. (I installed Synaptiks which works great and gives many more gestures and options, but is quite buggy).
SD Card Reader - Works Fine. 
Sleep/Suspend - Used this function numerous times without incident
Hibernate - As above
Sleep/Hibernate hybrid mode - I now use this most of the time, again without incident. 
Hard Drives - Both SSD and HD (eventually)
Sound - Both speakers and headphones. 

**What Doesn’t Work**
Hard Drives - These weren’t picked up initially by the Ubuntu installer but there is a simple workaround.
Graphics - The Nvidia Graphics card wasn’t detected by the installer either but again there is a simple workaround (bumblebee). 
Battery -  Initially I only got 2-3 hours battery, compared to 5-6 on Windows. (see below). 
Headphone Socket - This is meant to be a dual use (Headphone/Microphone) but I could only get it to work as Headphones. I haven’t tried it in Windows. 

**Haven’t Tested**
HDMI port
Mini Display port

**Installation**
The laptop came with Windows 8 pre-installed and I couldn’t at first get the Ubuntu installer from the Live USB to detect the hard drives. 

To get the installer to see my hard drives I had to boot into the Live USB and then enter this command at the terminal:

```
dmraid -E -r /dev/sda
```

Replacing sda with your actual device, this solved it. However the Ubuntu installer still wouldn’t recognise my Windows 8 installation at all. 

The next thing that I did was to boot into Windows 8 and the shrink the Windows partition to allow me to create a new partition that I could install Ubuntu onto. Then I formatted the new partition in FAT and then booted the Ubuntu Live USB and tried to install. Again it didn’t recognise my Windows 8 installation, but it did recognise the partition that I had created so I just installed Ubuntu onto the drive that I had formatted previously for that purpose. 

Everything went well and I could now dual boot. The battery problem was caused by the Nvidia card being switched on all of the time, so I installed Bumblebee which then turned the card off giving 5-6+ of battery life and reducing the fan noise to being almost silent.

---

### Post by moAal on 2013-02-18
Hi,

which rate you get by use of powertop? My rate is ~ 22 watts. I guess it's  pretty high for normal usage!?

I installed bumblebee too.


Thanks a lot

---

### Post by pablo180 on 2013-02-18
> **moAal said:**
> Hi,

which rate you get by use of powertop? My rate is ~ 22 watts. I guess it's  pretty high for normal usage!?

I installed bumblebee too.


Thanks a lot


That does seem pretty high. I was using 24-28 watts on average when I first installed Ubuntu just in normal usage.  

After installing bumbleebee I now use an average of 11-15 watts. Obviously it depends on what I am doing but just for general surfing, email, word processing etc that is what I get on average with the screen on the second lowest setting. The big drop in power usage was really the only way that I could tell that the Nvidia card was off. It sounds like your card may still be on. Which version of bumblebee are you using? As far as I know, only version 3+ can turn off the card. 

The instructions I followed for installing bumblebee and setting everything up came from here: 

[Nvidia Optimus and Bumblebee]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work")

The instructions I followed were from the top answer. 

Prior to following that, I hadn’t installed any Nvidia drivers and nor had any been installed during installation so I didn’t need to uninstall the Nvidia drivers as directed there. I basically just added the X-Swat PPA and the Bumblebee PPA and then run apt-get update and installed bumblebee, bumblebee-nvidia and linux-headers-generic and then rebooted. 

As soon as I logged in I noticed the difference in power usage.

---

### Post by obiwan on 2013-03-05
What about the average temperature after installing bumblebee? I've noticed the laptop is a little warmer on Linux than on Windows... 60°C aprox (140 °F).

---

### Post by pablo180 on 2013-03-05
> **obiwan said:**
> What about the average temperature after installing bumblebee? I've noticed the laptop is a little warmer on Linux than on Windows... 60°C aprox (140 °F).

Average CPU temp is about 50-60°C after installing Bumblebee. Not sure what it was before installing Bumblee as I hadn't figured out then how to get conky to display the CPU temp, but I do know the fans were on a lot more. Now the fan very seldom kicks in, it is virtually silent most of the time. 

Not too sure about the temp in Windows, as I don't use it very much at all, but the few times that I have looked it is about the same - 50-60°C.

---

### Post by obiwan on 2013-03-05
Just noticed that while charging the temp hits 62°, but on battery it has the same temps you reprot, 50-60°C. Must be normal then :)

---

### Post by jaysscholar on 2013-04-13
Thanks Pablo. This info was extremely helpful. Strongly considering the XPS 14 now that I know it works fairly well. One bumblebee install I can handle.

---

### Post by fredrik-fyksen on 2013-04-16
How does the trackpad work on this computer? Is it the same one as in XPS 13? Then we can use the sputnik PPA to get a good driver. I'm thinking of buying a XPS 14.

---

### Post by jaysscholar on 2013-04-24
I went ahead and bought the XPS 14 and have 13.04 beta running as of yesterday. Everything is looking good so far. 

My install went smoother since I didn't have to do the dmraid process that pablo outlined. I'm not planning on dual-booting to Windoze so I just set up my partitions during the Ubuntu install process in a simple manner. My XPS came with a hdd/ssd combo with 500gb hdd and 32gb ssd.
/dev/sda1 -> 500GB hdd -> /hdd
/dev/sdb1 -> 24GB ssd -> /
/dev/sdb2 -> 8GB ssd -> swap space

I had to do a little playing with gparted and fstab to get /hdd mounted the way I wanted, but that was it. I then went ahead and installed bumblebee as suggested and saw my wattage go down pretty much identical to what pablo saw. 

> **fredrik-fyksen said:**
> How does the trackpad work on this computer? Is it the same one as in XPS 13? Then we can use the sputnik PPA to get a good driver. I'm thinking of buying a XPS 14.

My trackpad has been pretty sensitive. Part of it is I'm a mouse baby and am not particularly good at trackpads (always seem to have two-fingers on there at the same time), part of it seems to be its sensitivity. After re-reading pablo's posts, I'll look into synaptiks to help it. I'm not sure if it's the same trackpad as the 13 however. 

I haven't tested the HDMI yet. But so far so good. This SSD is pretty sweet. Thanks again pablo for posting your initial findings.

---

### Post by ub16 on 2013-04-24
> **jaysscholar said:**
> I went ahead and bought the XPS 14 and have 13.04 beta running as of yesterday. Everything is looking good so far. 

My install went smoother since I didn't have to do the dmraid process that pablo outlined. I'm not planning on dual-booting to Windoze so I just set up my partitions during the Ubuntu install process in a simple manner. My XPS came with a hdd/ssd combo with 500gb hdd and 32gb ssd.
/dev/sda1 -> 500GB hdd -> /hdd
/dev/sdb1 -> 24GB ssd -> /
/dev/sdb2 -> 8GB ssd -> swap space

I had to do a little playing with gparted and fstab to get /hdd mounted the way I wanted, but that was it. I then went ahead and installed bumblebee as suggested and saw my wattage go down pretty much identical to what pablo saw. 



My trackpad has been pretty sensitive. Part of it is I'm a mouse baby and am not particularly good at trackpads (always seem to have two-fingers on there at the same time), part of it seems to be its sensitivity. After re-reading pablo's posts, I'll look into synaptiks to help it. I'm not sure if it's the same trackpad as the 13 however. 

I haven't tested the HDMI yet. But so far so good. This SSD is pretty sweet. Thanks again pablo for posting your initial findings.

I have a 128GB SSD and 32GB mSATA, I did similar partition like you but when I reboot after installation it boots back to windows recovery thing. What changes did you do to bios or during installation that lets you boot into ubuntu. Ubuntu 13.04 beta

Update: It worked.

---

### Post by jaysscholar on 2013-04-25
ub16, I got rid of WIndoze completley. The partition that had windoze I reformated.

Also, I hooked up my [Asus 1080p VH242H]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824236052") via HDMI and dual screen worked just fine. So the HDMI port is working.

---

### Post by chrislevita on 2013-06-12
> **pablo180 said:**
> That does seem pretty high. I was using 24-28 watts on average when I first installed Ubuntu just in normal usage. 

After installing bumbleebee I now use an average of 11-15 watts. Obviously it depends on what I am doing but just for general surfing, email, word processing etc that is what I get on average with the screen on the second lowest setting. The big drop in power usage was really the only way that I could tell that the Nvidia card was off. It sounds like your card may still be on. Which version of bumblebee are you using? As far as I know, only version 3+ can turn off the card. 

The instructions I followed for installing bumblebee and setting everything up came from here: 

[Nvidia Optimus and Bumblebee]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work")

The instructions I followed were from the top answer. 

Prior to following that, I hadn&#8217;t installed any Nvidia drivers and nor had any been installed during installation so I didn&#8217;t need to uninstall the Nvidia drivers as directed there. I basically just added the X-Swat PPA and the Bumblebee PPA and then run apt-get update and installed bumblebee, bumblebee-nvidia and linux-headers-generic and then rebooted. 

As soon as I logged in I noticed the difference in power usage.

Hello friend, I followed the step like you and everything was fine, but how did notice the difference? Do you have some software that can show you this?

---

### Post by pdbeard on 2013-06-17
There are a handful of programs that can monitor power usage. 
here's a list of a few

[http://askubuntu.com/questions/73904/how-do-i-monitor-power-consumption](http://askubuntu.com/questions/73904/how-do-i-monitor-power-consumption)

---

### Post by sandro2 on 2013-08-09
Thanks Pablo180! Bumblebee got my watts down also to ~13 :-). I do not get the super long battery lifetime though, but that might only be due to the fact that I have a lot of stuff running...

I also tested HDMI (connected my laptop to a Desktop Monitor), had a double desktop (the big monitor desktop beeing to the right of the laptop one) and all worked without problems.

---

### Post by pablo180 on 2013-08-21
> **chrislevita said:**
> Hello friend, I followed the step like you and everything was fine, but how did notice the difference? Do you have some software that can show you this?

I use Conky to monitor the power usage, it shows power usage and lots of other info on my desktop so I can pretty much monitor it all the time. Conky is a great app that uses minimal resources and is in the repositories but it can be a pain to configure, [probably the easiest way is to use a manager as mentioned here]("http://www.webupd8.org/2013/07/conky-manager-gui-for-managing-conky.html"). 

> **sandro2 said:**
> Thanks Pablo180! Bumblebee got my watts down also to ~13 :-). I do not get the super long battery lifetime though, but that might only be due to the fact that I have a lot of stuff running...

I also tested HDMI (connected my laptop to a Desktop Monitor), had a double desktop (the big monitor desktop beeing to the right of the laptop one) and all worked without problems.

No problem, glad it was of help. I installed a program called TLP that improved battery life even further, regularly getting down to about 9Wh. [The same website as above has instructions here that explain how to install]("http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html"), once installed it just runs every boot in the background so you don't need to do anything else after installing. That should help you get longer battery life, I gained an extra hour having about 7 hours battery life. 

I also tested the HDMI and the Mini Display Port (via an adaptor) and the same as you multiple monitors worked without any problems, they're also detected at boot if plugged in and lid closed, again without problems.

---

### Post by pablo180 on 2013-08-21
> **jaysscholar said:**
> Thanks again pablo for posting your initial findings.

No problem, I couldn't believe how well it ran Ubuntu, certainly better on this than any other computer I've had, including a N series Dell (with Ubuntu pre-installed) so thought that I should share that information. I just forgot to subscribe to the thread and so missed the replies!

---

### Post by sinai2 on 2013-10-13
Hi Pablo180, Hi all,

First of all, I would like to thank you for this thread.
I successfully installed Ubuntu precise pangolin, with the help of 
> dmraid -E -r /dev/sda


But now each time I turn on the Ultrabook, I obtain the menu for Intel Rapid storage technology. Here is a screen shot:

[IMG]http://img826.imageshack.us/img826/7213/d8s0.jpg[/IMG]

Is there any problem? And if not, is there a way to get rid of this menu?

Thanks,

S.

---

### Post by pablo180 on 2013-10-13
> **sinai2 said:**
> Hi Pablo180, Hi all,

First of all, I would like to thank you for this thread.
I successfully installed Ubuntu precise pangolin, with the help of 


But now each time I turn on the Ultrabook, I obtain the menu for Intel Rapid storage technology. Here is a screen shot:

[IMG]http://img826.imageshack.us/img826/7213/d8s0.jpg[/IMG]

Is there any problem? And if not, is there a way to get rid of this menu?

Thanks,

S.

No, it isn't a problem, that is normal. I remember getting the same thing and being annoyed by it too but I can't remember how I turned it off. I believe that there is a setting in the BIOS/UEFI that does this. I will have to check and get back to you as I messed around with a lot of settings in UEFI and can't remember what I did exactly.

---

### Post by pablo180 on 2013-10-13
> **sinai2 said:**
> Hi Pablo180, Hi all,

Is there any problem? And if not, is there a way to get rid of this menu?

Thanks,

S.

Sorry I'm not sure about this. I just played around with the settings in the BIOS and I couldn't get that screen to appear again and I don't remember what I did to get rid of it. I have all the Rapid Storage options enabled, so I didn't get rid of it by turning those off. Do you have the Legacy Boot enabled? I have Legacy Boot disabled and use UEFI and have Ubuntu as the first option in the boot menu in the BIOS.

Do you still get the Dell logo at boot?

---

### Post by sinai2 on 2013-10-14
Thank you very much, pablo180 !!

> **pablo180 said:**
> 
Do you still get the Dell logo at boot?

Yes, but only after that screen.

About the legacy boot and UEFI I don't know even wath is.... I am searching for the documentation...


I have also another problem, probably due to the video driver. Hope that someone could help me... 
                                                     Sometimes, the system crashes: the monitor still show the desktop  environment, but it is blocked.
Is there a way to understand at least the problem? How to do a diagnosis?

  I installed ubuntu precise, with also the Sputinik PPA and Bumblebee drivers.


Thanks

S.

---

### Post by pablo180 on 2013-10-16
> **sinai2 said:**
> 

 I installed ubuntu precise, with also the Sputinik PPA and Bumblebee drivers.


Thanks

S.

If everything works, you may be better off leaving the BIOS/UEFI alone then as messing around with that can stop Windows and Ubuntu from booting altogether. 

I am not 100% certain but I don't think that you need the Sputnik PPA for the 14 XPS Ultrabook. I thought that was just for the XPS 13 and 15? Having that PPA could mess with your video drivers. I certainly didn't enable it, but I installed Ubuntu 12.10 Quantal Quetzal and installed the [X-Swat PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates").

That PPA gives the latest, stable, video drivers for Ubuntu. You can install it by opening the Software Centre, clicking on Edit > Software Sources >Other Software (tab) and then clicking Add. Then paste in the PPA:

```
ppa:ubuntu-x-swat/x-updates
```

That should update your drivers on your next update. It may solve your crashing and hanging problem, although it will probably still hang occasionally (mine does). If it does hang a quick way of getting it back is to hit CTRL + ALT and F1, login and then type:

```
setsid unity
```

Or even just typing 'unity' should work. That will restart Unity and should bring your desktop back to being usable. Just hit CTRL + ALT and F7 to go back to your desktop.

---

### Post by sinai2 on 2013-10-19
> **pablo180 said:**
> 
  I installed Ubuntu 12.10 Quantal Quetzal and installed the [X-Swat PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates").


Thanks!

I will try to use that PPA. Can I simply add them, remove the sputnik PPA and do ```
sudo apt-get dist-upgrade
```?

I have another problem: crackling soud with integrated and external microphone. This is  not an hardware problem, as in Windows it works fine. Have you had the same problem?

Moreover, we i insert the headset, the integrated microfone turns off, as the jack is unique and it is supposed to accept both in and out audio.
Is there a way to use the integrated microphone along with the headset?

S.

---

### Post by pablo180 on 2013-10-20
> **sinai2 said:**
> Thanks!

I will try to use that PPA. Can I simply add them, remove the sputnik PPA and do ```
sudo apt-get dist-upgrade
```?

S.

I wouldn't use dist-upgrade, it may change more than you bargained for. I'm not an expert, but what I would do is install ppa-purge

```
sudo apt-get install ppa-purge
```

And then run that on the sputnik PPA e.g. 

```
sudo ppa-purge ppa:canonical-hwe-team/sputnik-kernel
```

Assuming the above is the right PPA location, you may have an older PPA. That should reverse the changes made by that PPA back to the standard ones but not make any wider changes. You should just remove the Sputnik PPA first before adding the X-Swat one, you may actually find that you don't need the X-Swat one at all, and the default graphics drivers are good enough but if you do use it, you can always reverse the changes using ppa-purge as above. 


Regarding the sound, I haven't really used the microphone much but I have noticed the crackling too, I haven't found a way to resolve this other than playing around with the settings in the Sound Menu. I installed the PulseAudio Volume Control and played with the settings there, it can be improved, very slightly but not greatly. 

```
sudo apt-get install pavucontrol
```

It may improve things for you. 

As for the audio jack, I thought it was dual use at first but I have tried plugging in a headset in both Ubuntu and Windows and I could not get it to accept audio in at all. Rechecking the Dell site, I saw that under tech specs it just lists it as:

> headset jack (1)

So I think I was wrong about it being dual use, unless anyone else has had any luck under Windows?

The integrated microphone works for me with headphones in, this may be something that can be changed with PulseAudio volume control and I may have already done that; at the very least you should be able to just switch it back on from there. I also just noticed that with headphones in, in the Sound Settings (from under the sound icon) the 'internal microphone' switches to 'microphone' when a headphones are plugged in and then back again when they are removed, but still seems to work in the same way with headphones plugged in.  

I should point out that I am using 13.10 Saucy Salamander so thing may be different there.

EDIT: I just ran a few tests in Audacity (Sound Recorder isn't working for me) and it seems to be that if you have the microphone above Unamplified in the sound settings, the crackling appears and gets worse the higher the microphone volume. I'm wondering whether Ubuntu just has the microphone up too high by default and it is picking up far too much background noise. I don't get the crackling in Skype, which controls its own settings, just when trying to record in Ubuntu.

---

### Post by sinai2 on 2013-10-20
Thanks a lot! I followed Your suggestions and I  will let ou know if I will find more errors.

Last doubts:
[QUOTE=pablo180;12817957]If everything works, you may be better off leaving the BIOS/UEFI alone then as messing around with that can stop Windows and Ubuntu from booting altogether. 

That PPA gives the latest, stable, video drivers for Ubuntu. You can install it by opening the Software Centre, clicking on Edit > Software Sources >Other Software (tab) and then clicking Add. Then paste in the PPA:

```
ppa:ubuntu-x-swat/x-updates
```

That should update your drivers on your next update. 
[QUOTE]

How can I be sure that the correct drivers are installed?
Here is wath I get:
```

me@mypc ~ $ sudo optirun firefox 
[sudo] password for me: 
[  482.011443] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[  482.011512] [ERROR]Could not connect to bumblebee daemon - is it running?

```

And
```

~ $ sudo apt-get dist-upgrade
[sudo] password for me: 
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  libdrm-nouveau2 libdrm-nouveau2:i386 libllvm3.1 libllvm3.1:i386
The following packages will be upgraded:
  libgl1-mesa-dri libgl1-mesa-dri:i386 libxatracker1
  xserver-xorg-video-nouveau
4 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.3 MB of archives.
After this operation, 77.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
n

```
Why dist-upgrade want install the nouveau-driver?!

S.


S.

---

### Post by pablo180 on 2013-10-20
> **sinai2 said:**
> 
Why dist-upgrade want install the nouveau-driver?!

S.

I'm not an expert on graphics drivers by any means, I usually either go with the default installed ones or use X-Swat so I can't tell you for definite whether they are the right ones. However the ones it is trying to install are the same drivers that I currently have installed, so chances are they are OK.

> **sinai2 said:**
> 

How can I be sure that the correct drivers are installed?
Here is wath I get:
```

me@mypc ~ $ sudo optirun firefox 
[sudo] password for me: 
[  482.011443] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[  482.011512] [ERROR]Could not connect to bumblebee daemon - is it running?

```

S.

That looks like bumblebee isn't properly installed. I would deal with the default drivers first if I were you as you need everything up and running before trying to install bumblebee and then run the install again for bumblebee step by step. I used the [instructions located here]("http://askubuntu.com/a/36936/99306"). You should be able to start straight from the section entitled - **Installation instructions for Bumblebee** and make sure you follow the instructions precisely. I am guessing you either didn't install the Nvidia drivers or the linux headers, or they have since been removed and that is what has gone wrong the first time.  

Also you don't need sudo to run optirun or Firefox, you'd basically be running Firefox as root. 

```
optirun firefox
```

Is better and safer.

---

### Post by sinai2 on 2013-10-21
Sorry, I am afraid that my pc is not equipped with the NIVIDIA card.... I read this [http://www.engadget.com/2012/06/26/dell-xps-14-review/](http://www.engadget.com/2012/06/26/dell-xps-14-review/) and
> 
 $ lspci -nn | grep 'VGA'
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)

Is it possible? Could you t How I can verify? (I have a second hand laptop and I don't have the paper with all the optionals)
I still don't know if this fixes the problem with the frozen system that still occurs.. at least I am learning lot of stuff....

---

### Post by pablo180 on 2013-10-22
> **sinai2 said:**
> Sorry, I am afraid that my pc is not equipped with the NIVIDIA card.... I read this [http://www.engadget.com/2012/06/26/dell-xps-14-review/](http://www.engadget.com/2012/06/26/dell-xps-14-review/) and

Is it possible? Could you t How I can verify? (I have a second hand laptop and I don't have the paper with all the optionals)
I still don't know if this fixes the problem with the frozen system that still occurs.. at least I am learning lot of stuff....

That is nothing to worry about, that is what you should get, I get the same thing after running that command too. Have you tried replacing VGA with NVIDIA?

```
lspci -nn | grep 'NVIDIA'
```

For which I get:

```
01:00.0 3D controller [0302]: NVIDIA Corporation GF117M [GeForce 610M/710M / GT 620M/625M/630M/720M] [10de:1140] (rev ff)
```

You should get something similar. 

If you've reverted back to the original graphics drivers and properly installed bumblebee, you can test out your card by typing:

```
optirun glxspheres
```

That should say something like: 

```
OpenGL Renderer: GeForce GT 630M/PCIe/SSE2
```

You should also hear the fans kick in after a few seconds and your battery time drop. 

Is your system still freezing up even after reverting to the default drivers?

---

### Post by sinai2 on 2013-10-22
> **pablo180 said:**
> Have you tried replacing VGA with NVIDIA?

```
lspci -nn | grep 'NVIDIA'
```


I don't get anything :(

---

### Post by pablo180 on 2013-10-22
> **sinai2 said:**
> I don't get anything :(

It's unlikely that the card has been removed and as far as I know they didn't ship them without the card. It is probably just a case of Ubuntu not detecting it, I seem to remember that when I first installed Ubuntu it didn't pick it up either. Have you installed bumblebee? That will install the Nvidia drivers and the card should then be detectable.

---

### Post by sinai2 on 2013-10-22
> **pablo180 said:**
> It's unlikely that the card has been removed and as far as I know they didn't ship them without the card. It is probably just a case of Ubuntu not detecting it, I seem to remember that when I first installed Ubuntu it didn't pick it up either. Have you installed bumblebee?
Yes, I have installed....

---

### Post by pablo180 on 2013-10-22
> **sinai2 said:**
> Yes, I have installed....

Why do you get when you type in:

```
lspci
```

Have you installed bumblebee again since you received the error you mentioned earlier?:

```
me@mypc ~ $ sudo optirun firefox 
[sudo] password for me: 
[  482.011443] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[  482.011512] [ERROR]Could not connect to bumblebee daemon - is it running?
```

---

### Post by sinai2 on 2013-10-23
> **pablo180 said:**
> Why do you get when you type in:

```
lspci
```
Have you installed bumblebee again since you received the error you mentioned earlier?



Yes, I reistalled bumblebee with sudo apt-get install --reinstall bublebee
Here is the result of lspci

```

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
03:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)

```

---

### Post by pablo180 on 2013-10-23
> **sinai2 said:**
> Yes, I reistalled bumblebee with sudo apt-get install --reinstall bublebee
Here is the result of lspci


Yes, definitely not there. I find it unlikely that the card is missing, it probably just isn't being detected, but just to make sure I would follow the steps below:

```
sudo ppa-purge ppa:bumblebee/stable
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic
```

You have to install bumblebee and bumblebee-nvidia and linux-headers-generic otherwise it won't work. I couldn't get the headers to install when I did it and had to install them manually, but it may work for you. Once done restart. If that still doesn't work, the card may either be not there, or not working. 

Incidentally, what is your battery rate? You can see this by clicking on the battery indicator then battery and then History and then switch the Graph type to rate and set a time of about 2 hours and see where the line is most often. When I was using Ubuntu without bumblebee and when the Nvidia card wasn't detected it seldom went under 25W and the fans were pretty much always on. If your rate is consistently low, maybe you don't have an Nvidia card but if it is consistently high, your card is there but just not being detected.

---

### Post by sinai2 on 2013-10-26
> **pablo180 said:**
> 
Incidentally, what is your battery rate? You can see this by clicking on the battery indicator then battery and then History and then switch the Graph type to rate and set a time of about 2 hours and see where the line is most often. When I was using Ubuntu without bumblebee and when the Nvidia card wasn After removing the Sputnick Kernel, the system has stopped to  freeze/block. That doesn't mean that It will not  happen... but I am  more confindent that the main problem is resolved.
't detected it seldom went under 25W and the fans were pretty much always on. If your rate is consistently low, maybe you don't have an Nvidia card but if it is consistently high, your card is there but just not being detected.

The line is always beyond 25W! It seems that mine is one of the few Dell XPS 14 UB without Nvidia.

The problem of the frozen monitor still occurs. It is  a crash, I can hear the the noise of the fan after few seconds, that means that the processor is running while the system is brocken...

Now let us try to solve our problem with the audio of headset... Does it make sense to  to install the lastest driver audio?

S.

---

### Post by pablo180 on 2013-10-27
> **sinai2 said:**
> The line is always beyond 25W! It seems that mine is one of the few Dell XPS 14 UB without Nvidia.

S.

If the line is always beyond 25W then I would say that your Nvidia card is present but just not being detected by Ubuntu, and therefore always on. If it wasn't there or turned off, you'd only be drawing around 10-15W on average certainly lower than 25W.  

> **sinai2 said:**
> 
Now let us try to solve our problem with the audio of headset... Does it make sense to  to install the lastest driver audio?

S.

Did you try re-enabling the microphone via the Sound Settings when the headphones are plugged in? Just click on the Sound icon in the top right and then Sound Settings and then either selecting the integrated microphone or turning it back on? 

I'm not sure about the latest drivers, you should already be using the latest drivers for your release.

> **sinai2 said:**
> 

The problem of the frozen monitor still occurs. It is  a crash, I can hear the the noise of the fan after few seconds, that means that the processor is running while the system is brocken...

S.

That is not normal. Compiz and Unity do crash, usually about once a day for me, but normally just restart it seldom freezes and locks me out. You may want to start a new thread about those crashes and get help from someone with a better knowledge of Compiz and graphics crashes.

---

### Post by sinai2 on 2013-10-29
> **pablo180 said:**
> If the line is always beyond 25W then I would say that your Nvidia card is present but just not being detected by Ubuntu, and therefore always on. If it wasn't there or turned off, you'd only be drawing around 10-15W on average certainly lower than 25W.
Sorry, my English is so bad... so the line is alwas under the 25threshold... see the picture
[IMG]http://img17.imageshack.us/img17/7424/sqg6.png[/IMG]
S.

---

### Post by sinai2 on 2013-11-08
HI again,

just to update you... I did an advancement of version from Precise LTS to Oneiric and the problem of freezed monitor has never occurred again (this doesn't necessarly means that it will not occur in the future....)

I checked the WIndows information about the Video Card. No Nvidia sofwtare installed. At this point I am quite sure that my lapto has not Nvidia card (less performance but more battery ;) ) 

The main problem now is the low quality of the input audio during the Skype calls. Still looking for a solution...

Thank you again, Pablo180!

---

### Post by gabriel.tessarolli on 2013-11-24
Hi,

I own a XPS 14 too and I want to install Ubuntu 12.04 in my  machine as the primary OS. What I want to do is pretty much the same  everyone else has been doing: install Ubuntu in the SSD disk and leave  the 500 HD to /home, removing the windows completely. But I was  wondering if after doing this setup I will be able to revert back the  machine to the factory state (with Intel RST and all that stuff  working), using the recovery disks I made.
I've been searching the  internet to better understand this, but did not find anything giving me  the straight answer! :) Hope will guys can help me.

Thank you!

---

### Post by sinai2 on 2014-03-14
> **sinai2 said:**
> HI again,

The main problem now is the low quality of the input audio during the Skype calls. Still looking for a solution...



After the update to saucy salamander and  tuning of the audio with alsamixer - put mic boost to zero!! - the problem has been fixed!!!!

S.

---

### Post by sinai2 on 2014-03-14
> **gabriel.tessarolli said:**
> Hi,

I own a XPS 14 too and I want to install Ubuntu 12.04 in my  machine as the primary OS. What I want to do is pretty much the same  everyone else has been doing: install Ubuntu in the SSD disk and leave  the 500 HD to /home, removing the windows completely. But I was  wondering if after doing this setup I will be able to revert back the  machine to the factory state (with Intel RST and all that stuff  working), using the recovery disks I made.
I've been searching the  internet to better understand this, but did not find anything giving me  the straight answer! :) Hope will guys can help me.

Thank you!

Sorry I am afraid I ca't help you. Actually I am not using the ssd at all :( Let us now if you will find a solution!

---

