---
title: "xfce fail next login after modify resolution"
date: 2009-10-31
forum: Desktop Environments
---

### Post by ccampbell on 2009-10-31
Setup:

Toshiba Centrino laptop 
External LCD monitor capable of 1440x900

On first XFCE session, resolution defaults to 

1024x768       75.1     70.1     60.0

So I go change it using xfce4-display-settings GUI  which gives me the 1440x900 option which applies and works great.  

However, on the next login, gdm starts up XFCE, xfce tries to start, then kicks me back into gdm.  

Knowing Linux, I ctrl+f1 into shell and delete ~/.config 

and I'm able to login to XFCE again, but that isn't something a "normal" person would know to do and it sucks to lose the whole ~/.config dir if you just setup your desktop for the first time.

Turns out all I needed to delete is this file:

~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml

but again, who is going to know to do that before they just give up on xubuntu or Linux completely?

I know people will have all sorts of solutions adding xrandr commands to my xfce init script and all that cool guy stuff, but what is the real solution?  

I see this as a serious problem because I don't think a laptop with external monitor is an odd hardware setup.  

How did this bug make it to the 9.10 release?  I see a similar complaint from someone running the 9.10 beta, but it seems like this would have been fixed during the 9.04 cycle.  

I've reported here  [http://bugzilla.xfce.org/show_bug.cgi?id=5932](http://bugzilla.xfce.org/show_bug.cgi?id=5932)

---

### Post by ccampbell on 2009-10-31
[FONT="Lucida Console"]Here is my solution for now.  

#!/bin/sh
# turn off laptop display
/usr/bin/xrandr --output LVDS1 --off
# set resolution/refresh rate 
/usr/bin/xrandr -s 1440x900 -r 60

I saved the above as xrandr.sh in my home space and made it executable:

chmod u+x xrandr.sh

Using these commands after I login I get my desktop setup and the displays.xml doesn't exist or change, so I can login to XFCE next time.[/FONT]

---

### Post by ccampbell on 2009-11-07
One more important note on this, if I place the above script at the end of my .profile I have the same issue, get kicked back into GDM ( login screen ).

I might be wrong using .profile, I need to find the proper . file so I can run the command "late enough" after XFCE is loaded up.  Anyone know where I can put this script so it runs at the proper time?

---

### Post by ccampbell on 2009-11-07
Found a config file that works.  I created a "Desktop Entry" autostart file in ~/.conf/autostart/  called  ~/.conf/autostart/fixDisplay.desktop

[Desktop Entry]
Encoding=UTF-8
Name=fixDisplay
GenericName=fixDisplay
Comment=Set resolution.
Exec=sh /home/***/xrandr.sh
Icon=/usr/share/pixmaps/program.jpg
Terminal=false
Hidden=false
Type=Application
Categories=
OnlyShowIn=XFCE;

This waits long enough for xfce to be established in crappy default resolution, then after < 2 seconds, the script runs, the primary laptop screen turns off, and the resolution is set properly on my external VGA.

Perfect.

From what I read this morning, the ~/.conf/autostart directory is a GNOME (maybe Xorg / freedesktop?) standard that works with XFCE.  

I would like to find more information about the "after GDM" X windows manager "boot process" for lack of a better description.

---

### Post by vickoxy on 2010-02-27
> **ccampbell said:**
> 

I see this as a serious problem because I don't think a laptop with external monitor is an odd hardware setup.  

How did this bug make it to the 9.10 release?  I see a similar complaint from someone running the 9.10 beta, but it seems like this would have been fixed during the 9.04 cycle.  

I've reported here  [http://bugzilla.xfce.org/show_bug.cgi?id=5932](http://bugzilla.xfce.org/show_bug.cgi?id=5932)

Thanks for this thread-i reinstalled xubuntu 2 times thinking that i messed something up. It is really annoying that this problem/issue is not fixed-i had another problems with 9.04 gnome edition, but still it seems that external display/monitor problems are not highest on priority list... 

This is my thread, but now it is solved (although by workaround):
[http://ubuntuforums.org/showthread.php?t=1416839](http://ubuntuforums.org/showthread.php?t=1416839)

---

### Post by azertyh on 2010-02-28
hi,
nice idea. i will try it.
i had the same problem, resolved it by modifing the file display.xml before logging.
i found another solution :
```
[FONT=Courier New][SIZE=2]sudo mv /usr/bin/xsplash /usr/bin/xsplash.disabled[/SIZE][/FONT]
```it works.

---

