---
title: "nVidia blackout"
date: 2009-03-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stubrownuk on 2009-03-06
I have looked at the various threads about nVidia, Dell and Ubuntu, but can't see anything that exactly matches the problem I have here. Configuration is as follows:
Dell Latitude C840 (an old machine, not my primary business computer, so doesn't matter if things go pear-shaped, I can always re-install)
Ubuntu 8.10 Intrepid thing with horns
Video display is  VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)

All works fine until I try to install the driver (which the system correctly - I think - identifies as nVidia accelerated graphics driver version 96. The installation appears to go without a problem and the system tells me that a re-boot is required. On reboot, the system is clearly functioning (I get the "ubuntu jingle"), but the display is completely blank and black. Since I cannot see anything to know what to do, my only option is to re-install Ubuntu.

The same problem occurred when I was using Ubuntu Studio, if that helps anyone to tie this one down.

Anyone got any ideas? It's not critical that I solve this - I don't need the effects to work for the type of work that I do - but if we can solve it, so much the better.

---

### Post by kamssada on 2009-03-06
me too. same problem. got the instruction from [http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Installation_of_ATI_and_nVidia_Graphics_drivers](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Installation_of_ATI_and_nVidia_Graphics_drivers)
and went to download driver here [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us).

To get the computer working without graphics card reboot, and enter using recovery mode, and select xfix. to fix the xserver. after that you should be booting in normally, but your card will still need to be installed.. 

How to get it installed, I don't know, still trying to figure that out myself.

---

### Post by armandh on 2009-03-07
problems with graphic chip/drivers resulting in black screen but the mouse is working....
a problem I had that a solution of purging compiz was recommended to me and then 8.10 worked [sans effects]

it was on board intel video

---

### Post by MartijnV on 2009-03-09
on my dell C810 (with nvidia 2Go graphics) removing compiz made my computer workable again. Installing the Nvidia 96 driver automatically enabled compiz, after reboot gnome was very sluggish, buttons not working...
Now, with the Nvidia driver but without compiz everything seems to work, except standby and hibernate, but that's a different nvidia problem :(

---

### Post by stubrownuk on 2009-03-10
Interesting that nobody in this thread so far seems to have found what I would regard as a totally satisfactory solution to this issue. I have nothing to add, I still can't get the system to work properly, though in most other respects I'm happy with running Intrepid Ibex or Ubuntu Studio on either a Latitude C840 or D800. All further thoughts/comments much appreciated.

---

### Post by armandh on 2009-03-10
many "Ubuntu problems" are really hardware problems.
older on-board video outputs may have been fine for display of work station spread sheets or docs but do not have the capability needed for compiz, or even the more common 3d.

and unlike plug in video cards, there is no upgrade.
purging the compiz made a Gateway 512 MEG, 2.0 GHZ, P4 run well enough, but not as well as a "thrown together" 512 MEG, .933 GHZ, P-III with a 128 meg [nvidea chip] video card that runs compiz effects and is used for a 1080P HDMI digital media feed.

.

---

### Post by sfrasher on 2009-03-17
I had the exact same problem. Ubuntu 8.10 on a Dell Latitude D840 that went black after installing the Nvidia Geforce 4 driver. I don't remember version of the driver, but I won't install it again!

After hopping all around gathering info, I decided to try to make this a little easier on the next person!

When it boots up and gets through the Dell screen, as soon as you see anything, hit the ESC key. This gets into the menu to fix it. It was F8 in Windows. I hit ESC while in the Dell screen (panic reaction) and it didn't do anything. I hit it again when the Ubuntu lines showed.

Once in the menu, down-arrow to one of the lines that says "recovery mode". Hit "enter".

It will run through a whole bunch of text stuff. Eventually you will get another menu. 
I just went to "xfix     Try to fix the xserver".
I also tried "dpkg      Repair broken packages".

I tried to figure out how to delete that Compiz thing, but I couldn't even find it. So I guess it's still there somewhere.

After that, I went to "resume     Resume normal boot" and everything works again!

I hope this saves someone the 2 hours I spent hunting it down.

---

### Post by simulant23 on 2011-02-03
Same problem here.  It seems that the LCD is not used.  If you plug in an external monitor, you will see your desktop.

To fix this I had to ad the following line under the DEPTH section of xorg.conf:

Option "UseDisplayDevice" "DFP-0"


My problem now is the power management doesn't work.  The C840 won't resume from suspend or hibertnate.  (10.10)

---

