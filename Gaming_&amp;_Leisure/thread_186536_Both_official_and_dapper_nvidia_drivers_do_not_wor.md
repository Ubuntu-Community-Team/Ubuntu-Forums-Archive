---
title: "Both official and dapper nvidia drivers do not work!"
date: 2006-06-02
forum: Gaming &amp; Leisure
---

### Post by PPower on 2006-06-02
I can not get either of the nvidia drivers to install! Whenever I reboot after installing them all that happens is a blank usplash appears.                                                     I can then press CTRL+ALT+F1 to get to a console. There were no errors in the installation of both drivers except for a little complaint of nvidia-glx-config enable when it said the md5sum of the xorg.conf file was invalid. A simple hack fixed that.

My card is a XFX nVidia GeForce 6600LE PCI-E with 256mb of ram. Tried latest drivers for x86 Linux.

---

### Post by eqisow on 2006-06-02
Just to confirm, you have both nvidia-glx and linux-restricted-modules installed, correct? If so, could you possibly post your xorg.conf?

---

### Post by PPower on 2006-06-02
[QUOTE=eqisow]Just to confirm, you have both nvidia-glx and linux-restricted-modules installed, correct? If so, could you possibly post your xorg.conf?[/QUOTE]
Fixed it. It was a bug in the nvidia-glx-config script. I bugged it. I made a faq outlining the fix.

---

### Post by eqisow on 2006-06-02
I'm glad you worked out your problem, and having your solution documented will be very helpful! Where did you post it? It might be helpful to have it added to [https://wiki.ubuntu.com/NvidiaTroubleshooting](https://wiki.ubuntu.com/NvidiaTroubleshooting) as well.

---

### Post by tseliot on 2006-06-02
[QUOTE=PPower]Fixed it. It was a bug in the nvidia-glx-config script. I bugged it. I made a faq outlining the fix.[/QUOTE]
nvidia-xconfig is much better and works without problems

---

### Post by handy on 2006-06-03
I had to edit my **xorg.conf** file to get it to work properly.

After installing the the nVidia (closed) drivers via [**Automatix**]("http://ubuntuforums.org/showthread.php?t=177646") :KS   I rebooted, & had 85hz refresh rate instead of the default 60hz.  But, still only the same three screen resolutions available, topping out at 1024x768.

So, I edited the **xorg.conf**, putting in the acurate vertical & horizontal refresh rates for my monitor. & added 2 more resolutions to each of the screen modes: 1280x1024 &1600x1200, the latter being what I usually use.

I also edited the mouse settings to get my** m$ IntelliMouse Explorer** to fully function.  **See below?**

Did a control, alt, backspace!  & landed in all sorts of xorg trouble :rolleyes: 

I was forced to use a backup **xorg.conf**, which started up ok.

I then just put the largest size screen res' & deleted the others - 1600x1200.  Restarted again no problem!! :confused:  Below works perfectly for me now!

**[Edit:] *I get 13,000 fps, with glxgears -printfps*** which is atleast as good if not slightly better than what I got in Breezy.

[B][I]Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"

(For anyone who doesn't know: Make sure you have the correct numbers in the following 2 lines, look in your monitor manual or google it up, VERY important.  The numbers edited out "#" were what the system supplied!!  The higher the refresh rate of a CRT monitor the more stable the image.  Makes a big difference for some sets of eyes... )

	HorizSync	30-107    # 28-51   
	VertRefresh	48-120    # 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection[/I][/B]


*This is all I need for the intellimouse explorer, to get the 2 buttons on the side to go forward & back through web pages in firefox. The rest of it works as normal:*

[I][B]Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons"       "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping"  "4 5"
EndSection[/B][/I]

**[Edit:] *I get13000 with glxgears -printfps***

---

### Post by asparagus3000 on 2006-06-07
[QUOTE=tseliot]nvidia-xconfig is much better and works without problems[/QUOTE]

Thanks!  I tried this on a 5700, and it seems to have worked.  
  --- Details below: ---
I have been having problems using nvidia-glx-config on two separate (and very different) systems on 6.06 dapper. I am writing this post to try to inform the ubuntu staff about the problem)  In both cases, I got the same error message (or at least a very similar error message, having to do with md5sum).  Here's the full procedures I used to solve each problem:

------------------------------
System #1 (legacy):  card: nvidia TNT2 

What I had done:
I installed the nvidia-glx-legacy drivers and attempted to enable GLX using:

            sudo apt-get install nvidia-glx-legacy
            sudo nvidia-glx-config enable
Problem:
nvidia-glx-config generates an error message (something to do with md5sum)...
            "Error: your X configuration has been altered. This script cannot proceed automatically."
   I'm not completely positive that this is a problem.  But anyway, if I remember correctly, during previous attempts, this error message usually meant that he hardware acceleration had not successfully been enabled (although in my case, I believe the xserver still started).  Incidentally I tried running "nvidia-settings", as suggested, but this gave me an error message and didn't seem to do anything.)

Solution:
    Then I edited the /etc/X11/xorg.conf file, and replaced "nv" with "nvidia" (as suggested by the error message), and restarted.  That seemed to do the trick.  (After that, the command "glxinfo | grep rendering", returns "direct rendering: Yes".)

Domain of validity:
I should mention that this particular proceedure only worked for me when starting from scratch.  Note that right after ubuntu is installed if you type:
          glxinfo | grep rendering
then, if I'm not mistaken, you should get a simple one-line answer:
         direct rendering: No
However if it says something other than No or Yes., then you may have broken something while installing other packages or tinkering around.  This was my expierience on an earlier install.  Editing /etc/X11/xorg.conf on that occasion did not work (I forget exactly what hapened, but something bad).  Try uninstalling and reinstalling the nvidia drivers, or if that fails, re-installing ubuntu before editing the xorg.conf file.

------------------------------

System #2: card: nvidia fx5700 (LE I think)

What I had done:
I installed the nvidia-glx-legacy drivers and attempted to enable GLX using:

            sudo apt-get install nvidia-glx
            sudo nvidia-glx-config enable

Problem:

Again, the "nvidia-glx-config" script generates an error message.  I think it was the same message I got in system #1, or very similar.  ("md5sum", "This script cannot proceed automatically.")

Solution:
      I uninstalled nvidia-glx (I think I used System->Administration->Synaptic Package Manager to do this), restarted, re-installed nvidia-glx using: "sudo apt-get install nvidia-glx".  Incidentally, after doing all this, when I entered:
         glxinfo | grep rendering
the computer responded with:
         direct rendering: No
(This was a good sign.)

      Then I tried tseliot's suggestion:  I ran "nvidia-xconfig".  This worked and upon a restart, it enabled my 3D hardware acceleration for the 5700 (althought the glx-gears framerates were a little bit lower than expected (1000-2000 fps)).

Incidentally, I don't know what would have hapened if I had tried nvidia-xconfig on the other system.  (Perhaps it would have worked.)  I'm a bit sleepy right now and I hope these notes weren't too rambling or vague.  Feel free to move this post anywhere relevant.  Cheers.

Andrew

---

### Post by asparagus3000 on 2006-06-07
In short, the instructions located at:
[http://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](http://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)
didn't work for me on either of the two systems I tried.
In both cases, "sudo nvidia-glx-config enable" didn't do what was expected, although perhaps something I'm doing is to blame.

---

### Post by B0rsuk on 2006-06-07
Just curious, why did you reboot ?

---

### Post by PPower on 2006-06-07
I did launchpad a bug on this
[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/48077]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/48077")

---

