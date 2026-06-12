---
title: "Nvidia driver problem in Jaunty"
date: 2009-04-30
forum: General Help
---

### Post by Geobot on 2009-04-30
So I just decided to change from 8.10 to 9.04. The install went smoothly(fresh install, not upgrade), did the auto-updates, so I had a nice clean install.

Upon install, it prompted me to install the proprietary Nvidia driver like normal, which I did, ver 180.

However, it doesn't appear to be working. No desktop effects can be used, no 3d in games, etc. 

I tried the other two driver versions listed, 173 and 96, no dice. Then I purged all the nvidia drivers with apt-get purge nvidia* envy and installed a fresh 180.51 from the Nvidia site according to directions I found on another post here. That didn't fix it either. 

My computer has an Nvidia 6200 card, and it worked fine with 8.10, so I'm not sure exactly what the problem is. Any help would be appreciated.

---

### Post by DeMus on 2009-04-30
> **Geobot said:**
> So I just decided to change from 8.10 to 9.04. The install went smoothly(fresh install, not upgrade), did the auto-updates, so I had a nice clean install.

Upon install, it prompted me to install the proprietary Nvidia driver like normal, which I did, ver 180.

However, it doesn't appear to be working. No desktop effects can be used, no 3d in games, etc. 

I tried the other two driver versions listed, 173 and 96, no dice. Then I purged all the nvidia drivers with apt-get purge nvidia* envy and installed a fresh 180.51 from the Nvidia site according to directions I found on another post here. That didn't fix it either. 

My computer has an Nvidia 6200 card, and it worked fine with 8.10, so I'm not sure exactly what the problem is. Any help would be appreciated.

Try to get the original driver shipped with Jaunty installed.
Then go to System - Administration - Hardware drivers
Just above the close button you see a button to install the right one. For me, since I installed it already, the button says Remove.

---

### Post by Geobot on 2009-04-30
Well, that's exactly what I did upon install. Right after the fresh installation, it prompted me with that dialog, so I chose 180 and hit 'install'. It did its thing, but the 3d didn't work. Oh, and yes, I restarted the pc after that.

---

### Post by kpkeerthi on 2009-04-30
Enter this command in the terminal and reboot.
```
sudo nvidia-xconfig
```

---

### Post by 4Orbs on 2009-04-30
If I understand correctly, the most recent activity was manually installing the nVidia driver using the .run package from nVidia's website?

When you manually install the driver, it is activated automatically during install... so don't try to activate it with the Hardware Drivers Mgr afterwards. The Hardware Drivers Mgr does not work with manually installed drivers.

If this is what you did, I suggest uninstalling the manually installed driver then try to activate the driver provided by Ubuntu in the Hardware Drivers Mgr. You gotta kill gdm first. In a terminal enter:
```
sudo /etc/init.d/gdm stop
```
Then login to the black screen (you might need to hit CTL ALT+F1 to bring up the login). Then enter:
```
sudo nvidia-uninstall
```
Then start gdm again:
```
sudo /etc/init.d/gdm start
```
It's probably best to reboot before using the Hardware Drivers Mgr to activate the driver provided by Ubuntu.

---

### Post by Geobot on 2009-04-30
kpkeerthi - Done, but with no success.

---

### Post by Geobot on 2009-04-30
4Orbs - Well, after manually installing the .run package, the first thing I did was check to see if my 3d worked, before going to the Hardware Drivers applet. That being said, I went ahead and uninstalled my driver like you said anyway, because what could it hurt, right?

Well, it didn't seem to hurt anything, but the only thing I notice different now after activating the default driver is that I don't get the option to install the proprietary drivers in the Hardware Driver manager any more. Before, it gave me 3 options for Nvidia(180, 173, and 96). Now it just says "No proprietary drivers are in use on this system".

Of course, my 3d still doesn't work, otherwise I'd be cheering.

---

### Post by 4Orbs on 2009-04-30
It doesn't show any drivers because you purged them two steps previously. You can either go to Synaptic and reinstall the nvidia-180-modaliases and nvidia-common and the driver, THEN go to activate it in Hardware Drivers Mgr.

Or you can install EnvyNG and use it to install the driver.

Or you can install the driver manually with the .run package from nVidia's website, but don't try to activate it if you choose this option.

One question: When you first used the Hardware Drivers Mgr to activate the driver, did the process complete and then prompt you to restart the computer?

And a second and third question: When you installed it with the .run package, did it inform you of success, and did you tell it to configure the xorg.conf for you and merge with the current one?

---

### Post by Geobot on 2009-04-30
4Orbs- To answer your question, yea, it prompted me to restart afterwards, which I did.

Just now, I reinstalled the drivers via Synaptic and activated in Hardware Drivers, but that didn't help.

So basically, I've tried the Ubuntu drivers twice, and manually installing the driver from nvidia three times now, purging between changing drivers. I honestly don't know what the problem is. I never had this problem with 8.10, and I haven't changed hardware.

EDIT:
To answer your other questions... Yes, it said it was successful, and it asked me whether I wanted to configure xorg, which I did, and it said that part was successful as well.

---

### Post by 4Orbs on 2009-04-30
Does the Hardware Drivers Mgr tell you that the driver is currently activated?

If it shows that it's activated. What do you see when you go to System-> Preferences-> Appearance-> Visual Effects? Is it greyed out preventing you from turning on the effects?

---

### Post by Geobot on 2009-04-30
Yep, NVIDIA accelerated graphics driver(version 180)[Recommended] shows Activated and currently in use.

---

### Post by 4Orbs on 2009-04-30
I edited my previous post with an extra question.

---

### Post by muhannadfa on 2009-04-30
i'm new user of jaunty 9.04 (buggy release) oh no i think its still RC even,
-------------------------------
Nvidia problrm
on other laptop of mine > ATI problem
on the 3rd > Intel problem
All over three > network connection problems
Cpu over use problems >
--------------------------------
i think this RC release needs alot of work
i know it's officail release > what a shame
--------------------------------
moving back to 8.10 
bbye

---

### Post by Geobot on 2009-04-30
Hmm, ok, well, apparently now my Desktop effects decided to work, but no 3d in games. I don't know why the effects just started working, but they did. 

But to answer your question properly, no they weren't greyed out, but they weren't before either. It would just tell me 'no' when I tried to enable them. Now it seems to work fine, I just need to figure out what's causing my other problem. 

May be wine related, but I doubt it. The game I'm trying to get running is EVE online, which worked fine before also. It loads and works as is, but none of the 3d models show up. all the 2d backgrounds and overlays work, though.

I might find another game or two to see if those will work correctly.

Thanks for the help

---

### Post by ivanhoe75 on 2009-04-30
I have almost same problem with 7600gs videocard. I tried all available drivers - 180, 177... x win do not start after that at all

---

### Post by 4Orbs on 2009-04-30
Any games that require a video test when installing should be retested so they can choose the correct Hal mode now. Don't know about Eve, but I had to let Diablo2 retest and reconfigure after I finally got the proper driver installed.

You know, these Linux geek developers do subtle things so they can get a good laugh at our expense.

Anyway, I think Jaunty is great and quite trouble-free considering all the big changes since Intrepid.

---

### Post by infinitejones on 2009-04-30
I've been having exactly the same problem as the OP. I've started my [own thread]("http://ubuntuforums.org/showthread.php?t=1137849") about it with no useful responses so far, so since this thread seems to have a bit of traffic, here's the story so far:

HP Laptop with nVidia 8400M video card. Under Intrepid, with the current stable nVidia driver (180) installed and activated via System -> Administration -> Hardware Drivers, full Desktop Effects worked perfectly, via System -> Preferences -> Appearance -> Desktop -> Visual Effects.

Following a clean upgrade to Jaunty (/ partition formatted, /home partition not), Desktop Effects don't work. nVidia driver 180 is installed and activated via Hardware Drivers. Everything else updated after installation via aptitude. All that happens when I try to activate them is a dialogue box saying "Desktop effects could not be enabled".

Ironically, when I'd done a sudo update-manager -d from Hardy to a pre-release Jaunty, it all worked fine. The problem only appeared following a clean update. This must be a clue to someone who knows about these things.

I've found a couple of threads on Ubuntuforums and Launchpad talking about blacklisted video cards in the new version of compiz, but the nVidia 8400M isn't on that blacklist.

Any other suggestions ***at all?*** Thanks!

---

### Post by kpkeerthi on 2009-04-30
> **muhannadfa said:**
> i'm new user of jaunty 9.04 (buggy release) oh no i think its still RC even,
-------------------------------
Nvidia problrm
on other laptop of mine > ATI problem
on the 3rd > Intel problem
All over three > network connection problems
Cpu over use problems >
--------------------------------
i think this RC release needs alot of work
i know it's officail release > what a shame
--------------------------------
moving back to 8.10 
bbye
Have you considered filing a bug report?

---

### Post by 4Orbs on 2009-04-30
> Ironically, when I'd done a sudo update-manager -d from Hardy to a pre-release Jaunty, it all worked fine. The problem only appeared following a clean update. This must be a clue to someone who knows about these things.

So the system you're running now has been upgraded from Hardy to Intrepid to Jaunty?

---

### Post by infinitejones on 2009-04-30
> **4Orbs said:**
> So the system you're running now has been upgraded from Hardy to Intrepid to Jaunty?

Sorry, I've just realised my error. When I say Hardy, I mean Intrepid.

> **kpkeerthi said:**
> Have you considered filing a bug report?

One has already been filed: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363967]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363967")

---

### Post by 4Orbs on 2009-04-30
If the Hardware Drivers Mgr says that the driver is activated and in use, but you are unable to turn on the desktop effects... my suggestion is first to deactivate the driver, reboot then reactivate the driver. If that doesn't help... my next suggestion is to open the nvidia settings mgr as root (gksudo nvidia-settings) and make sure resolution and other settings agree with what you really see, then click the button to save to xorg.conf file. You probably should make a backup copy of your current /etc/X11/xorg.conf before overwriting it from the nVidia Settings Mgr.

Reboot after saving the new version of the file (which possibly will be no different from the current one), then try again to enable the desktop effects.

---

### Post by infinitejones on 2009-04-30
OK... in the nVidia X Server Settings dialogue, the OpenGL/GLX Information tab just says "Fail to query the GLX server vendor."

I googled that and found a few threads that seem to be discussing the same problem, but they're for older versions of Ubuntu so I'm reluctant to try any of the suggested fixes.

The only thing I did try was this:

```
glxinfo | grep rendering
```

which returns

```
Error: couldn't find RGB GLX visual or fbconfig
```

I then googled that error and found [this current bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/354484") on launchpad. There's a fix on the page involving (re)creating a symlink in /usr/lib/xorg/modules but that doesn't work either...

Anyway, this is now getting above my head so unless anyone has any other ideas, or has fixed the problem already, I'll just keep track of the bug on launchpad.

---

### Post by infinitejones on 2009-05-02
In case anyone's following this - I just re-installed from the ISO and desktop effects work perfectly now. No idea what was wrong before - but since it only took me about 15 mins to reinstall, compared to the couple of hours I spent fiddling and researching the actual problem, maybe that's just the best solution...

---

