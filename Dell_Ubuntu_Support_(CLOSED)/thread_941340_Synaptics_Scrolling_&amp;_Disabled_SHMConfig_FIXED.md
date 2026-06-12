---
title: "Synaptics Scrolling &amp; Disabled SHMConfig FIXED"
date: 2008-10-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ThinkDifferenter on 2008-10-08
I posted this in a response to another thread, but I realized it might not reach the audience it needs from the OP, since it's only mildly related, so I'll post it again in a new topic, more of a howto than anything.

NOTE: THIS IS WHAT WORKED ON MY DELL LAPTOP RUNNING HARDY HERON. ANYTHING YOU TRY IS AT YOUR OWN RISK.

Although I think this could be a general fix for the problem, I see it pop up in Dells most frequently, and I have a Dell XPS m1530, so that's why it's in the Dell section.

I beat my brains out for weeks about this. The touchpad scrolling only worked half of the time. I figured out that it was because the synaptics driver wasn't being loaded correctly, so other things I had attached to SHMConfig, such as no tapping during typing, didn't work either. After reading one particular bug report, I figured out that the psmouse module was being loaded before the synaptics driver, which meant it was overtaking the mouse function. Many people experience this after connecting a USB mouse to their laptop. That's where I went wrong too. Before that, everything worked. After that, things went completely downhill. Unfortunately, the fix didn't seem to apply to Hardy, since it involved commenting out lines in a file that doesn't exist: rc.modules. So how does one stop Ubuntu from loading the psmouse module before the synaptics drivers?

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

If this works for you, let us know. If people know it's working, they're apt to try it. It might work for a lot of other people too. If you have a different setup and it works for you, also say something. I have no idea if this is Dell specific or Ubuntu specific or what. Also, it could just be my specific computer. If it doesn't work, oh well, but at least we exhausted THAT option :D

---

### Post by jhansonxi on 2008-10-08
I think I found an easier method.  See **[my comment]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/209949/comments/12")** for Bug #209949.

---

### Post by ThinkDifferenter on 2008-10-08
I think your problem is something else entirely. I don't have another mouse connected when I lose functionality. Mine didn't work even by itself. I have tried reconfiguring the xorg.conf a million different ways. The problem is, if the synaptics driver isn't being loaded correctly, NOTHING in the xorg.conf under Synaptics Touchpad is going to do a damn thing, because it's not even reading that part of the file, since it doesn't have the driver loaded correctly, and can't even recognize the touchpad properly. Having Option "CorePointer" enabled in the touchpad section doesn't mean anything in this case, since X is skipping that part of xorg.conf entirely.

See [THIS POST]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/209949/comments/10") for another explanation of what's going wrong. I think the problem they're having is that they don't have SHMConfig at all, not just when another mouse is being used, and in the specific case that I had, and that I saw a lot of other people having, it worked some boots, and some boots, there was nothing. That's what I keep seeing over and over and over, along with the intermittent scrolling, and it's what I kept experiencing over and over. Either nothing works, or they all work. If it was really a problem in the xorg, it would NEVER work, and the problem wouldn't be random.

---

### Post by snickie on 2008-12-04
I've been struggling with the problem of not beeing able to disable my touchpad on my Dell XPS M1530. The blame is of course Dell's cause they didn't make an option in the BIOS to disable the touchpad. My box works perfectly well in Windows Vista but when booting into Kubuntu (8.04) sometimes it was impossible to disable the touchpad i.e. I got the message of SHMConfig not in memory (or something like that). The annoyance was that it worked sometimes. When I followed your tips of not loading psmouse until just before login, it suddenly worked. It has to be some bug in the kernel if load order does matter in this way!

Anyhow, your thoughts about the load order of modules seem to have fixed it for me.

Many thanks!
snickie

---

### Post by Chili.willy on 2009-01-20
I was battling the "SHMConfig Disabled?" error too.  It wouldn't go away until I added a line to xorg.conf right after the driver specification. Now my touchpad section looks like this:
```
Section "InputDevice"
        Identifier      "SynPS/2 Synaptics TouchPad"
        Driver          "synaptics"
        Option          "CorePointer"
        Option          "Device"              "/dev/psaux"
        Option          "Protocol"            "auto-dev" 
        Option          "SHMConfig"           "true" 
        Option          "MaxTapTime"          "0"
EndSection
```
That _CorePointer_ made the difference!  I had also moved this section above all the other InputDevice sections, but now I don't know if that matters or not. 

It is so great not to have that unwanted tap feature! It might be a good thing if the hardware were less sensitive, but on this Thinkpad it was horrible.

BTW this is with Debian Lenny, but *ahem* Debian is just another 'buntu flavor, right?

---

### Post by CWayne on 2009-02-08
> **Chili.willy said:**
> I was battling the "SHMConfig Disabled?" error too.  It wouldn't go away until I added a line to xorg.conf right after the driver specification. Now my touchpad section looks like this:
```
Section "InputDevice"
        Identifier      "SynPS/2 Synaptics TouchPad"
        Driver          "synaptics"
        Option          "CorePointer"
        Option          "Device"              "/dev/psaux"
        Option          "Protocol"            "auto-dev" 
        Option          "SHMConfig"           "true" 
        Option          "MaxTapTime"          "0"
EndSection
```
That _CorePointer_ made the difference!  I had also moved this section above all the other InputDevice sections, but now I don't know if that matters or not. 

It is so great not to have that unwanted tap feature! It might be a good thing if the hardware were less sensitive, but on this Thinkpad it was horrible.

BTW this is with Debian Lenny, but *ahem* Debian is just another 'buntu flavor, right?

A very big thanks to Chili.willy for this.
I worked at this problem for over two days...unsuccessfully.
I copied & pasted this in my xorg.conf file. Now Gsynaptics controls the touchpad correctly.
I'm running debian Lenny on Thinkpad T-42.
Nice job Chili!!
Cliff

---

### Post by CRIMPS on 2009-02-28
Very interesting!!!  I was having the same issues with inconsistent scrolling, etc.

I seem to now have full functionality after just a slight addition to my xorg.conf file.  

Here is my xorg.conf file.  Notice my only addition in red.  
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	[COLOR="Red"]Option          "CorePointer"[/COLOR]
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"LeftEdge"		"120"
	Option		"RightEdge"		"830"
	Option		"TopEdge"		"120"
	Option		"BottomEdge"		"650"
	Option		"FingerLow"		"14"
	Option		"FingerHigh"		"15"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"ClickTime"		"0"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"0"
	Option		"MinSpeed"		"0.45"
	Option		"MaxSpeed"		"0.75"
	Option		"AccelFactor"		"0.020"
	Option		"EdgeMotionMinSpeed"	"200"
	Option		"EdgeMotionMaxSpeed"	"200"
	Option		"UpDownScrolling"	"1"
	Option		"CircularScrolling"	"0"
	Option		"SHMConfig"		"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

One thing to add is that the majority of my additions for my touchpad were from this [wiki]("https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#Ubuntu%208.04%20Hardy%20Heron") since I am running Ubuntu 8.04 on a Dell XPS 1530.

I will definitely update this if I find that some changes weren't permanent.  But Thanks!!!  :)

---

### Post by CRIMPS on 2009-03-14
ok, I can temporarily use my touchpad to scroll.  However, if I reboot again, I will no longer have scrolling capabilities.  This is because I have made a change to my xorg.conf file by adding and then removing this line from the Synaptics Touchpad section:
```
    Option         "CorePointer"

```
The addition of this line now completely disables my touchpad.

So, I think I may look further into the SHMConfig conflict.  

Does anyone have anything else to add to this?

---

### Post by nwadams on 2009-03-14
I found the root of the problem...We're all too lazy to touch type properly...LOL. OK, actually though. I found that no really all of these fixes are hit or miss because of the nature of the problem. I really think the solution needs to be something that can disable the touchpad when an external mouse is plugged in, and something that reduces the sensitivity of the touchpad. But on the other had the initial syndaemon fix seems to work great for me...

Or atleast if it doesn't, unplugging my external mouse and re-attaching it seems to fix any issues I have. 

I shall investigate more...

---

### Post by CRIMPS on 2009-04-09
> **ThinkDifferenter said:**
> I posted this in a response to another thread, but I realized it might not reach the audience it needs from the OP, since it's only mildly related, so I'll post it again in a new topic, more of a howto than anything.

NOTE: THIS IS WHAT WORKED ON MY DELL LAPTOP RUNNING HARDY HERON. ANYTHING YOU TRY IS AT YOUR OWN RISK.

Although I think this could be a general fix for the problem, I see it pop up in Dells most frequently, and I have a Dell XPS m1530, so that's why it's in the Dell section.

I beat my brains out for weeks about this. The touchpad scrolling only worked half of the time. I figured out that it was because the synaptics driver wasn't being loaded correctly, so other things I had attached to SHMConfig, such as no tapping during typing, didn't work either. After reading one particular bug report, I figured out that the psmouse module was being loaded before the synaptics driver, which meant it was overtaking the mouse function. Many people experience this after connecting a USB mouse to their laptop. That's where I went wrong too. Before that, everything worked. After that, things went completely downhill. Unfortunately, the fix didn't seem to apply to Hardy, since it involved commenting out lines in a file that doesn't exist: rc.modules. So how does one stop Ubuntu from loading the psmouse module before the synaptics drivers?

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

If this works for you, let us know. If people know it's working, they're apt to try it. It might work for a lot of other people too. If you have a different setup and it works for you, also say something. I have no idea if this is Dell specific or Ubuntu specific or what. Also, it could just be my specific computer. If it doesn't work, oh well, but at least we exhausted THAT option :D

I actually tried a lot of the easier suggestions before I went through these steps.  Nothing would fix my scrolling issue.  So, I decided to bite the bullet and go through your tutorial.  IT WORKED!  Thanks for posting this up for all of us. :)

---

### Post by 1clue on 2009-04-09
This approach would probably work for me, as long as I put in EVERY possible driver which could be matched first.

I did as described, and then found that my touchpad was using "evdev" as its driver.  So I added that to the list of things to blacklist and later modprobe.

Now, it says the touchpad is using the "usb" driver.

There must be a way to tell the OS to load the synaptics driver FIRST, rather than to disable a bunch of crap and then re-enable it after it is likely that some critical part of my OS isn't working as it should.

---

