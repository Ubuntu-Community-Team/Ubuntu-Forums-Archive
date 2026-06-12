---
title: "[SOLVED] GeForce 8800GT and Ubuntu..."
date: 2008-02-17
forum: Gaming &amp; Leisure
---

### Post by chazdraves on 2008-02-17
With my recent dabbling into Quake Wars, I've rather decided my old 7600GT should get the boot. It seems the 8800GT is the latest bang-for-your-buck video card, and I think it may be time to dive in. I've heard there are some issues with Ubuntu 7.1 and the 8800GT's? I already have a very-functional install, and I don't want to ruin anything nor do I want to be out 2 days of forum-searching to get it working. How much of a pain are they to get working properly? Anyone been there? Anyone survived and been really happy with the results?

Thanks for your time, everyone.
- Chaz

---

### Post by herbster on 2008-02-17
I just built a new machine about a week or so ago, with an eVGA 8800GT. You just need to grab the latest driver, 169.09 as of now, from nvidia.com. My card works perfectly, I play ET, Quake 4, D3, ETQW, watch any video-- this card laughs at even 1080p.

The card works superbly, but the driver is the key mi amigo!

---

### Post by chazdraves on 2008-02-18
And that driver is not the one that Ubuntu has by default, correct? How do you go about downloading/installing it, how long/complicated is it, and how does Quake Wars run on that puppy? :)

Thanks,
- Chaz

---

### Post by herbster on 2008-02-18
I don't use Ubuntu, but I'm assuming the latest driver is the 100.x.x, whereas the 169.x.x drivers support the 8xxx series cards.

Go to nvidia.com, click Drivers, fill in the correct fields (8800 GT, linux 32 or 64-bit, etc. that applies to you) and hit download. You'll download a .run file, save it to /home/user/ for example, then you'll need to kill the X server. I found this:

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/33102-howto-install-nvidia-3d-drivers.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/33102-howto-install-nvidia-3d-drivers.html)

Should cover it all for ya bud.

And ETQW on my box runs at 1900x1200 with everything maxxed and constant 90fps.

---

### Post by mivo on 2008-02-18
The driver that Ubuntu installs from the restricted drivers manager works perfectly fine with the 8000GT and Quake Wars -- I have the same card, use the driver, and the Ubuntu stock kernel. You should be fine, really. :) (I do have to boot with the nosplash option, though.)

---

### Post by herbster on 2008-02-18
Ah, there you go. You're all set, chazdraves.

---

### Post by chazdraves on 2008-02-18
So, when I install it for the first time, I can expect my system to boot as normal? I just have to do a bit of legwork on the driver install. That doesn't sound too off. It seems like a great card (much like the 6800GT's of yester-year). Thanks to both of you!

- Chaz

EDIT: I just placed the order! :)

---

### Post by herbster on 2008-02-18
Yep, it should be fine. Of course, you'll probably have to tinker with your xorg.conf.

Try nvidia-settings (ALT+F2, type nvidia-settings, hit ENTER). You can adjust your resolution, monitor temperature, etc. from there.

---

### Post by reed026 on 2008-02-18
do they have an 8800 in low profile yet? I've searched newegg for one, but have been reluctant to find one. I really need an upgrade from my ATI VE, and I've been looking at nvidia's recently.

---

### Post by chazdraves on 2008-02-18
To reed026: Not that I'm personally aware of. I'd be surprised to see them any smaller than they are. I doubt you'd be disappointed if you have the space, however.

On topic: Sorry for being such a worrier, but I've had a lot of rough experiences getting into Linux, so I just want to know what I can expect. What do you figure I'll have to adjust in xorg? Just resolutions/refresh rates? I'm pretty familiar with nvidia-settings, so that should go allright.

Thanks for your patience.
- Chaz

---

### Post by mivo on 2008-02-19
The 8800GT is frequently out of stock. It's actually hard to find one, I think. Price/performance ratio is very good, and probably the best deal you can currently get still.

The driver installation is easy: you just select "Restricted Drivers Managers" from the Admin menu, choose the driver, and it'll be installed for you. It's just a few clicks, no real extra effort. If you do want the latest Nvidia driver for the card, you can install it through [Envy]("http://albertomilone.com/nvidia_scripts1.html") (but as I said, I've not felt the need yet). On my system, I needed to add the nosplash option to /boot/grub/menu.lst, but there may be other workarounds for this, or it may not be needed anymore. I haven't fiddled with it since Gutsy was released last October (I prefer seeing what's going on anyway, so the absence of the pretty splash screen isn't a problem for me). :)

---

### Post by herbster on 2008-02-19
Hmm, I'm using the 169.09 driver and haven't had to add any nosplash option to GRUB. What is the problem you experience that requires that being added?

And yes, the 8800GT is the best. I'm not a hardcore gamer or anything but I do want to be able to play stuff like Crysis, Bioshock, COD4, etc. and my main interest is in playing HD video with ease, and the 8800 does all this like a piece of cake, great price ($250 CDN) and man it runs quiet and cool.

Oh, word of warning, don't get the Asus 8800GT. I am an Asus fan (P5K-E with new build) but they really drank the Kool-Aid on this one. The 8800GT has a proprietary thermal sensor, so you can't monitor your GPU temperature unless you use their crappy SmartDoctor software (which of course will require Windows). It's so incomprehensibly silly a thing to have done. I luckily have a good relationship with the store I got my stuff from so they exchanged my Asus for an eVGA, and made it a superclocked version to boot :D Now all is well. Just thought I'd mention that.

---

### Post by Sammi on 2008-02-19
Easy way to update your graphics card driver in Ubuntu: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Just be prepared to use this line in the command prompt when the kernel gets a update "sudo envy -t". It will start Envy in text mode, from where you be able to uninstall and reinstall the Nvidia driver, which you'll need to do every time you install a new kernel :popcorn:

---

### Post by chazdraves on 2008-02-19
Yeah it seems like one heck of a card. I got the eVGA as well. I didn't go for the superclocked because it wasn't even a 10% overclock and they were still getting an extra $20 for it. I figure I can get at least that out of one myself and save the cash (although I wish I didn't have to re-overclock everytime I restart my computer...).

That's interesting that ASUS went that way, though they do seem to be fans of proprietary software (even though I love their mobos).

Thanks for the link, Sammi. That doesn't look too hard to use. Bugger that you have to remove it before upgrading the kernel though. You can do the install just as well through the GUI, correct? As a former-Windows guy, GUI's are more familiar and approachable to me.

To mivo: I was wondering as well why you need the -nosplash option...?

Thanks!
- Chaz

---

### Post by mivo on 2008-02-19
If I don't use the nosplash (and remove the quiet) option, the screen goes blank and doesn't "come back": I should actually try and see if it's still required with the latest Ubuntu kernel. I didn't have the problem with Fedora, their splash screen worked with the card.

---

### Post by chazdraves on 2008-02-22
Wel.. it arrived...

HELP!

python pulse.py nvidia 
root@chaz-desktop:/usr/share/envy# python pulse.py nvidia
Envy - Version 0.9.10
Ubuntu Gutsy 64bit
Your graphic card has been detected as a GeForce 8800 GT
Your graphic card is supported by the latest driver
OK: All the packages are installed
Checking the Dependencies for the New Method
ENVY: The following packages are not installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libcupsys2-dev but it is not going to be installed
E: Broken packages
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev

This is what I see when I try to install drivers through Envy regardless of whether I do automatic or manually... I've tried installing that first package through Synaptic as well, but I get the same errors and I can't seem to work around it. 

Anyone? I really wanna get this thing working stat!

Thanks, all!
- Chaz

---

### Post by erealz on 2008-02-22
well have you try installing the drivers on a windows box or virtual session ? this will save you some headaches

---

### Post by chazdraves on 2008-02-22
Well, I'm not certain that I understand what you're saying, but I need the drivers to work in Ubuntu?

- Chaz

---

### Post by chazdraves on 2008-02-22
Another note: I just downloaded the drivers from nVidia's website. I then installed (which was a chore for me) with X shutdown and it told me everything was working perfectly. However, when I got to Ubuntu again it said the same thing it has been saying "Low Graphics Mode: Configure, Continue". I really don't get it...? There's nothing listed in the Restricted Drivers Manager, it won't even open because it says my hardware doesn't require any restricted drivers... I'm giving this problem about an hour before I reformat and do Windows.

- Chaz

---

### Post by Sammi on 2008-02-22
There's one line in the error message you got from trying to install Envy,  that caught my eyes: ```
libqt3-mt-dev: Depends: libcupsys2-dev but it is not going to be installed
```Seems like the libqt3-mt-dev package needs libcupsys2-dev to already be installed. Try installing that package. You can use this line in a terminal to do it: ```
sudo apt-get install libcupsys2-dev
```Afterwards do this line to get all the other packages that Envy needs: ```
sudo apt-get install libqt3-mt-dev kernel-wedge rpm sharutils libxxf86misc-dev libxtst-dev libxxf86vm-dev
```
...and at last try installing Envy again

---

### Post by chazdraves on 2008-02-23
Yeah, that's the line that struck me as well. I appreciate the idea, but I'm afraid that didn't happen to work either. I did finally figure out how to get the driver to install, but as soon as it did, it wiped my Quake Wars install. By that I mean, it didn't delete it, it just made it not work. No amount of re-installing seemed to help, Quake Wars just doesn't play (which is my only 3D game and only reason for the 8800)... Needless to say, I found another way to resolve the problem.

Thanks much for the help, folks!
- Chaz

---

### Post by mivo on 2008-02-23
So, all that's left is to say congrats to the excellent card, and welcome to Quake Wars! That game has been eating up a lot of my time (usually while at work -- oops!), and once you find a few servers whose regulars you enjoy playing with (and who balance out the teams), it's really a blast. :) The community forum is at [http://community.enemyterritory.com](http://community.enemyterritory.com) -- there are quite a few Linux users as well! Check the boards for some tweaks and useful hints. And: Have fun!

---

### Post by anjilslaire on 2008-02-23
Judging by the timeline of this thread, I suspect his "another way to resolve the problem." was installing Windows (he said he was only waiting an hour to fix it).

Care to share you fix with us Chaz? Are you still in Linux?

---

### Post by mivo on 2008-02-23
Well, if that's the case, there's a good [How-To]("http://ubuntuforums.org/showthread.php?t=583762") on making ETQW work on Linux! :) Especially the 64-bit version needs some extra files. Artificial Intelligence's site had a guide too, I believe.

---

### Post by chazdraves on 2008-02-23
Yeah, I had ETQW working perfectly in Ubuntu before the new card (per AI's guide), but somehow the new card and drivers ceased the game from even loading... I tried re-installing to no avail. I'm afraid anjilslaire is accurate in his guessing. I simply don't have time for the types of problems that seem to occur in Linux. My time in Linux has been often good, and I will certainly keep an eye on the latest distros to see just when they fix wireless internet and proper driver support, but right now, I really need something that works and (probably only because I'm so familiar with it) Windows has always worked for me.

Anyhow, I just want it clear that this isn't a zing to Linux, it's just simply a call that I had to made.

Regardless, ETQW is a great game and I'm having a good time on !!!!thexc!amation!!! server. Seems to be a pretty good group (though good in both ability and demeanor). It's a fun place to get my butt kicked!

- Chaz

---

### Post by mivo on 2008-02-23
Sorry it didn't work out for you. Linux and gaming is a bit of a sore point still. I moved most of gaming to handhelds, plus what's available for Linux, but if you're into the commercial offerings, Windows is still the better choice. (I also never had real issues with Windows, I just ended up feeling too limited.) I'm surprised ETQW is causing troubles, though, since I works really well for me.

The eXc!amation is one of the best US servers, from what I read (I'm in Europe myself), so you definitely found a good server to play on. :) The only problem the game has is that when teams are imbalanced, it's no fun. But on good servers the admins either shuffle or people just even out the teams voluntarily. All in all, I feel that ETQW attracts a more mature crowd (for an FPS).

Anyway, hope to see you back in the Linux gaming scene at a later time. :) I think things are improving at a relatively steady rate, and perhaps more publishers will consider Linux, too.

---

### Post by tjharvey on 2008-02-24
I'm having this same issue.  I'm running the 64-bit version of Ubuntu 7.10 on an AMD X2 6400+ and NVIDIA 8800GT video card.  I downloaded the latest drivers (169.09) and following the install everything runs great, even after logging out and back in numerous times.  But, when I reboot the machine I get the "Low Graphics Mode: Configure, Continue" message.  I checked the xorg.conf file in /etc/X11/ and it hasn't changed since installing the drivers.  There is no option to select Restricted Drivers.  Under "System Administration" and "Screens and Graphics" it indicates the Vesa driver is loaded and the "NVidia X Server Settings" app under System Tools will not run, saying that I'm not using the NVIDIA X driver.  It's as if the system is not atempting to load the NVidia driver at boot.  I'm not a strong Linux person so am lost at this point.  Any idea what to check for?

---

### Post by tjharvey on 2008-02-25
Disregard my previous post.  I discovered the issue and it's running great.

---

### Post by mivo on 2008-02-25
Glad you got it working fine! What was the trouble caused by and how did you fix it? :)

---

### Post by tjharvey on 2008-02-25
I executed the command "apt-get remove nvidia-kernel-common", reinstalled the 169.09 drivers and it worked.  I'm not certain what all that command removes but I can now reboot the machine and the drivers loads fine.

---

### Post by pahn on 2008-02-25
It seems like I'm having the same problem as tjharvey.  I tried his solution and ran *apt-get remove nvidia-kernel-common* and then reinstalled the nvidia driver (169.09) but I still get low graphics settings when I start gdm back up.  I'm following the steps most other people have mentioned(remove nvidia kernel, stop gdm, install driver, and then start gdm back up).  I checked my xorg.conf and it looks ok.  I know sometimes you have to change the Driver name from "nv" to "nvidia" under the Section "Device", but it was already set up.  Any ideas on what else could be wrong?  Are there any other packages I need to install or remove before starting the driver installation?

---

### Post by pahn on 2008-02-26
Nevermind, I used Envy and got the drivers installed.  I tried Envy before with no success, but it worked fine on my new machine.

---

### Post by handy on 2008-02-26
I'm using an AGP XFX 7950GT, which I spent time trying to install when Gutsy was first released, to no avail.  I ended up back on Sabayon where it worked with the initial install (the proprietary nVidia drivers were installed by default).

Anyway, I've just reinstalled Gutsy, & everything is fine except I still can not get the restricted drivers to work.

I have tried the restricted driver manager, & envy, but still end up with a black screen when I startx, or the vesa mode after a reboot.

I will give the latest drivers from nVidia a go tonight or tomorrow & see if I have luck.  I'll also give the command:

apt-get remove nvidia-kernel-common

with everything crossed as well... :lolflag:

---

### Post by Sammi on 2008-02-26
[SIZE=5]**Remember to remember this line if you use Envy:**[/SIZE]

```
 sudo Envy -t
```You will need it when the nvidia driver doesn't load after a kernel update, and you get stuck at the command prompt after booting. That command will start Envy in the terminal, from where you can uninstall and reinstall the Nvidia driver.

Other than that, Envy is great :D

---

### Post by handy on 2008-02-26
> **Sammi said:**
> [SIZE=1]**Remember to remember this line if you use Envy:**[/SIZE]

```
 sudo Envy -t
```You will need it when the nvidia driver doesn't load after a kernel update, and you get stuck at the command prompt after booting. That command will start Envy in the terminal, from where you can uninstall and reinstall the Nvidia driver.

Other than that, Envy is great :D

Envy is great, when it works!

When it doesn't don't forget:

[I]Boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:

**envy --uninstall-all**

then simply type:

**reboot**

and boot as usual.

On next reboot the Xserver should work fine (but you will use the open source driver) [/I]

---

### Post by handy on 2008-02-27
My evil 7950GT card is automatically recognised on my just installed Sabayon 3.4F OS (on another drive in a different drive drawer).  I then did an emerge nvidia-driver to bring it up to the latest version & the damn thing even new which card it was!!  & that card is not a common one.

I had to adjust the xorg.conf monitor refresh rates to get it just right, but hey, it worked out of the box so to speak on the Sabayon ***LiveDVD*** & on the full HDD install & update.

The Sabayon 3.4F is at least 6, or more like 8 months old & it can handle my difficult nVidia card.  

So of course regarding Ubuntu, this begs the question?

---

### Post by walter13 on 2008-06-01
> **herbster said:**
> Oh, word of warning, don't get the Asus 8800GT. I am an Asus fan (P5K-E with new build) but they really drank the Kool-Aid on this one. The 8800GT has a proprietary thermal sensor, so you can't monitor your GPU temperature unless you use their crappy SmartDoctor software (which of course will require Windows). It's so incomprehensibly silly a thing to have done.

In fact, there is a way to monitor the temperature accurately with a modified version of nvclock.
Here are some information about that, and a package for ubuntu 8.04:
[http://computersstoneage.blogspot.com/2008/06/asus-nvidia-8800-gt-gpu-temperature.html](http://computersstoneage.blogspot.com/2008/06/asus-nvidia-8800-gt-gpu-temperature.html)

---

