---
title: "xrandr confusions"
date: 2019-03-07
forum: Desktop Environments
---

### Post by jgw on 2019-03-07
I am running with a radeon 3000 motherboard display and my display driver is 'radeon'

I have been trying to increase my resolution from 1024x768 to 1920x1080 with xrandr

I started with:
greg@gregdown:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
1024x768 60.00*
800x600 60.32 56.25
848x480 60.00
640x480 59.94
DVI-0 disconnected (normal left inverted right x axis y axis)

then I entered:
xrandr --newmode 1920x1080-1  220.64  1920 2056 2264 2608  1080 1081 1084 1128  -HSync +Vsync
and then did it again (no excuse)

and now I have:
greg@gregdown:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
DVI-0 disconnected (normal left inverted right x axis y axis)
  1920x1080-1 (0x4fb) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1089 end 1095 total 1125           clock  60.00Hz
  1920x1080-2 (0x4fe) 220.640MHz -HSync +VSync
        h: width  1920 start 2056 end 2264 total 2608 skew    0 clock  84.60KHz

I also understand that once I get through the xrandr I will need to:
xrandr --addmode VGA-0 "1024x600_60.00"
xrandr --output VGA-0 --mode "1024x600_60.00"

The first thing I think I did wrong was to not put the 1920x1080-1 in quotation marks in the initial xrand --newmode line.  I probably need to start over from scratch but have no idea how to do that.  The I can start with a new newmode.  Right now I have cleverly managed to insert two DVI assignments but there is no DVI connection.  I also have no idea how I managed that.

Any thoughts would be appreciated.

Thank you...................

---

### Post by jgw on 2019-03-08
OK, I figured it out - Here was my solution (I will mark it as solved):
get monitor info:
xrandr
All the commands below are entered in the terminal!

Get current devices/connections - mine is VGA-0, it could be any connection like HDMI, DVI, etc.   "DEVICE" will mean whatever is found with "xrandr --current" and will be something like VGA, DVI, HDMI, Etc.
xrandr --current

Remove device (change DEVICE to device): 
xrandr --auto && xrandr --output DEVICE --off

get line to add to "sudo xrandr --addmode  DEVICE"   Do not add the 'Moduline";
cvt 1920 1080
which returned:
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

Then we put it all together and get:
sudo xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

Now add the device:
xrandr --addmode DEVICE "1920x1080_60.00"

The basic commands to put into the terminal are:
xrandr
xrandr --current

If you need to remove any devices:
xrandr --auto && xrandr --output DEVICE --off

cvt 1920 1080
sudo xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode DEVICE "1920x1080_60.00"

Now run xrandr again and see what you  got.  The last line of the device is what you just entered. If it didn't take you can force it with:
xrandr --output DEVICE --mode "1920x1080_60.00"

Now you can goto settings, choose the new resolution and see if it works.  Mine did but the screen ran off the right hand side.  I turned off my monitor, turned it back on.

Now, to make it permanent you need to enter the following lines to the .profile file in your home directory.  (the .profile file reloads the commands everytime you re-boot):
#set starting resolution
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode  "1920x1080_60.00"

You can also add (which, apparently, assures the --addmode takes):
xrandr --output DEVICE --mode 1920X1080_60.00

A Link: [https://www.ma-no.org/en/content/index_how-to-force-screen-s-resolution-in-ubuntu-and-make-it-permanent_2172.php](https://www.ma-no.org/en/content/index_how-to-force-screen-s-resolution-in-ubuntu-and-make-it-permanent_2172.php)

I did this and found it did NOT work (or permanently change your reboot)
if you don't have arandr install it with: sudo apt-get install arandr

sudo apt-get install arandr
once you got it like you want it run arandr, set up your resolution stuff there, press control enter and, in theory it should be set until you want to change it!

Here is a link: [https://askubuntu.com/questions/642617/how-to-permanently-set-a-custom-resolution](https://askubuntu.com/questions/642617/how-to-permanently-set-a-custom-resolution)

---

