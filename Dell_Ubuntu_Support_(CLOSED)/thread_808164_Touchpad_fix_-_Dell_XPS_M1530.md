---
title: "Touchpad fix - Dell XPS M1530"
date: 2008-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aaBlueDragon on 2008-05-26
Let's make it clear once and for all.
for all of you XPS M1530 Users who experience Touchpad Slowliness/Gliches
even though they have added i8042.nomux=1:

you must add i8042.nomux=1 in the kernel line before where it says splash.
after the change, the line should look something like this:
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3fced842-2be9-413d-802e-4da2e19ccdc1 or quiet i8042.nomux=1 splash
or you can also look at the screenshot I have attached to this post.
this will surely fix the speed and craziness of your touchpad.

---

### Post by LK_gandalf_ on 2008-05-26
Same here: [http://ubuntuforums.org/showthread.php?t=777950](http://ubuntuforums.org/showthread.php?t=777950)
:KS

---

### Post by MikeyMike01 on 2008-05-30
Is there any way to get this into the install .iso, so I can actually install Ubuntu?

---

### Post by hackel on 2008-06-08
> **aaBlueDragon said:**
> Let's make it clear once and for all.
you must add i8042.nomux=1 in the kernel line before where it says splash.


This is just wrong.  The order of linux kernel options does not matter.  I have been running with
# defoptions=splash i8042.nomux=1
since I got my M1530 and it works fine.  If you still are experiencing touchpad issues, I suggest tweaking your synaptics (alps) configuration in xorg.conf.

---

### Post by jespdj on 2008-06-09
> **MikeyMike01 said:**
> Is there any way to get this into the install .iso, so I can actually install Ubuntu?
Workaround: Attach an USB mouse while installing Ubuntu.

Indeed, the order of the kernel parameters doesn't matter. It works fine on my M1530 with i8042.nomux=1 at the end of the kernel line.

---

### Post by blierp on 2008-06-10
well, my touchpad does work again after applying this 'fix' but it's so slow it's hardly usable. Changing the options in xorg.conf doesnt change anything either and i can't enable SHMConfig for some reason.
Not that it's a big problem, i use an external mouse most of the time, but it's annoying.

---

### Post by Agrajag27 on 2008-06-21
Same issue for me except that it WAS working for ONE session. My gripe was that the border was extremely tight against the edge of the pad but that I could live with. Now I'm back to gsynaptics refusing to load even though everything looks perfectly fine setup wise.

---

### Post by fragos on 2008-06-21
The acceleration and speed of the touchpad is by default slower than I like. The following section from /etc/X11/xorg.conf fixed it for me. The AccelFactor, MaxSpeed and MinSpeed options are the ones to add and adjust.

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
        Option      "MinSpeed" "0.5"
        Option      "MaxSpeed" "0.8"
        Option      "AccelFactor" "0.07"
EndSection

---

### Post by Agrajag27 on 2008-06-21
I just want to get back to where the scrolling works for me as it did on ONE boot. This is one of the reasons I'm not sold on Linux/Ubuntu overall. These sorts of issues seem to be very much the norm in a product that sells itself as being so free of these kinds of things.

Once that is resolve then I can focus on the speed issue.

---

### Post by toozler on 2008-08-20
Same issue here, crazy touchpad, fixed adding the "nomux" on GRUB, but still it's quite slow, specially because i'm on 1650x1050 screen resolution, so to move the pointer to one side to the other, takes me 4 or 5 swipes on the entire touchpad area.

I'm not on my computer right now, but I found these tips for Gentoo that may work to enable de vertical scrolling: [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

Maybe addind the following lines to xorg.conf may help. Let me know if it works and how it works.

#     Option        "VertEdgeScroll"    "true"  
#     Option        "HorizEdgeScroll"    "true"  
#     Option        "VertScrollDelta"    "100"  
#     Option        "HorizScrollDelta"    "100"

---

### Post by Agrajag27 on 2008-08-20
I'm at a point where it works about 40% of the time. It's so frustrating. Wish we could find out what hoses it the other 60% of the time.

---

### Post by toozler on 2008-08-22
Well, adding the parameters bellow on xorg.conf did work for me. But I set up higher values for both MinSpeed and MaxSpeed (1 and 1.2 respectively). What's weird is that changes won't take effect by restarting X (ctrl+alt+backspace), I had to reboot everytime I tried a different number. 

Option "MinSpeed" "0.5"
Option "MaxSpeed" "0.8"
Option "AccelFactor" "0.07"

As of the vertical and horizontal scrolling, it did work, but not properly. Scrolling speed was to slow and it would not always work, as if I needed to apply the correct pressure at an exact line and at an exact speed. I did check **man synaptics** to tune those parameters but without any sucess. There's also an VertTwoFingerScroll parameter. That would be sweet if it worked.

---

### Post by astra2000 on 2008-09-12
> **aaBlueDragon said:**
> Let's make it clear once and for all.
for all of you XPS M1530 Users who experience Touchpad Slowliness/Gliches
even though they have added i8042.nomux=1:

you must add i8042.nomux=1 in the kernel line before where it says splash.
after the change, the line should look something like this:
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3fced842-2be9-413d-802e-4da2e19ccdc1 or quiet i8042.nomux=1 splash
or you can also look at the screenshot I have attached to this post.
this will surely fix the speed and craziness of your touchpad.


Tnks dude.. Works fine :)

---

### Post by badwaik.jai on 2008-09-15
Hi,
I think the following link should work.
I haven't tried it myself.
But i trust that guy.
So if you want you can try it.

[http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/](http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/)


Waiting for ur reply

---

### Post by fragos on 2008-09-15
It's an excellent piece and may represent a solution for you but a lot has changes in 3 years and some of those changes may have impacted touchpads. For example, I have a USB touchpad with a chipset from Cirque Corp. It is automatically detected and full featured without any mention in xorg.conf. Never would have been in the past. The touchpad on my Dell laptop does use Synaptics driver and although the GUI Preferences allowed me to disable pad taps I still had to adjust the acceleration and sensitivity in xorg.conf.

---

### Post by Darrell Lawrence on 2008-09-15
> **aaBlueDragon said:**
> Let's make it clear once and for all.
for all of you XPS M1530 Users who experience Touchpad Slowliness/Gliches
even though they have added i8042.nomux=1:

you must add i8042.nomux=1 in the kernel line before where it says splash.
after the change, the line should look something like this:
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3fced842-2be9-413d-802e-4da2e19ccdc1 or quiet i8042.nomux=1 splash
or you can also look at the screenshot I have attached to this post.
this will surely fix the speed and craziness of your touchpad.

Thanks for this post BlueDragon. Just some additional info, If you are thinking about purchasing a Dell XPS M1530 preloaded with Ubuntu 8.04, Dell has the i8042.nomux=1 setup exactly as shown in BlueDragon's attachment.

Darrell

---

### Post by hiyaegagagm1 on 2008-09-16
[size=2][font=Times New Roman][size=3]hi,everyone,need guitar effects pedals? take a look at [guitar effects pedals shop](http://www.myguitarpedals.com/), may be u will find ur favorite...This is an excellent thread!**The good:** The optional Bowers and Wilkins audio system in the 2009 Jaguar XF offers exceptional separation and clarity for music playback. We like the interior materials in the XF, along with the tech touches. The engine offers a good amount of power for the car while delivering acceptable fuel economy.[runescape gold](http://www.runescapecoin.net/) **The bad:** The touch-screen interface for audio, navigation, and other car systems is too slow, and it is not well organized. The navigation system is unremarkable.[age of conan gold](http://www.buy-age-of-conan-gold.com/)**The bottom line:** The 2009 Jaguar XF offers a lot of luxury for the money, with many unique high-tech touches and an exceptional audio system. But it doesn't always deliver on its apparent promise, [color=#008000][age of conan money](http://www.ageofconanmoney.net/) [/color]with a run-of-the-mill suspension and navigation system.[runescape money](http://www.runescapemoney.ws/). [/size][/font][/size]

---

### Post by kingaaronj on 2008-09-26
Just a small update.  I had the i8042.noloop and splash items reversed in GRUB and I was still having issues with disabling tap-clicking.  I changed them to the way listed in Bluedragon's screencap and everything works fine now.

---

### Post by kingaaronj on 2008-09-30
I take it back.  With this fix my trackpad is fully detected only 1/2 of the time!  This is really annoying.  So what's happening is, on boot, 1/2 the time Ubuntu won't detect that a trackpad is present.  I can use it, but I can't access the menu for trackpads under preferences - mouse.  This means I can't disable tap-clicking!  Anyone have any ideas?

---

### Post by kingaaronj on 2008-10-03
I just thought I'd point out that I am on firmware version A09 (the latest from Dell).  Sometimes my dell will boot and it will fully detect the ALPS touchpad as the device and other times it will come up as N: Name="Macintosh mouse button emulation"

When it detects the ALPS properly, everything works great.  When it doesn't I can't scroll or disable touch-clicking.  Is there a modification to my xorg.conf that I can make to fix this?

---

### Post by fragos on 2008-10-03
> **kingaaronj said:**
> I just thought I'd point out that I am on firmware version A09 (the latest from Dell).  Sometimes my dell will boot and it will fully detect the ALPS touchpad as the device and other times it will come up as N: Name="Macintosh mouse button emulation"

When it detects the ALPS properly, everything works great.  When it doesn't I can't scroll or disable touch-clicking.  Is there a modification to my xorg.conf that I can make to fix this?

You should report this bug or add to an existing report. The details you've uncovered well be helpfull in finding and fixing the problem.

---

### Post by ThinkDifferenter on 2008-10-08
I have a Dell XPS m1530, and a solution to most of the scrolling issues, SHMConfig issues, and synaptics driver issues I've had.

I beat my brains out for weeks about this. The touchpad scrolling only worked half of the time. I figured out that it was because the synaptics driver wasn't being loaded correctly, so other things I had attached to SHMConfig, such as no tapping during typing, didn't work either. After reading one particular bug report, I figured out that the psmouse module was being loaded before the synaptics driver, which meant it was overtaking the mouse function. Many people experience this after connecting a USB mouse to their laptop. That's where I went wrong too. After that, things went wrong. Unfortunately, the fix didn't seem to apply to Hardy, since it involved commenting out lines in a file that doesn't exist: rc.modules. So how does one stop Ubuntu from loading the psmouse module before the synaptics drivers?

Believe me, I understand your pain. It's extremely frustrating to only have your mouse working half of the time. For anyone who tries this and it doesn't work, I'm sorry. This worked on my computer, and there is no guarantee that it will work on yours.

First, I blacklisted the psmouse module by making a file in /etc/modprobe.d. I called mine touchpad, but the way I understand it, you can call it anything you want. Running an LS will show that there are blacklists in this folder. We're going to blacklist the psmouse module at boot up.

```
#cd /etc/modprobe.d
#sudo gedit touchpad
```

with the new file open type one line:

**blacklist psmouse**

Save and exit. This will keep the psmouse module from loading before the synaptics drivers. Now your touchpad will have its full functionality. But be careful and hope your power doesn't fail, because without this module your touchpad won't work at all. So you need to load it with a command that runs after boot. Fortunately Ubuntu has created a nifty device for such things called rc.local. After making sure your rc.local file is executable, you need to add modprobe psmouse to it before the exit 0 line.

```
#cd /etc
#ls -lah rc.local
-rwxr-xr-x 1 root root 306 2008-04-22 10:49 rc.local
#sudo gedit rc.local
```

When your done it should look something like:

[b]modprobe psmouse
exit 0[/b]


You're done! Reboot and see if your touchpad scroll or other things are working. If you have SHMConfig in your xorg.conf, check to see if it's also enabled. I did this by testing my no tap during typing. SUCCESS!! So far my touchpad has had full functionality. I haven't rebooted a bunch of times, but so far, it seems to load normally each time.

If this works for you, let us know. If people know it's working, they're apt to try it. It might work for a lot of other people too. If you have a different setup and it works for you, also say something. I have no idea if this is Dell specific or Ubuntu specific or what. Also, it could just be my specific computer. If it doesn't work, oh well, but at least we exhausted THAT option :)

---

### Post by 4Play on 2008-10-12
I have a Dell XPS M1530 also, but the above solution did not work for me, I reboobted three times to see if the changes would kick in, but the touchpad drivers failed to load each and every time.

here is my xorg.conf:

> Section "InputDevice"
    	Identifier     "Synaptics Touchpad"
   	Driver		"synaptics"
	Option 		"SHMConfig" 		"true"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option 		"VertEdgeScroll" 	"true"
	Option 		"HorizEdgeScroll" 	"true"
	Option 		"VertScrollDelta" 	"100"
	Option 		"HorizScrollDelta" 	"100"
	Option 		"MinSpeed" 		"0.8"
	Option 		"MaxSpeed" 		"1.2"
	Option 		"AccelFactor" 		"0.07"
EndSection

I changed the nomux boot option to before the "splash" but the damn thing still refuses to work 90% of the time.

update: to get it to work again I had to chage my xorg.conf, commenting out everything below the "Protocol" line, this seemed to load the touchpad driver (on reboot) but i find it curious that my /proc/bus/inpud/devices has a :
> I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3


where I expected to find the synaptics entry.....

---

### Post by ThinkDifferenter on 2008-10-12
Here are the relevant parts of my xorg:

Section "ServerLayout"
   Identifier     "Default Layout"
   Screen       0 "Screen0" 0 0
   Screen       1 "Screen1" RightOf RightOf
   Input Device   "Synaptics Touchpad"
EndSection

Section "InputDevice"
   Identifier     "Synaptics Touchpad"
   Driver         "synaptics"
   Option         "SendCoreEvents" "true"
   Option         "Device" "/dev/psaux"
   Option         "Protocol" "auto-dev"
   Option         "HorizEdgeScroll" "0"
   Option         "SHMConfig" "on"
EndSection


As you can see, I don't have a lot of crap under the touchpad section. I found that after the touchpad driver loaded correctly, most things worked by themselves. Ubuntu has a pretty good auto-detect system, and it can function without much of an xorg at all. I've seen it work with almost no xorg config whatsoever, although using video drivers is extremely hard this way, so I don't suggest trying it :-P

Anyway, I'm sorry it didn't work for you. I might add that this fix is for a laptop that doesn't still have a USB mouse attached. I've found that the people still trying to use both at once are still having problems. If that's what's happening to you, then I'm sorry I can't help :(

I did this whole thing because I knew mine would be fixed if i did:

```
#sudo rmmod psmouse && modprobe psmouse
```

and then restarted X with ctrl alt delete. My touchpad worked every time when I did that, so I knew that blacklisting the psmouse might be the answer.

For anyone else, you might want to try this first to see if yours is compatible with my fix, and if that doesn't work, then I doubt that fix will help you, but you can try it anyway :-P

---

### Post by fragos on 2008-10-12
I've a 1420n that I installed a strait fom Ubuntu 8.04 on. The touch pad worked but needed some adustments in sensitivity. I disabled taps in the mouse preferences and made the following changes in xorg:

        Option      "HorizScrollDelta" "0"
        Option      "MinSpeed" "0.5"
        Option      "MaxSpeed" "0.8"
        Option      "AccelFactor" "0.07"

That tuned the pad the way I wanted it. I occasionally use an RF USB mouse as well and they don't interfere with each other.

On my DIY assembled desktop with 8.04 I have three cursor control devices -- wired USB mouse, wired USB touchpad and a Wacom USB tablet. This touchpad functions fully without any mention of Synaptics in my xorg. All three work interchangably although on occasion the tablet will cease working correctly until I reboot. Lsusb reports the unconfigured but working touchpad as 0488:0020 Cirque Corp. I don't know if any of this helps you directly. I also used both of these setups in Ubuntu 7.10 and they worked then as well although I do recall using a Synaptics xorg.conf section in a past release with my USB touchpad.

---

### Post by teody.cue on 2008-11-17
> **ThinkDifferenter said:**
> I have a Dell XPS m1530, and a solution to most of the scrolling issues, SHMConfig issues, and synaptics driver issues I've had.

I beat my brains out for weeks about this. The touchpad scrolling only worked half of the time. I figured out that it was because the synaptics driver wasn't being loaded correctly, so other things I had attached to SHMConfig, such as no tapping during typing, didn't work either. After reading one particular bug report, I figured out that the psmouse module was being loaded before the synaptics driver, which meant it was overtaking the mouse function. Many people experience this after connecting a USB mouse to their laptop. That's where I went wrong too. After that, things went wrong. Unfortunately, the fix didn't seem to apply to Hardy, since it involved commenting out lines in a file that doesn't exist: rc.modules. So how does one stop Ubuntu from loading the psmouse module before the synaptics drivers?

Believe me, I understand your pain. It's extremely frustrating to only have your mouse working half of the time. For anyone who tries this and it doesn't work, I'm sorry. This worked on my computer, and there is no guarantee that it will work on yours.

First, I blacklisted the psmouse module by making a file in /etc/modprobe.d. I called mine touchpad, but the way I understand it, you can call it anything you want. Running an LS will show that there are blacklists in this folder. We're going to blacklist the psmouse module at boot up.

```
#cd /etc/modprobe.d
#sudo gedit touchpad
```

with the new file open type one line:

**blacklist psmouse**

Save and exit. This will keep the psmouse module from loading before the synaptics drivers. Now your touchpad will have its full functionality. But be careful and hope your power doesn't fail, because without this module your touchpad won't work at all. So you need to load it with a command that runs after boot. Fortunately Ubuntu has created a nifty device for such things called rc.local. After making sure your rc.local file is executable, you need to add modprobe psmouse to it before the exit 0 line.

```
#cd /etc
#ls -lah rc.local
-rwxr-xr-x 1 root root 306 2008-04-22 10:49 rc.local
#sudo gedit rc.local
```

When your done it should look something like:

[b]modprobe psmouse
exit 0[/b]


You're done! Reboot and see if your touchpad scroll or other things are working. If you have SHMConfig in your xorg.conf, check to see if it's also enabled. I did this by testing my no tap during typing. SUCCESS!! So far my touchpad has had full functionality. I haven't rebooted a bunch of times, but so far, it seems to load normally each time.

If this works for you, let us know. If people know it's working, they're apt to try it. It might work for a lot of other people too. If you have a different setup and it works for you, also say something. I have no idea if this is Dell specific or Ubuntu specific or what. Also, it could just be my specific computer. If it doesn't work, oh well, but at least we exhausted THAT option :)
Took me a whole day trying to figure out why my other tools such as gsynaptics and the default synaptic driver for the Mouse menu cannot access my touchpad all the time. I only got it to work like 10% of the time.

Everything is working now thanks to your post. We have the same machine by the way, so this is the perfect solution. :) Many thanks!

---

### Post by themagicmanfromtrent on 2009-02-10
fantastic thanks!

---

### Post by arjmage on 2010-01-31
> **ThinkDifferenter said:**
> I have a Dell XPS m1530, and a solution to most of the scrolling issues, SHMConfig issues, and synaptics driver issues I've had.

If this works for you, let us know. If people know it's working, they're apt to try it. It might work for a lot of other people too. If you have a different setup and it works for you, also say something. I have no idea if this is Dell specific or Ubuntu specific or what. Also, it could just be my specific computer. If it doesn't work, oh well, but at least we exhausted THAT option :)


Good deductions there!

I tried this on my Dell XPS M1210 and got positive results! Touchpad's scrolling and speeds were being recaltritant, but now they are well under control. 

My touchpad was working perfectly fine in the original in:-
stallation of Ubuntu 9.04 (jaunty) and then I upgraded to the woeful 9.10 (karmic) and only then did I come to realize the amount of trouble other ubuntu versions have given touchpads (and other stuff).

Hope Ubuntu's next releases regain the magic of their prime releases.


Thanks for the tip ThinkDifferenter! :D

---

### Post by fragos on 2010-01-31
I had no trouble upgrading my Dell 1420n from 9.04 to 9.10. I had been using gsynaptics and it was upgraded for me. I see there is now a replacement for gsynaptics called gpointing-device-settings.

---

