---
title: "how to make 'desktop edition' look like 'netbook edition'"
date: 2011-09-19
forum: Desktop Environments
---

### Post by jonnyboysmithy on 2011-09-19
At the moment my desktop enviroment looks like the attached picture.

I'm trying to make my desktop enviroment look something like the pictures on this page: [http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d](http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d)

I'm running 11.04

So my question is how can I do this?

---

### Post by Alwimo on 2011-09-19
Log out, and then when you get to where you type in your password, click on where it says "Ubuntu Classic" down the bottom of the screen and select "Ubuntu".

---

### Post by jonnyboysmithy on 2011-09-19
> **Alwimo said:**
> Log out, and then when you get to where you type in your password, click on where it says "Ubuntu Classic" down the bottom of the screen and select "Ubuntu".
 
I just logged out and back in.
I was and still am using ubuntu not ubuntu classic.
Still looks the same..

---

### Post by Alwimo on 2011-09-19
That probably means that your graphics card or drivers aren't quite up to it. First, check System > Administration > Additional Drivers and see if there's anything there for you.
 
Alternatively, install Unity 2D, which is a version of Unity that is more likely to work on your hardware. It can be installed through the software centre, and then you just choose Unity 2D when logging in.

---

### Post by Frogs Hair on 2011-09-19
Take a look at the link .[http://www.omgubuntu.co.uk/2011/05/pre-unity-ubuntu-netbook-launcher-is-resurrected-put-in-a-ppa/](http://www.omgubuntu.co.uk/2011/05/pre-unity-ubuntu-netbook-launcher-is-resurrected-put-in-a-ppa/)

---

### Post by Copper Bezel on 2011-09-19
Frogs Hair, I don't think he's talking about the difference between the old NBR and the current Unity launcher. He doesn't have Unity running and probably doesn't have Compiz running, either.

jonnyboysmithy, try running compiz --replace in a terminal window and copying and pasting any error messages you see here. (After you copy it in, select the text and click the # to put it in a code box.)

Edit: Better yet, follow [_this_]("http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html") guide and let us know your result. Instead of compiz --replace, run

```
/usr/lib/nux/unity_support_test -p --compiz
```

and see what output you get.

---

### Post by jonnyboysmithy on 2011-09-19
> **Frogs Hair said:**
> Take a look at the link .[http://www.omgubuntu.co.uk/2011/05/pre-unity-ubuntu-netbook-launcher-is-resurrected-put-in-a-ppa/](http://www.omgubuntu.co.uk/2011/05/pre-unity-ubuntu-netbook-launcher-is-resurrected-put-in-a-ppa/)
I'll try that!

---

### Post by drawkcab on 2011-09-19
> **Frogs Hair said:**
> Take a look at the link .[http://www.omgubuntu.co.uk/2011/05/pre-unity-ubuntu-netbook-launcher-is-resurrected-put-in-a-ppa/](http://www.omgubuntu.co.uk/2011/05/pre-unity-ubuntu-netbook-launcher-is-resurrected-put-in-a-ppa/)

Good call.  10.04's netbook edition was really great in my opinion.  Unity is, by comparison, a confusing endeavor.  

I would switch back to 10.04 if it weren't for the fact that Linux Mint Debian edition with metacity is just much lighter on the resources than Ubuntu.

I think this Gnome 3/Unity transition is pushing me into the retro grouch category.

---

### Post by jonnyboysmithy on 2011-09-19
> **Copper Bezel said:**
> Frogs Hair, I don't think he's talking about the difference between the old NBR and the current Unity launcher. He doesn't have Unity running and probably doesn't have Compiz running, either.

jonnyboysmithy, try running compiz --replace in a terminal window and copying and pasting any error messages you see here. (After you copy it in, select the text and click the # to put it in a code box.)

Edit: Better yet, follow [_this_]("http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html") guide and let us know your result. Instead of compiz --replace, run

```
/usr/lib/nux/unity_support_test -p --compiz
```and see what output you get.
Seems all good :
```
OpenGL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv25 20091015 x86/MMX/SSE2
OpenGL version string:  1.2 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes

Compiz supported:         yes

```
So what do you guys think?

---

### Post by jonnyboysmithy on 2011-09-19
I ran ```
compiz --replace
``` and the effect that had is exactly what happens when im using my pc and  every so often (maybe 30min-few hours?)it will do exactly what happens if I run that code.


Edit:nevermind, I'll try focus on getting it to look like netbook edition...... :)

---

### Post by Copper Bezel on 2011-09-19
Curious. What effect is that?

Here, paste this into a terminal and hit enter:

```
if [ $(pgrep -c metacity) -gt 0 ]; then
  echo "metacity is running"
elif [ $(pgrep -c compiz) -gt 0 ]; then
  echo "compiz is running"
fi
```
It'll return either "compiz is running" or "metacity is running," and we can identify whether this is a Compiz problem or a Unity one.

Edit: Unity being the interface you're trying to get and Compiz being the window manager and compositor that runs it.

---

### Post by jonnyboysmithy on 2011-09-19
> **Copper Bezel said:**
> Curious. What effect is that?

Here, paste this into a terminal and hit enter:

```
if [ $(pgrep -c metacity) -gt 0 ]; then
  echo "metacity is running"
elif [ $(pgrep -c compiz) -gt 0 ]; then
  echo "compiz is running"
fi
```It'll return either "compiz is running" or "metacity is running," and we can identify whether this is a Compiz problem or a Unity one.

Edit: Unity being the interface you're trying to get and Compiz being the window manager and compositor that runs it.
It says compiz is running.
Edit: sometimes I'll get a gpu lockup, especially if I've been running supertuxkart.
 It'll say "GPU lockup switching to fbcon" and completely freeze..

---

### Post by Copper Bezel on 2011-09-20
Weird. Both parts.

What happens if you run unity --reset ?

Edit: Or if you have compizconfig-settings-manager installed, just try to enable the Ubuntu Unity plugin?

---

### Post by jonnyboysmithy on 2011-09-20
> **Copper Bezel said:**
> Weird. Both parts.

What happens if you run unity --reset ?

Edit: Or if you have compizconfig-settings-manager installed, just try to enable the Ubuntu Unity plugin?
I enabled the Ubuntu Unity Plugin it had a few key binding conflicts other than that it enabled fine.

---

### Post by Copper Bezel on 2011-09-20
So the plugin enabled and Compiz is running, but it didn't give you the netbooky interface?

I think I'm out of my depth, now. = /

---

### Post by Krytarik on 2011-09-20
If I may step in here, please run the below command as well, it will check if your current video hardware/driver setup is capable to also run Unity:
```
/usr/lib/nux/unity_support_test -p
```
Then please post the results.

---

### Post by jonnyboysmithy on 2011-09-20
> **Copper Bezel said:**
> So the plugin enabled and Compiz is running, but it didn't give you the netbooky interface?

I think I'm out of my depth, now. = /
Eh, no it never has. yes compiz is running, and yes, it still looks like the screenshot I attached to the first post. Maybe logout and in?
:) also out of my depth, its why I asked here :)
Edit: I logged out and back in, it still looks the same..

---

### Post by jonnyboysmithy on 2011-09-20
> **Krytarik said:**
> If I may step in here, please run the below command as well, it will check if your current video hardware/driver setup is capable to also run Unity:
```
/usr/lib/nux/unity_support_test -p
```Then please post the results.
Thank you for stepping in! I appreciate the help.
```
enGL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv25 20091015 x86/MMX/SSE2
OpenGL version string:  1.2 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no

``` 'unity supported no' ookkaaay..  maybe thats why it didn't work :biggrin:

---

### Post by Copper Bezel on 2011-09-20
Edit - Scrubbed.

---

### Post by Krytarik on 2011-09-20
Did you already try the proprietary Nvidia driver offered via "System -> Administration -> Additional Drivers"!? Either the "nvidia-current" or the "nvidia-173", if both are offered.

Btw., what video card/chip do you have?

EDIT: Ah, concurrent posts! No, I would only try forcing to run Unity if the video card/chip is blacklisted.

---

### Post by jonnyboysmithy on 2011-09-20
> **Krytarik said:**
> Did you already try the proprietary Nvidia driver offered via "System -> Administration -> Additional Drivers"!? Either the "nvidia-current" or the "nvidia-173", if both are offered.

Btw., what video card/chip do you have?
woaw sorry guys, i dont have the proprietary driver installed. I thought i did!

 I'll activate it now and retry the code you gave me before.
From memory its a Nvidia Ti4200 with 64mb but it'd be better if i checked.
Whats the code to check what card I have?

The proprietary driver is installed now.
I ran the unity compatibility test again the results are:
```
OpenGL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv25 20091015 x86/MMX/SSE2
OpenGL version string:  1.2 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no

```

---

### Post by Copper Bezel on 2011-09-20
Hrng. Well, based on what Krytarik said, it's probably a bad idea to force Unity to start. (The non-proprietary drivers might also explain the weird GPU issues you've been having.)

At this point, I'd go ahead and try installing the package unity-2d. You can still run Compiz for desktop effects in a Unity-2D session, and the interface in Unity 2D is very close to Unity 3D's.

Krytarik, thanks again for stepping in, and sorry about the concurrent post!

---

### Post by jonnyboysmithy on 2011-09-20
Edit: -------

---

### Post by Krytarik on 2011-09-20
> **jonnyboysmithy said:**
> From memory its a Nvidia Ti4200 with 64mb but it'd be better if i checked.
Whats the code to check what card I have?

Coincidentally, I have the same modell if this is indeed the case. :P
So, by this way I would also learn if *my* card is capable to run Unity. :D

To check the general modell of the card/chip, run:
```
lshw -c video
```Result in my case (don't care about the warning message):
```
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: NV25 [GeForce4 Ti 4200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:**01:00.0**
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:11 memory:ee000000-eeffffff memory:f0000000-f7ffffff(prefetchable) memory:ef800000-ef87ffff(prefetchable) memory:ef7e0000-ef7fffff(prefetchable)

```Then, to also check the memory size, take the bus address highlighted in the first output and run a command like this (just learned it):
```
lspci -v -s **01:00.0**
```Result in my case:
```
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)
    Subsystem: Micro-Star International Co., Ltd. Device 8705
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 11
    Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
    Memory at f0000000 (32-bit, prefetchable) [**size=128M**]
    Memory at ef800000 (32-bit, prefetchable) [size=512K]
    [virtual] Expansion ROM at ef7e0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-96, nvidiafb, rivafb, nouveau

```Reg. the still being used "nouveau" driver, run this command to create a new, proper "/etc/X11/xorg.conf" for the proprietary Nvidia driver:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```Then reboot/relogin.

PS: As you can see, it took me a while to put this together, so sorry for the delay. ;-)

---

### Post by jonnyboysmithy on 2011-09-20
Lol we got the same cards!!

```
*-display               
       description: VGA compatible controller
       product: NV25 [GeForce4 Ti 4200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
       resources: irq:16 memory:e8000000-e8ffffff memory:d8000000-dfffffff memory:e0000000-e007ffff memory:e0080000-e009ffff

```

and ```
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3) (prog-if 00 [VGA controller])
    Subsystem: LeadTek Research Inc. WinFast A250 LE TD (Dual VGA/TV-out/DVI)
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    Memory at e0000000 (32-bit, prefetchable) [size=512K]
    [virtual] Expansion ROM at e0080000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb, rivafb

```

I just finished installing unity 2d packages.

Emmm....```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
sudo: nvidia-xconfig: command not found

```

---

### Post by Krytarik on 2011-09-20
Are you sure that the proprietary driver is installed? It should offer the "nvidia-96".

In any case, please check/post the output of:
```
dpkg -l |grep nvidia
```
In my case - Lucid 10.04 - it is:
```
ii  nvidia-173-modaliases                  173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96                              96.43.17-0ubuntu1                               NVIDIA binary Xorg driver, kernel module and
ii  nvidia-96-modaliases                   96.43.17-0ubuntu1                               Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                          0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current-modaliases              195.36.24-0ubuntu1~10.04                        Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-settings                        195.36.08-0ubuntu2                              Tool of configuring the NVIDIA graphics driv

```

---

### Post by jonnyboysmithy on 2011-09-20
the output is ```
ii  nvidia-cg-toolkit                      3.0.0007-0ubuntu1                          Cg Toolkit - GPU Shader Authoring Language
ii  nvidia-common                          0.2.30                                     Find obsolete NVIDIA drivers

``` so i don't think I have the driver installed, see the attached picture.
Additional Drivers thinks I have the Nvidia 3D experimental driver installed.
Soo I need to install the nvidia-96 driver:```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-96 : Depends: xorg-video-abi-8.0 but it is not installable
             Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but it is not going to be installed
E: Broken packages
```

---

### Post by Krytarik on 2011-09-20
> **jonnyboysmithy said:**
> Additional Drivers thinks I have the Nvidia 3D experimental driver installed.
Yeah, that's the "nouveau" driver, not the proprietary one! :D

Seems like the method of how to find appropriate drivers for Nvidia cards/chips has changed since Natty 11.04. Apparently, it isn't based on the "nvidia-XXX-modaliases" packages anymore, and right now I don't know how it works now.

However, you can just install the packages "nvidia-96" and "nvidia-settings" manually:
```
sudo apt-get install nvidia-96 nvidia-settings
```
After that, check if the "/etc/X11/xorg.conf" was generated automatically. If not, run the previously given command to do so.

---

### Post by jonnyboysmithy on 2011-09-20
```
sudo apt-get install nvidia-96 nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-settings is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-96 : Depends: xorg-video-abi-8.0 but it is not installable
             Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but it is not going to be installed
E: Broken packages

```I played some supertuxkart and had a lockup on launching the game, it says something about the experimental nouveau driver being the issue.
Thats that explained! I'd be very happy if I could install the correct driver and everything would function normally.
I'm running unity 2D at the moment without any 'special effects' like window focus or shadow or desktop cube etc...


EDIT: I think I may have found a source: [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8)

---

### Post by jonnyboysmithy on 2011-09-20
right guys, I managed deactivate the nouvea driver and install the .run script.
I booted up and it couldn't find the screen im not sure, it said something about not being able to connect the xserver which didnt make sense to me. 
Anyway I booted in failsafe graphics and made a new config with the code provided in the previous posts.
It hangs on boot now, getting stuck at checking battery state..
Help? :biggrin:

---

### Post by Krytarik on 2011-09-20
> **jonnyboysmithy said:**
> ```
The following packages have unmet dependencies:
 nvidia-96 : Depends: xorg-video-abi-8.0 but it is not installable
             Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but it is not going to be installed
E: Broken packages

```
Yeah, that's true, "xorg-video-abi-8.0" is missing, strangely #-o:

[http://packages.ubuntu.com/natty/nvidia-96](http://packages.ubuntu.com/natty/nvidia-96)

> **jonnyboysmithy said:**
> I think I may have found a source: [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8)
Yeah, that's indeed the source, but, not really surprising, "xorg-video-abi-8.0" here with a broken link, too:

[https://launchpad.net/ubuntu/natty/i386/nvidia-96/96.43.19-0ubuntu8](https://launchpad.net/ubuntu/natty/i386/nvidia-96/96.43.19-0ubuntu8)

I figured that "xorg-video-abi-8.0" is a so-called "[virtual package]("http://www.debian.org/doc/debian-policy/ch-binary.html#s-virtual_pkg")", which is actually provided by "xserver-xorg-core" (and "xserver-xorg-core-udeb"). I learned this by checking the ["nvidia-96" package for Oneiric 11.10]("http://packages.ubuntu.com/oneiric/nvidia-96"), which is not broken.

However, even if we could circumvent the - virtual - dependency issue, which I believe is not only possible (though not with 'apt-get' currently) but also wouldn't break anything 'real', as the missing package is actually provided by "xserver-xorg-core", it would break the package management, and you would end up with not being able to install/remove/upgrade anything!

So, for now (bug report [here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/807158"), you should enlist yourself there) the only sensible option is to install the driver manually with the installer from Nvidia's website, in fact the worst possible option, for a number of reasons. - Which is what you did right now while I was looking into the issue and the available options. And failed already. --- I'll get to this new issue in my next post! (Sorry, Copper, should have added this before!)

---

### Post by Copper Bezel on 2011-09-20
If it's hanging before it fully boots, is there any way to revert the configuration from a LiveCD, then get back to the failsafe mode? I mean, just to get back to the previous functionality?

---

### Post by Krytarik on 2011-09-20
Ok then, to your issue with the manually installed driver now.

As we have seen in the output of the failed installation of "nvidia-96" with 'apt-get', the package "xserver-xorg-core" seems to be missing. So, make sure it is installed:

1. At the boot menu choose "recovery mode", then "netroot". You may have to press the Shift key to make the menu appear.

2. At the console - you will already be root - run:
```
apt-get install --reinstall xserver-xorg-core
```
3. Reboot by pressing Ctrl+Alt+Delete

Then see if this fixed it.

---

### Post by jonnyboysmithy on 2011-09-20
if I drop to root shell and startx I get fatal error no screen found.
I tryd to reconfigure graphics.. but still no screen found.

---

### Post by Krytarik on 2011-09-20
> **jonnyboysmithy said:**
> if I drop to root shell and startx I get fatal error no screen found.
I tryd to reconfigure graphics.. but still no screen found.
Could you please follow my instructions! It's time consuming enough already. Sorry!

---

### Post by jonnyboysmithy on 2011-09-20
> **Krytarik said:**
> Could you please follow my instructions! It's time consuming enough already. Sorry!
aye! my mistake sorry my excuses.

I didnt refresh the page or see your last post. 

Right Ill do that.```
apt-get install --reinstall xserver-xorg-core
```

---

### Post by jonnyboysmithy on 2011-09-20
Yup done that reinstalled xserver-xorg-core

---

### Post by jonnyboysmithy on 2011-09-20
Don't worry too much about my current system, Ill just do a clean install some time.

---

### Post by Krytarik on 2011-09-20
> **jonnyboysmithy said:**
> Yup done that reinstalled xserver-xorg-core
And? Can you boot into your desktop now?

---

### Post by jonnyboysmithy on 2011-09-20
> **Krytarik said:**
> And? Can you boot into your desktop now?
No, still hangs on boot
If I go ctrl+alt+F2 then login and type startx I get 
exec: 3: /usr/bin/x: not found
xinit: giving up
xinit:unable to connect to X server: Connection refused
xinit: server error

My first thoughts were xserver wasn't installed but I'm sure it is.

---

### Post by Krytarik on 2011-09-20
Sure that the driver was installed correctly?

Try running the installer again, from the recovery console.

---

### Post by jonnyboysmithy on 2011-09-20
This is the first time I've used launchpad, I've marked 'this bug affects me' Is there anything else I should do?

---

### Post by jonnyboysmithy on 2011-09-20
> **Krytarik said:**
> Sure that the driver was installed correctly?

Try running the installer again, from the recovery console.
I have run apt-get install --reinstall xserver-xorg-core and am absolutely positive that I have done so correctly. sorry but still exactly the same thing as before.

Edit: you mean the nvidia driver. right..

---

### Post by Krytarik on 2011-09-20
> **jonnyboysmithy said:**
> This is the first time I've used launchpad, I've marked 'this bug affects me' Is there anything else I should do?
- You could leave a comment, as the last comment (as well as the initial filing) was on July 7th. However, your 'affects me, too' automatically triggered the status to change to "Confirmed". Maybe this is enough to bring it up again. Decide yourself.

- You should subscribe to the bug report by clicking on "not directly subscribed to this bug's notifications" on the right side.

---

### Post by Krytarik on 2011-09-20
> **jonnyboysmithy said:**
> 
Edit: you mean the nvidia driver. right..
Yep. ;-)

---

### Post by jonnyboysmithy on 2011-09-20
> **Krytarik said:**
> Yep. ;-)
The installer wasn't happy and unistalled itself ill attach some pictures, not sure if you can read the text

---

### Post by Krytarik on 2011-09-20
> **jonnyboysmithy said:**
> The installer wasn't happy and unistalled itself ill attach some pictures, not sure if you can read the text
Yeah, I can read the text just fine. ;-)

Following this guide now:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

1. Boot into recovery console.

2. Remove "nvidia-settings" again:
```
sudo apt-get purge nvidia-settings
```3. Make sure "build-essential" and kernel headers are installed
```
sudo apt-get install --reinstall build-essential linux-headers-`uname -r`
```4. Run the installer again (report errors if any).

5. Reboot.

---

### Post by jonnyboysmithy on 2011-09-20
> **Krytarik said:**
> Yeah, I can read the text just fine. ;-)

Following this guide now:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

1. Boot into recovery console.

2. Remove "nvidia-settings" again:
```
sudo apt-get purge nvidia-settings
```3. Make sure "build-essential" and kernel headers are installed
```
sudo apt-get install --reinstall build-essential linux-headers-`uname -r`
```4. Run the installer again (report errors if any).

5. Reboot.
I did  apt-get install xserver-xorg reconfigured the graphics to the default, and it works, its not pretty at 1024x768.
Only just read your post now, I'll try install the nvidia driver again. :)

Edit: I ran the installer again and the 'noscreen found' has returned.
It has the same errors as in the photos earlier. 
Maybe I'm not using the correct installer?
I downloaded this [http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-96/nvidia-graphics-drivers-96_96.43.19.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-96/nvidia-graphics-drivers-96_96.43.19.orig.tar.gz) extracted and ran the .run file.
What the other files in there are for? configs?

Edit: just had a look at the nvidiamanual, I'll try that when I've got time.

---

### Post by Krytarik on 2011-09-20
> **jonnyboysmithy said:**
> Edit: I ran the installer again and the 'noscreen found' has returned.
It has the same errors as in the photos earlier. 
Maybe I'm not using the correct installer?
I downloaded this [http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-96/nvidia-graphics-drivers-96_96.43.19.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-96/nvidia-graphics-drivers-96_96.43.19.orig.tar.gz) extracted and ran the .run file.
What the other files in there are for? configs?
Did you remove "nvidia-settings" and installed the possibly missing packages?

And yes, although the installers (for 32 and 64 bit, did you take this into account?) included in those package seem to be fine, too, better download the driver directly from the website of Nvidia, choose "Legacy" as the "Product Type" there.

Btw., I guess you have a 32-bit system, right?

---

### Post by jonnyboysmithy on 2011-09-22
> **Krytarik said:**
> Did you remove "nvidia-settings" and installed the possibly missing packages?

And yes, although the installers (for 32 and 64 bit, did you take this into account?) included in those package seem to be fine, too, better download the driver directly from the website of Nvidia, choose "Legacy" as the "Product Type" there.

Btw., I guess you have a 32-bit system, right?
Yup I got 32bit system
Today I upgraded to ubuntu 11.10 and guess what!?!!! when I installed the proprietary driver (nvidia-96 from Additional Driver) it installed like a charm. Soo happy with it :biggrin:  ):P
Things like supertuxkart and minecraft run perfect! even on fullscreen where previously it would result in a instant gpu lockup.
atm I'm running unity 2D with no effects but no effects is definitely worth it.
Thank you very much for your help!

---

### Post by Krytarik on 2011-09-22
Great that it worked out this way! :D
Even though Oneiric is still in Beta.

And yes, Oneiric's Unity 2D is pretty near the original!
But does the 'real' one work too, with your current setup? As you know, I have the same, so curious, obviously. :p

Greetings.

---

### Post by jonnyboysmithy on 2011-09-22
At the logging I have 2 options; ubuntu and ubuntu 2D
both ubuntu and ubuntu 2D both run fine with no effects whatsoever. I've got 
compizconfig-settings-manager installed and wobly windows and desktop cube enabled, but I still don't have any effects.

---

### Post by jonnyboysmithy on 2011-09-22
Dash takes about 3seconds to open, bit long but oh well

---

### Post by Krytarik on 2011-09-22
> **jonnyboysmithy said:**
> At the logging I have 2 options; ubuntu and ubuntu 2D
both ubuntu and ubuntu 2D both run fine with no effects whatsoever.
So, it seems you are eventually redirected to Unity 2D if you choose "Ubuntu", because the system figures that your current setup isn't capable to run the original Unity.

You can check if Unity 2D is actually running by opening the System Monitor and checking if there are processes running with "unity-2d" in their names.

---

### Post by jonnyboysmithy on 2011-09-22
> **Krytarik said:**
> So, it seems you are eventually redirected to Unity 2D if you choose "Ubuntu", because the system figures that your current setup isn't capable to run the original Unity.

You can check if Unity 2D is actually running by opening the System Monitor and checking if there are processes running with "unity-2d" in their names.

Yup unity-2D launcher and a bunch of other 2D stuff.
Definetely running 2D, if its not running effects its probably because its not capable.
There wouldn't be any point forcing it to?

---

### Post by Krytarik on 2011-09-22
> **jonnyboysmithy said:**
> There wouldn't be any point forcing it to?
Well, we could try, but it also doesn't seem like the "nvidia-96" driver is running.
Please check that with the earlier used commands.

---

### Post by jonnyboysmithy on 2011-09-22
```
dpkg -l |grep nvidia
ii  nvidia-96                              96.43.20-0ubuntu4                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-96-updates                      96.43.20-0ubuntu3                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                          1:0.2.35                                Find obsolete NVIDIA drivers
ii  nvidia-settings                        280.13-0ubuntu2                         Tool of configuring the NVIDIA graphics driver
ii  nvidia-settings-updates                280.13-0ubuntu1                         Tool of configuring the NVIDIA graphics driver

```
This means it is using the nvidia-96 driver?

---

### Post by Krytarik on 2011-09-22
> **jonnyboysmithy said:**
> This means it is using the nvidia-96 driver?
Nope, although this already looks better than before, but I was referring to this:

[http://ubuntuforums.org/showthread.php?p=11267899#post11267899](http://ubuntuforums.org/showthread.php?p=11267899#post11267899)

---

### Post by jonnyboysmithy on 2011-09-22
```
 /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce4 Ti 4200/AGP/SSE2
OpenGL version string:  1.5.8 NVIDIA 96.43.20

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    no
GL version is 1.4+:       yes

Unity 3D supported:       no

```I think this means its using the NVIDIA 96.43.20 driver
Is this correct?

---

### Post by Krytarik on 2011-09-22
Yeah, that one was even better! ;-)

This way we also see that using the "nvidia-96" doesn't make any difference to the "nouveau" driver, you used before, sadly! :(

---

### Post by jonnyboysmithy on 2011-09-22
> **Krytarik said:**
> Yeah, that one was even better! ;-)

This way we also see that using the "nvidia-96" doesn't make any difference to the "nouveau" driver, you used before, sadly! :(
It is better in the way that I dont get a instant gpulockup like I used to when I fullscreened it
and minecraft doesnt just close like it used to whenever I broke a block :)

---

### Post by Krytarik on 2011-09-22
> **jonnyboysmithy said:**
> It is better in the way that I dont get a instant gpulockup like I used to when I fullscreened it
and minecraft doesnt just close like it used to whenever I broke a block :)
At least, yeah! :p

So, have fun with finally enjoying Minecraft! :D

---

