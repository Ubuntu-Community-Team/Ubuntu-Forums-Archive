---
title: "Unity Laggy Ubuntu 11.10"
date: 2011-10-14
forum: Desktop Environments
---

### Post by thewaffler100 on 2011-10-14
Hello, I recently upgraded from Ubuntu 11.04 to 11.10, and after the upgrade I noticed that the unity interface causes lags. Dragging windows is laggy, resizing windows is laggy, window animations are also laggy, and get this: It is still laggy even with static blur and no blur enabled. In 10.04 the animations used to be laggy. I have an ATI Radeon x1200 graphics chip, 128 MB shared memory. Anyone having problems with any ATI based graphics cards?:confused:

---

### Post by righardt on 2011-10-15
Hi,

I can confirm that I have the same experience! Anybody have any suggestions?

My graphics card details:
ATI Radeon 3000 Graphics

Thanks!

---

### Post by thewaffler100 on 2011-10-15
I disabled the active blur but no luck. Unity 2D sucks also, so I went ahead and installed GNOME 3 shell. Now moving windows around isn't laggy. I will miss Unity, though...

---

### Post by gamblor01 on 2011-10-15
I have an nvidia card so I can't tell if this will work for you or not, but the following post for Natty had a fix in it for laggy performance with an ATI card.  You might want to check it out:

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)


The relevant section says:

> **Using an AMD (ATI) graphics card with the latest Catalyst 11.04 and experience bad performance / lag?**

To get better performance, install CompizConfig Settings Manager (see the first tip in the post for installing it), then open it from Dash and go to the "OpenGL" plugin and uncheck the "Sync to VBlank" option.


If you don't want to have to follow the link to determine the proper way to install CCSM then just run this in terminal:

```

sudo apt-get install compizconfig-settings-manager

```


Maybe try that and see if it works?

---

### Post by JustGlowing on 2011-10-15
I noticed the same problem and I started to use Unity 2d.
In the login screen I checked Ubuntu 2 in the user setting.

I hope it helps.

---

### Post by Remuzzz on 2011-10-16
I'm having the same problem with my Ati x600 card. Ubuntuy 11.04 runs smoothly. 11.10 is laggy as hell. Disabling Sync to vblanc doesn't work. 

Anyone else got a solution? I'm really desperate, I was used to the effects in 11.04 and don't want to miss them, so Unity 2d isn't an option.

Using lower resolutions doesn't fix the problem. Effects like fading unity and minimizing windows run smoothly, but dragging windows is really slow.

Gnome Shell is less laggy btw, so in the mean time I'll stick to that

---

### Post by ApproachMedium on 2011-10-16
I also have a laggy issue with my 11.10. Reinstalled twice and cant get it to work right. Video works perfectly however in 11.04. Had this same exact issue with the beta as follows.

When I enter "lspci | grep -i vga" in the terminal, it tells me i have VGA Compatible controller: ATI Technologies Inc RS960M [Radeon x1200 Series] However, when I go to system settings>system info under graphics it says Unknown. I believe this is the issue why my video is so slow, and why I cant get VM Ware to work. Many articles mention opening Additional Drivers and selecting something in there and hitting activate. When I open additional drivers, I get blank. Nothing. Zilch. I have tried a few things that suggest doing things thru the terminal but none work so far. Im sure it doesnt help that I am very new to Unix, so if anyone has any help or suggestions please go easy on me.

Other things to keep in mind, this is a work issued laptop. HP Compaq 6715b. Upgrading to a new machine is not an option. HP provides no support or drivers from their website for Linux, and ATI hasn't been much of any help either. We are trying to use Ubuntu to save time on virus repairs etc as the laptops are used for mission critical repairs and diagnostics of railroad equipment.

---

### Post by mcduck on 2011-10-16
> **Remuzzz said:**
> I'm having the same problem with my Ati x600 card. Ubuntuy 11.04 runs smoothly. 11.10 is laggy as hell. Disabling Sync to vblanc doesn't work. 

Anyone else got a solution? I'm really desperate, I was used to the effects in 11.04 and don't want to miss them, so Unity 2d isn't an option.

Using lower resolutions doesn't fix the problem. Effects like fading unity and minimizing windows run smoothly, but dragging windows is really slow.

Gnome Shell is less laggy btw, so in the mean time I'll stick to that
If the effects work fine, the problems would probably be something else than the actual hardware requirements.

Try decreasing the Mouse Polling Interval (in the Mouse position polling-plugin). Some of the Compiz features are really lagging for me with the default polling interval, but dropping it to minimum makes them prefectly smooth. (I'm using a laptop with Mobility Radeon X1600, by the way, so just like you I'm stuck with using the opensource drivers and no support from Ati/AMD)

---

### Post by Remuzzz on 2011-10-16
Thanks for your reply. It doesn't make a huge difference to decrease the mouse-polling interval. I wonder which plugin is new/updated and causing my problems, since 11.04. 

:(

---

### Post by flamarro on 2011-10-17
Hi guys,
just posted [this]("http://ubuntuforums.org/showpost.php?p=11356747&postcount=37") in other thread before i saw yours, and is exactly the annoying problem that i feel.

Sorry for my english. :)

---

### Post by alexds9 on 2011-10-17
I've installed **Ubuntu 11.10**, **64bit** version, on **HP Compaq 6715s**. 
My graphical card is **ATI RS690M** [**Radeon X1200** Series].
Just after the installation windows drugging was laggy. Then I've installed the packages: ***fglrx*** and ***fglrx-amdcccle***. The windows drugging became smooth, but any graphical task, "***glxgears***" for example, fails with similar error:[INDENT]**X Error of failed request:  BadRequest (invalid request code or no such operation)**
**  Major opcode of failed request:  135 (GLX)**
**  Minor opcode of failed request:  19 (X_GLXQueryServerString)**
**  Serial number of failed request:  12**
**  Current serial number in output stream:  12**
[/INDENT]Also, ***amdcccle ***fails with error:
 [INDENT]**There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.**
**No AMD graphics driver is installed, or the AMD driver is not functioning properly.**
**Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.**
[/INDENT]

---

### Post by klein de usa on 2011-10-18
hi 

found this like you can ask the unity team directly 

[http://askubuntu.com/questions/ask?tags=unity]("http://askubuntu.com/questions/ask?tags=unity")

make your voices heard

---

### Post by saiki4116 on 2011-10-18
i am also facing same problem...gnome shell is not rendered properly..graphic card driver not getting installed,,,my grphic card is ati mobile radeon hd5470 with 1gb graphic memory..but the intel integrated graphic card is working...

---

### Post by swappa on 2011-10-19
This issue has been my #1 problem with a lot of distros on my laptop. It became a lot worse with Unity though. And, in 11.10 the GUI is almost unusable. From googling, users reporting this is often using some kind of a mobile graphic chip. Mine is the Nvidia Quadro NVS 160M. Not exactly great, but the performance I get in Windows is light years better compared to Ubuntu 11.10. I would expect Ubuntu (and its siblings) to at least be on par.

I have tried all the hacks to no avail. I have tried with and without proprietary drivers, but the open source version is, sorry to say; Crap. 

If I just sit idle and observe TOP - Xorg can use 50% of the CPU for about 10 minutes without me doing anything on the computer what so ever. 

To me this is a show stopper, and I am greatly disappointed. They really have to pay attention this. It has been a problem for many for a long time. Fancy features and innovative thinking is fine, but, make sure the basics are working first.

---

### Post by fraktalek on 2011-10-24
I have the same problem on my T420 ThinkPad with SandyBridge graphics only (i5). System info in the settings even shows the probably correct video driver SandyBridge mobile.

After trying to change the Sync to VBlank option in OpenGL, Unity 3D stopped working completely, I had to reset the settings to default.

---

### Post by Green_Star on 2011-10-28
My 11.10 upgrade worked fine for more than a week, but after few updates yesterday the video lag started, I tried disabling options in Openggl etc etc with no luck in display lag. Any video play takes 100% CPU and still video tears a part frequently, it is very hard to watch at my browser when I do scrolling, and I type a sentence and stop, ubuntu takes maybe 0.5 secs to complete typing, I mean the test still coming even after I stopped tying. By the way I am using latest(as of now) ATI catalyst drivers for my HD4200 video card.

---

### Post by fraktalek on 2011-10-28
maybe it's partly related to this Compiz CPU eating bug: [https://bugs.launchpad.net/unity/+bug/803943](https://bugs.launchpad.net/unity/+bug/803943)

at least I see this behaviour in my case too

---

### Post by CrusaderAD on 2011-10-28
I had the same problem. I started using Ubuntu 2D from the login menu. My graphics card must just be poorly supported. Much better under 2D.

---

### Post by bagm on 2011-10-31
bump

---

### Post by k4rizma on 2011-10-31
Is there a way to disable unity and go to the normal desktop environment without having to install the Compiz software? 

I have a user base I would like to upgrade but they highly dislike the unity UI. 

Thanks.

---

### Post by mcduck on 2011-10-31
> **k4rizma said:**
> Is there a way to disable unity and go to the normal desktop environment without having to install the Compiz software? 

I have a user base I would like to upgrade but they highly dislike the unity UI. 

Thanks.

Well, depends on what is the "normal desktop environment" you want.

Ubuntu 11.10 by default only comes with a combination of Gnome 3 and Unity, available in both 3D and 2D variants.

If you want Gnome Shell instead, you'll have to install it. And same of course goes for any other desktop environment than Gnome.

If you want Gnome 2, then no, you can't get that any more. It's out of development and unsupported now. Gnome Shell's fallback mode is quite similar, though, as is XFCE4 and perhaps even LXDE.

Anyway, you of course don't need to install Compiz to change your desktop environment. Not that you even could install Compiz, it's already installed by default like it has been for several Ubuntu versions now. And assuming you were talking about CompizConfig Settings Manager, that's also unrelated to changing your desktop environment. They are simply selected from the login screen..

---

### Post by bagm on 2011-10-31
I think we should report this as a bug.
I see there are different cards involved, OP is ATI, mine is NV.
I commented on this thread in this one bug:
[https://bugs.launchpad.net/unity/+bug/803943](https://bugs.launchpad.net/unity/+bug/803943) (Compiz consuming a lot of cpu)

---

### Post by anatolik on 2011-11-03
I have ATI HD 2600 and it also lagged when I installed Unity.

I solved it but installing ATI proprietary drivers using "Additional Drivers" program. It seems Unity does not like open source drivers.

---

### Post by TeamRocket1233c on 2011-11-03
Tried adding more RAM, upgrading to a faster CPU and a better video card, or just using a different DE/WM, like KDE, Openbox, JWM, etc.?

---

### Post by typhoon_tip on 2011-11-03
Try this simple fix, worked for me (I have the compiz idle effect too, but it's not related to the choppy I think... at least not that much !).

- Install fglrx driver (stock driver is choppy...)
- Open AMD Catalyst (after reboot !)
- Enable "tear free" desktop option
- Open compiz config
- OpenGL plugin, untick Sync to VBlank, Texture = BEST, Lighting effect ON
- Composite plugin, Detect refresh rate unticked, set the refresh rate at double your video frequency (in my case 60 Hz, I set it to 120)
- Close compiz
- Log ogg
- Log in again, it should be now smooth as silk and tear free

Please give me a feedback on this procedure, as it worked for me since 11.04 till 11.10, seems quite consolidated.

Be careful not to touch anything else in those OpenGL and Composite plugins !

---

### Post by flamarro on 2011-11-04
> **typhoon_tip said:**
> Try this simple fix, worked for me (I have the compiz idle effect too, but it's not related to the choppy I think... at least not that much !).

- Install fglrx driver (stock driver is choppy...)
- Open AMD Catalyst (after reboot !)
- Enable "tear free" desktop option
- Open compiz config
- OpenGL plugin, untick Sync to VBlank, Texture = BEST, Lighting effect ON
- Composite plugin, Detect refresh rate unticked, set the refresh rate at double your video frequency (in my case 60 Hz, I set it to 120)
- Close compiz
- Log ogg
- Log in again, it should be now smooth as silk and tear free

Please give me a feedback on this procedure, as it worked for me since 11.04 till 11.10, seems quite consolidated.

Be careful not to touch anything else in those OpenGL and Composite plugins !

Hi guys,
man, you did it. It really worked. Although it has a little lag, maybe it is because of i am focusing on seeing some lag :), but it really has nothing to do to what was before.
pufff, i couldn't keep seeing this in Ubuntu. Now, lets really try this. I'm so glad.
Again, sorry about my poor English, but i think i could show how glad i am.

---

### Post by typhoon_tip on 2011-11-05
> **flamarro said:**
> Hi guys,
man, you did it. It really worked. Although it has a little lag, maybe it is because of i am focusing on seeing some lag :), but it really has nothing to do to what was before.
pufff, i couldn't keep seeing this in Ubuntu. Now, lets really try this. I'm so glad.
Again, sorry about my poor English, but i think i could show how glad i am.

Hey thank you pal, no worries, I understood perfectly. I spent a looong time over this issue too, pissed me off totally that I couldn't get a smooth Desktop, as utilization of GPU and CPU was practically null and still "choppy".

Hope this post help everyone with similar problem ! Perhaps we could make an "how to" thread for ATI + fglrx...

EDIT: when many things are opened, some lag is still normal tough, because anyway the power of the PC is not unlimited.

---

### Post by Samos123 on 2011-11-05
@typhon_tip anybody care to give some more instructions for a noob :P ? would help me a lot. Like where is the compiz config? and what commands to run?

Thanks a lot, i am using unity2d for now, which works and fast and responsive but would like to switch. I am using ati radeon 4200 HD for laptop.

---

### Post by bmw-uf on 2011-11-08
This guid is not very helpful to me with hd2400, but you can try.
Compiz Config not installed by default, run console and copy this tu install it:

```
sudo apt-get install compizconfig-settings-manager
```

After it you can find compizconfig in main menu by typing "compiz".

To install ati fglrx driver you can use jockey-gtk.

---

### Post by linuxaddix on 2011-11-08
unity is a ram hog i think it uses about 260mb install gnome shell it uses about 140mb ram a bit lighter on the ram its probably laggy cause the update to a newer version has repository clashes.a fresh install is better

---

### Post by linuxaddix on 2011-11-08
if you wanna run compiz in unity for 11.10 here it is:
[http://ubuntuforums.org/showthread.php?t=1864603](http://ubuntuforums.org/showthread.php?t=1864603)

---

### Post by typhoon_tip on 2011-11-08
> **Samos123 said:**
> @typhon_tip anybody care to give some more instructions for a noob :P ? would help me a lot. Like where is the compiz config? and what commands to run?

Thanks a lot, i am using unity2d for now, which works and fast and responsive but would like to switch. I am using ati radeon 4200 HD for laptop.

Sorry I arrived late :P

I think bmw-uf above already replied for the compiz part. For the rest, I try to explain better what to do:

- Install fglrx driver (stock driver is choppy...); to do this, just open "Additional Drivers" application and select "ATI/AMD proprietary FGLRX driver" (do not use post-updates/release), then click "activate" and wait for it to finish. EDIT: if it doesn't appear in the list, your hardware may not be supported.
- Open "AMD Catalyst" (after reboot !)
- Enable "tear free" desktop option (one will find it easily)
- Open compiz config (command: ccsm)
- OpenGL plugin, untick Sync to VBlank, Texture = BEST, Lighting effect ON (be careful here, to open the settings, click on the buttons and NOT on the tick/untick for the element, or entire desktop will disappear).
- Composite plugin, Detect refresh rate unticked, set the refresh rate at double your video frequency (in my case 60 Hz, I set it to 120)
- Close compiz
- Log ogg
- Log in again, it should be now smooth as silk and tear free

:popcorn:

---

### Post by hopugop on 2011-11-27
> **typhoon_tip said:**
> Try this simple fix, worked for me (I have the compiz idle effect too, but it's not related to the choppy I think... at least not that much !).

- Install fglrx driver (stock driver is choppy...)
- Open AMD Catalyst (after reboot !)
- Enable "tear free" desktop option
- Open compiz config
- OpenGL plugin, untick Sync to VBlank, Texture = BEST, Lighting effect ON
- Composite plugin, Detect refresh rate unticked, set the refresh rate at double your video frequency (in my case 60 Hz, I set it to 120)
- Close compiz
- Log ogg
- Log in again, it should be now smooth as silk and tear free

Please give me a feedback on this procedure, as it worked for me since 11.04 till 11.10, seems quite consolidated.

Be careful not to touch anything else in those OpenGL and Composite plugins !

This works perfectly! Thank you very much! :D These news should be spread!! :popcorn:

---

### Post by typhoon_tip on 2011-11-27
> **hopugop said:**
> This works perfectly! Thank you very much! :D These news should be spread!! :popcorn:

I saw some guy posted already something in an Ubuntu page, looks like we came to the exact same conclusion, but he posted much earlier (I think in April 2010), anyway the page is still there. I never look for it because I had the problem back since 10.04 and there was no guideline back then, so I just figured it out by trying dozens of settings.

---

### Post by novatax on 2011-12-02
> **typhoon_tip said:**
> Sorry I arrived late :P

I think bmw-uf above already replied for the compiz part. For the rest, I try to explain better what to do:

- Install fglrx driver (stock driver is choppy...); to do this, just open "Additional Drivers" application and select "ATI/AMD proprietary FGLRX driver" (do not use post-updates/release), then click "activate" and wait for it to finish. EDIT: if it doesn't appear in the list, your hardware may not be supported.
- Open "AMD Catalyst" (after reboot !)
- Enable "tear free" desktop option (one will find it easily)
- Open compiz config (command: ccsm)
- OpenGL plugin, untick Sync to VBlank, Texture = BEST, Lighting effect ON (be careful here, to open the settings, click on the buttons and NOT on the tick/untick for the element, or entire desktop will disappear).
- Composite plugin, Detect refresh rate unticked, set the refresh rate at double your video frequency (in my case 60 Hz, I set it to 120)
- Close compiz
- Log ogg
- Log in again, it should be now smooth as silk and tear free

:popcorn:

thx buddy, feels much smoother, but only for while. When I drag the window faster this lag came again..

I experience this problem on my Dell Inspiron M102z as in [http://www.ubuntu.com/certification/hardware/201011-6847:201101-6961](http://www.ubuntu.com/certification/hardware/201011-6847:201101-6961) (mine powered by E450) ; Toshiba L645D-S4033 ; even my desktop (HD4650).

---

### Post by typhoon_tip on 2011-12-03
> **novatax said:**
> thx buddy, feels much smoother, but only for while. When I drag the window faster this lag came again..

I experience this problem on my Dell Inspiron M102z as in [http://www.ubuntu.com/certification/hardware/201011-6847:201101-6961](http://www.ubuntu.com/certification/hardware/201011-6847:201101-6961) (mine powered by E450) ; Toshiba L645D-S4033 ; even my desktop (HD4650).

Happens to me as well, laptops all have this "problem", because they use scaling technology of CPU and GPU (Intel). Normally at start, all laptops are in Automatic OnDemand mode. Setting to performance will bring drastic difference to GPU as well as CPU, but will drain the battery faster.

We are lucky however, as we can set the mode ourselves. Try to do the following thing (attention, for Unity !):
```
sudo apt-add-repository ppa:artfwo/ppa
sudo apt-get update
sudo apt-get install indicator-cpufreq
```

After finishing, if a new icon do not appear in top bar, logoff and login again. Click on the icon and set the mode to "Performance", you will notice a huge difference in graphic 2D acceleration performances overall.

---

### Post by danger89 on 2012-01-22
@typhoon_tip

WOW! That is a huge difference indeed. I want to thank you really much.

I hope my battery wont drain, but it's not laggy anymore (using Intel HD).

Still Compiz & Xorg has huge CPU speaks while moving a window, so that is still NOT solved, but this indicator is a start...

---

### Post by pst007x on 2012-03-18
This resolved laggy Ubuntu desktop. Not a perfect solution, more of a tweak.. Thanks 

#NVidia 

...Add latest drivers PPA, and upgrade:

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update && sudo apt-get install nvidia-current nvidia-settings

(I tried Additional Drivers: "post-release updates" didn't work for me)

#COMPIZ

...Added following Compiz PPA and upgrade:

sudo apt-add-repository ppa:vanvugt/compiz

sudo apt-get update && sudo apt-get upgrade

...Or add via a source manager:

deb [http://ppa.launchpad.net/vanvugt/compiz/ubuntu](http://ppa.launchpad.net/vanvugt/compiz/ubuntu) oneiric main

deb-src [http://ppa.launchpad.net/vanvugt/compiz/ubuntu](http://ppa.launchpad.net/vanvugt/compiz/ubuntu) oneiric main

...then update and upgrade compiz

(the source is found here: [https://launchpad.net/~vanvugt/+archive/compiz](https://launchpad.net/~vanvugt/+archive/compiz))

#Install Compiz-Setting-Manager:

(this is found in the Ubuntu software centre)

#COMPIZ SETTINGS: Open and navigate to:

...Composite setting:

DETECT REFRESH RATE: (UNTICK)

REFRESH RATE: (DOUBLE YOUR REFRESH RATE)

...Mouse Position Polling setting:

MOUSE POLL POSITION: (1).

...Snapping Windows:

SNAPPING WINDOWS: (UNTICK)

...Move Window:

OPACITY: 30

LAZY POSITIONING: (UNTICK)

...OpenGL

SYNC TO VBLANK: (UNTICK)

TEXTURE: (BEST)

LIGHTING EFFECT: (ON)


#Configuring The Right Driver

The next thing to do is to make sure that your machine uses the correct driver. To ensure that, we are going to blacklist the nouveau driver first. Open a terminal and enter the following to do so:

sudo nano /etc/modprobe.d/blacklist.conf

...At the end of the document, add this line:

[...]

blacklist nouveau

...Afterwards update your initial ram file system by entering this into a terminal:

sudo update-initramfs -u -v

...Then check:

sudo nano /etc/X11/xorg.conf

...Find the Device section and make sure the driver is set to "nvidia". It should look somewhat like this:

[...]

Section "Device"

Driver "nvidia"

Identifier  "Default Device"

Option  "NoLogo"    "True"
EndSection

[...]

---

### Post by Linuxman1900 on 2013-03-11
One of the main reasons unity is laggy is because it uses Compiz. The problem with that is, Compiz hasn't been in development for months or maybe even years. Which is why GNOME 3 disabled the ability to swap window managers. Also why KDE created it's own similar compiz effects. Also why XFCE and LXDE don't recommend compiz. And of course why cinnamon and pantheon forbid switching window managers. Since 12.10 removed unity 2d you are stuck with compiz... And installing an AMD or NVidia driver in 12.10 WILL Break the system, because the package linux-kernel-headers was removed which is completely dumb! Considering that steam is out (And steam expects proprietary drivers to work the best.) People who have AMD and NVidia drivers will be F%CKED UP! They'll wanna play steam games so they'll install the proprietary driver and then reboot and well BOOM! Nothing if they're an AMD or NVidia user. Just a wallpaper and only able to use ctr-alt-T to open the terminal remove the fglrx package reboot install linux-kernel-headers and on and on. I mean Canonical just cannot do this to us AMD or NVidia users. Another reason I seriously want to switch to Gentoo.

---

### Post by coffeecat on 2013-03-11
This thread is about Ubuntu 11.10.

Back to sleep, old thread.

---

