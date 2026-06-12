---
title: "Gutsy gaming PC"
date: 2007-11-24
forum: Gaming &amp; Leisure
---

### Post by Burkey on 2007-11-24
I have just installed Gutsy on my amd64, everything is pretty much go now:

gForce 8600GTS (3D desktop on etc, DRI enabled)
DWL-G510 wireless seems to be working, it lost it's connection once and I had to reboot to get it working again though

So, I am after some advice, should I disable the 3D desktop for better game performance?  Or does it not matter?

For the Wireless, is the default Gutsy driver best or something else?  Has anyone had problems with this?

Thanks in advance!

---

### Post by hardyn on 2007-11-24
yes, disabling 3d desktop will get you better gaming performance as the 3d desktop stay in video memory.

i have had no trouble with the default wifi manager, but many have complained... if it works, great; if you want to try something else, that is great too.

---

### Post by Burkey on 2007-11-24
thanks for the reply hardyn, I did disable the 3D desktop, it may have bumped my fps a little.

btw.. I am running World of Warcraft inside wine.. my hardware should kill it really, but I am still not being blown away by it!  30+fps is just ok, it should never drop below 60 with this kind of hardware.

Not sure if the default nvidia driver is the best either or if there is otherthings to do such as xorg.conf mods etc.

I am also wondering about the kernel, is there a low-latency kernel?  Would it be better for games?

---

### Post by Xavieran on 2007-11-24
Don't know about the kernel...but I would definetely use the proprietary driver...sorry Stallman ;-)

---

### Post by Tyke91 on 2007-11-24
if you haven't gone into the "restricted drivers manager" and updated your nvidia drivers, then do it now and you will see a great boost in performance... I dunno... for WoW, perhaps the added strain of running wine is slowing it down just a tad? I know that windows Team fortress two works maybe 10-20 fps faster than wine+linux TF2...

---

### Post by Burkey on 2007-11-24
Hmm, it gave me the proprietary driver thing and installed for me automatically.. do you guys mean I should go to nvidia's site and download the latest driver from there?  Or is there a newer one in synaptic?

Edit: just checked synaptic, it has already installed nvidia-glx-new with version 100.14.19+2.6.22.4-14.10

---

### Post by Sockerdrickan on 2007-11-24
The new nVidia driver gives you much better FPS [www.nvidia.com/drivers](www.nvidia.com/drivers) go to beta

---

### Post by hikaricore on 2007-11-24
> **Tux0r said:**
> The new nVidia driver gives you much better FPS [www.nvidia.com/drivers](www.nvidia.com/drivers) go to beta

You're talking about this one: [http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)
As compared to this one: [http://www.nvidia.com/object/linux_display_ia32_100.14.23.html](http://www.nvidia.com/object/linux_display_ia32_100.14.23.html)

(linking 32bit as that's what I'm using)

Right Tux0r?  I'm going to test it out,didn't even know they popped out a new beta.  ^_^

**EDIT** Hot damn, that auto detect freq in the OC section finally works for me.  ^_^

---

### Post by stinger30au on 2007-11-24
do disable the 3d effects on screen, on your tool bar you will see a red rock, or gem stone looking thing.

right click on it

you will see window manager and 3 choices. you will see beryl, compiz or gnome

set it to gnome for default deiver

---

### Post by KhaaL on 2007-11-24
Does anyone know if the realtime kernel affects gaming performance?

---

### Post by Sockerdrickan on 2007-11-24
> **hikaricore said:**
> You're talking about this one: [http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)
As compared to this one: [http://www.nvidia.com/object/linux_display_ia32_100.14.23.html](http://www.nvidia.com/object/linux_display_ia32_100.14.23.html)

(linking 32bit as that's what I'm using)

Right Tux0r?  I'm going to test it out,didn't even know they popped out a new beta.  ^_^

**EDIT** Hot damn, that auto detect freq in the OC section finally works for me.  ^_^

I knew you would like it ;)

---

### Post by hardyn on 2007-11-24
probably not, infact i would think it may hurt game performace.

RT kernels are designed for motion control, or audio applications (DJ suites) where real-time execution of the system components is manditory, when playing a game, you want most of the CPU processing the game, not managing the rest of the computer (and i think software has to be written to utilize realtime kernel hooks anyway)... but of course, if you are not doing anything mission critical... TRY IT (and let us know)

---

### Post by sirdilznik on 2007-11-24
One way to maximize resources is by running a game in it's own separate Xserver by using the xinit command.  This way the game is not bogged down by the desktop environment.  [Here](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+extra+XServer) is a howto on running various apps through xinit.

---

### Post by Burkey on 2007-11-25
Thanks for the replies about the beta driver!  I am going to give it a shot tonight when I get home from work.. or I may even download it and whack it onto my work laptop at lunchtime :-D

Cant play wow though due to firewall dammit.

---

### Post by Burkey on 2007-11-25
quick question.. do I need to blacklist any drivers or remove the nvidia drivers Ubuntu put on before running this installer or is it safe to just instal over the top?

Sorry, I have only ever installed ATi binary drivers so I am not sure of what to look for on these

---

### Post by Sockerdrickan on 2007-11-25
And by this driver you mean the one I posted?
In that case:

```

GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start

```

---

### Post by Sockerdrickan on 2007-11-25
And if it works you can save it as a file "how2: install nvidia driver" for later use :)
It has always worked for me. It's my perfect how2!

---

### Post by Burkey on 2007-11-25
Tux0r, thanks for the info.. I pretty much done as you had put down and the driver seems to be in and running, however.. gnome is not happy at all!  I get a lot of dialogs on login and no gnome-panels:

```

GConf Error: Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/UNKNOWN:1.0

```

Hoping someone can identify that and help me out.

---

### Post by Burkey on 2007-11-25
Fixed.. rebooted and gnome told me the settings demon could not start, I noticed update manager had kicked in and wanted to install some gnome-config tools, which I done, restart X and it is good.

Awesome thing is.. my dock is working correctly so I am back to using my 23" LCD instead of the 15" laptop screen.  YAY

---

### Post by Sockerdrickan on 2007-11-26
I am very happy to hear that :D

---

