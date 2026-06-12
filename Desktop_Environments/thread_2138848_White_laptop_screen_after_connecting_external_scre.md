---
title: "White laptop screen after connecting external screen"
date: 2013-04-25
forum: Desktop Environments
---

### Post by Misconstruction on 2013-04-25
Hi linux gurus!

I'm running ubuntu 12.04 on a new laptop with nvidia optimus. I haven't installed bumblee or anything, so im just using the intel graphics card. I have a dual boot with windows.

Recently i tried using a external lenovo screen with extended displays - which worked perfectly. However, after shutting down, disconnecting the lenovo screen, and rebooting, the laptop screen is pure white. The laptop is still working, ie. the startup jingles still play.

The same problem happens when i boot into windows 7.

If i connect an external screen, i can use the external screen just fine, but the laptop screen is still white. Everything else though works perfectly.

I have tried fixing the problem in both ubuntu and windows with no succes (rebooting, reinstalling drivers, trying all screen resolutions etc.)

here is the output from xrandr:
------------------------------------------
Screen 0: minimum 320 x 200, current 3286 x 1200, maximum 8192 x 8192
LVDS1 connected 1366x768+1920+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1366x768       59.8*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
-------------------------------------------------

The problem seems to be that the 'native' settings of the laptop screen isn't detected (as it is for the external screen), its auto-resolution should be 1920x1200.

I'm thinking i somehow need to restore the default settings for the laptop screen, but i don't know how.

I'm am starting to get rather desperate, so any advice is greatly appreciated!

/Misconstruction

---

### Post by gordintoronto on 2013-04-25
I would give 10 to one odds that this is a hardware problem, you're seeing the white lamp, and the LCD isn't working at all.

You might have told us the exact brand and model of laptop.

---

### Post by Misconstruction on 2013-04-26
Thanks for the reply! I'm am indeed fearing it is a hardware rather than software problem (the laptop model is Vision S3768).

But would a broken LCD screen also lead to wrong resolution options being detected? In other words, why am i not able to choose the standard 1920x1200 resolution?

---

### Post by gordintoronto on 2013-04-26
Wow, first time I have used Google to translate a page from Danish. I was searching for the specs for your laptop, and failed. 1920x1200 is quite unusual.

I would take the machine back to the dealer.

---

### Post by Misconstruction on 2013-04-27
You're absolutely right 1920x1200 is unusual, because it is of course 1920x1080. Sorry for the mistake!

Here are the specs from the vendor (scrool down a bit): [http://www.mm-vision.dk/produkter/vispcsystem.asp?action=vis&type=notevision&menu=notebook&varenr=705500020&gruppe=visionnotebook](http://www.mm-vision.dk/produkter/vispcsystem.asp?action=vis&type=notevision&menu=notebook&varenr=705500020&gruppe=visionnotebook)

To go back to the xrandr output, how exactly is the information shown below retrieved? is there a specification file somewhere?

[COLOR=#000000]LVDS1 connected 1366x768+1920+0 (normal left inverted right x axis y axis) 0mm x 0mm[/COLOR]
[COLOR=#000000]1366x768 59.8*+[/COLOR]
[COLOR=#000000]1360x768 59.8 60.0 [/COLOR]
[COLOR=#000000]1024x768 60.0 [/COLOR]
[COLOR=#000000]800x600 60.3 56.2 [/COLOR]
[COLOR=#000000]640x480 59.9

Once again thanks for the reply[/COLOR]

---

### Post by gordintoronto on 2013-04-27
Sorry, I don't know where xrandr gets its information. On my desktop it says:
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1280x800       59.8  
   1280x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
HDMI-0 disconnected (normal left inverted right x axis y axis)

My system is a lot simpler than yours.

---

### Post by Misconstruction on 2013-04-29
I have not been able to find any description either.

Which means i'm giving up and sending the laptop back to the manufacturer :-(


But thanks alot for the support! Helped me zoom in on the hardware rather than the software as the problem.

---

