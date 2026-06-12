---
title: "Baffling Xrandr Error codes."
date: 2010-03-04
forum: Desktop Environments
---

### Post by rfbeck on 2010-03-04
In trying to set my laptop's resolution to 1024x768 I am trying to use the "xrandr" command. I have used the cvt tool to get a modeline, and incorporate this into the newmode switch as follows:

$ xrandr --newmode "1024x768_60.00"  63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

which returns the following error code:

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18

Any help troubleshooting this would be great, as I wish to incorporate this xrandr command into a start up script. Thanks.
______
Robert

---

### Post by breley on 2010-03-04
I'm seeing exactly the same problem as Robert after following the Ubuntu Wiki steps[ here]("https://wiki.ubuntu.com/X/Config/Resolution") and [here]("http://solutionz.yolasite.com/linux/add-a-new-screen-resolution-with-the-terminal-on-ubuntu-9-10").  In my case the monitor is an LCD that is detected as "unknown" but is set at gdm login to 1152x864.

---

### Post by rfbeck on 2010-03-04
Okay, that's two of us now. Anyone care to help us out? Thanks.
______
Robert

---

### Post by breley on 2010-03-05
I believe I have solved my problem, and fortunately I had an additional monitor to plug into the desktop system that supported the higher resolution.
In a terminal, I ran "sudo dpkg-reconfigure -phigh xserver-xorg" initially, then ran "sudo gedit /etc/X11/xorg.conf".  In the blank xorg.conf file I put the following to explicitly set the maximum resolution (10x7):

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1024x768"
Horizsync 31.5-48.0
Vertrefresh 56.0 - 65.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
EndSubSection

After saving the file, I then restarted my system and this seems to have fixed my problem.   Robert, if you can drop to a command line, try the first command, and if that fails you could try copying the contents of the above lines (I also enclosed them in an xorg.zip file---not a real zip, just my renamed xorg.conf file...but the above lines are all it has in it) to you xorg.conf file in /etc/X11/.

Rather kludgy I suppose, but it works for me.   Someone wiser than I may have a more proper/elegant solution.

---

### Post by rfbeck on 2010-03-05
Thanks. I've tried the xorg.conf route before and it doesn't work for me for whatever reason. I really want to get the xrandr thing going.
Is there anyone out there who can figure out what causes these error codes stated in my previous post and give me a hand here?

---

