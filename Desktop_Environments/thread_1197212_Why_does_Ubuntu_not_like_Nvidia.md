---
title: "Why does Ubuntu not like Nvidia?"
date: 2009-06-25
forum: Desktop Environments
---

### Post by Tholley on 2009-06-25
I have been searching for a problem with my new install of 9.04 as a dual boot with Xp on a HP Media Center PC that has a Nvidia Geforce card. 

Nobody has really jumped on my thread in Beginners like usual, so I am left trying to figure the problem out by myself (Install recommended proprietary driver, get "Input Signal out of Range") So I search Nvidia in the forum and most threads show 0 replies like mine. (as if nobody is willing to touch them...)


what's up with Ubuntu and Nvidia? Are they just not compatible?

---

### Post by ad_267 on 2009-06-25
The Nvidia drivers are closed source and proprietary, so it's out of Ubuntu's control and all up to Nvidia.

I haven't had any problems with Nvidia drivers in a while though, but I did find that sometimes the nvidia setup tool worked better than the default Ubuntu one for configuring monitors. You can run it by pressing Alt+F2 and running "gksu nvidia-settings". Make sure you choose the option to save your configuration to the xorg.conf file.

---

### Post by merlinus on 2009-06-25
Are you using the nvidia x server settings gui?  And installing them via System/Administration/Hardware Drivers?

I have had no problems with my geforce 9400, except when trying to use the latest proprietary ones from their website.

---

### Post by Tholley on 2009-06-25
Been there, done that... I get this... You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

Do that and get the "Input Signal out of Range" 

See this thread  [http://ubuntuforums.org/showthread.php?t=1196674](http://ubuntuforums.org/showthread.php?t=1196674)

I installed Ubuntu ons a friends old Dell with Nvidia and all worked fine.
No idea why I'm having problems with mine.

---

### Post by Tholley on 2009-06-25
> **merlinus said:**
> Are you using the nvidia x server settings gui?  And installing them via System/Administration/Hardware Drivers?

I have had no problems with my geforce 9400, except when trying to use the latest proprietary ones from their website.

Yes, went there and installed Recommended.

---

### Post by merlinus on 2009-06-25
What are the choices in X Server Display Configuration?  I had to play around a bit to get mine right.

---

### Post by Tholley on 2009-06-25
> **merlinus said:**
> What are the choices in X Server Display Configuration?  I had to play around a bit to get mine right.

X Server Display Configuration... (I'm still pretty much a newbie), is that the same as System/Preferences/Display? If that is the case I get this... "it appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" I click OK, I get this ..."You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I do that and back to square 1.

---

### Post by windfix on 2009-06-25
You installed nvidia-settings package via Synaptic Package Manager?

And nvidia-glx-180 package?

I have this on my Dell E6500; Nvidia X Server Settings tool appears under System | Administration.  While it is a PIA, it does work for me.  I sure wish Nvidia worked with the normal Ubuntu Display applet in Preferences though.

---

### Post by Tholley on 2009-06-25
> **windfix said:**
> You installed nvidia-settings package via Synaptic Package Manager?

And nvidia-glx-180 package?

I have this on my Dell E6500; Nvidia X Server Settings tool appears under System | Administration.  While it is a PIA, it does work for me.  I sure wish Nvidia worked with the normal Ubuntu Display applet in Preferences though.

I went to SPM, I have nvidia-180-libvdpau, I'll try an install nvidia-180- dev, and see what happens.

---

### Post by Tholley on 2009-06-26
I installed the nvidia-180-dev as per above, but that had no effect either.
 
Anybody have any ideas?
 
Should I just try re-installing 9.04? Maybe there is just a glich somewhere?

---

### Post by merlinus on 2009-06-26
X Server Display Configuration is one of the options in the Nvidia X Server Settings gui.

```

gksu nvidia-settings

```

If you run this from the System/Prererences menu, you will not be able to save your changes.

---

### Post by Tholley on 2009-06-26
> **merlinus said:**
> X Server Display Configuration is one of the options in the Nvidia X Server Settings gui.
 
```

gksu nvidia-settings

```
 
If you run this from the System/Prererences menu, you will not be able to save your changes.
 
I tried that last night as well and it takes me to the same place as "Display" with the same message as stated before.

---

### Post by merlinus on 2009-06-26
Do you not have NVIDIA Xserver Settings as a menu option in System/Preferences?  If not, you can find it at synaptic by searching for jockey.

---

### Post by Tholley on 2009-06-26
I'm not at my home computer right now, but will be in a couple hours.
 
I'm pretty sure I have that on my main menu, but it (I think) just does the same as going to Display... The Nvidia Xserver I guess is what says I'm not using the recommended driver and asks whether or not I want to. If I click Yes, it takes me to the list of which one of 3 drivers to Activate.
Which then leads to the initial problem.
 
If I click no, I get to the Display panel, but ony low res options. 
 
I'll double check that when I get back home.

---

### Post by merlinus on 2009-06-26
If I select System/Preferences/Display, I get the same error message as you did.  I can run the XServer Settings gui from the menu, but unless using the terminal command cannot save any changes.

System/Administration/Hardware Drivers gets me to the selection you just mentioned.

---

### Post by Tholley on 2009-06-26
I just posted this on another thread but I still need more help...

Well I think I am getting closer, but still have problems. 
I couldn't access Desktop from Rec Mode, so I was able to ctrl/alt/f1 and run the above.
But then I still get the bootup screen asking me to choose resolution, which I skip past. Then I get a window saying Ubuntu is running in Low Graphics mode. The following errors... blah blah blah.
Anyway, after going thru a bunch of crap, I was able to get back to my desktop.

Now, I activated the driver and rebooted, more Low graphics crap again, but the driver remains activated and even tho I had to choose No to use the driver going into Display (because as it say I need to run Nvidia-Xconfig as root, that did nothing. "gksu nvidia-xconfig" right?)

But I have a choice of 1280x1024 (5:4) (0hz refresh only option?)to choose from (it should be 1680x1050 16:9) and is a little better.

But also going into Appearance/Visual Effects, I can choose Normal, says could not be enabled.

So this is getting very frustrating and I'm wondering if I should just re-install and start all over again.
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7523360")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7523360")

---

### Post by merlinus on 2009-06-26
```

gksu nvidia-settings

```

worked for me.

---

### Post by Tholley on 2009-06-26
Tried that several times. Still the same saying I have to run nvidia-xconfig, which I have done numerous times.

Just going to reinstall Ubuntu tomorrow and see if anything changes.

Thanks for all the help anyways!

---

### Post by merlinus on 2009-06-27
No problema.  Hope your reinstall works, and please let me know.

FWIW, when I ran sudo nvidia-xconfig, nothing seemed to happen. gksu nvidia-settings opened a gui where I could change screen resolution, color depth, and refresh rates, and save the changes.

---

### Post by Tholley on 2009-06-27
> **merlinus said:**
> No problema. Hope your reinstall works, and please let me know.
 
FWIW, when I ran sudo nvidia-xconfig, nothing seemed to happen. gksu nvidia-settings opened a gui where I could change screen resolution, color depth, and refresh rates, and save the changes.
 
Yeah that's what it _should have done_ when _I ran_ gksu nvidia-settings, but would just show the "you don't seem to be running blah blah..., run nvidia-xserver as root, blah blah..."
 
Will update on the re-install when i get around to it.
 
Thanks again...

---

### Post by Tholley on 2009-06-27
Well I haven't finished with the re-install, but I have a feeling it won't be any different since even the Live CD has too low resolution also and I'm unable to change it to anything higher.

I googled Ubuntu Nvidia Resolution and found allot of the same problems going back years to Feisty Fawn. 

Here is a link to a bug report from 2 years ago, but I don't find a solution in it.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/82095](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/82095)

 I'm thinking maybe certain Nvidia cards may just not be compatible with Ubuntu. Maybe I'll go out and buy a cheap non-Nvidia card and see what happens... maybe...

Anybody...? Any ideas...?

---

### Post by Tholley on 2009-06-27
Ok maybe I was wrong, the new install seems to be working good now. As soon as it installed, I went to Appearance/Visual Effects, it was set at none, I selected normal, it told me I need to install the Nvidia drivers, I clicked OK, and all is good now!

Don't know what the problem was before, but I'm loving it now. 

Thank you to everyone who put in allot of effort to help me!

Terry

---

### Post by merlinus on 2009-06-28
Excellent news!  Glad you persevered...

---

