---
title: "video resolution causing problems?"
date: 2011-06-23
forum: Desktop Environments
---

### Post by covenist5 on 2011-06-23
[SIZE=3]Hello again,
    Here's the deal.  I have an older HP (pavilion xt963) and everything was working relatively fine (no suspend) untill I hooked up a (questionable quality) LCD screen.  I've upgraded to Lucid(clean install) and here are the issues. I can not restart the system via the OS, nor can I shut it down without holding down the power button.  Also the toolbars seem to have disappeared (gone out of video range?) which I've solved by using "gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel"
then putting "pkill gnome-panel" in the startup.
but I am pretty sure the new higher resolution bieng used by this monitor is the cause of it all.  With the garbage monitor I was using (1024x768) the system would shutdown and restart, and I had no toolbar issue. now at 1440x900.  

[/SIZE]

---

### Post by FormatSeize on 2011-06-23
I have the same monitor. Perhaps your hardware drivers aren't properly supporting it. Now I'm not going to say that I have a brand new top of the line machine, but there are cases when it won't work with some things. If I have Unity installed, the Grub menu resolution is such that I can't read the text on the screen, then it tells me that the video mode is not supported. So I have about 2 seconds to scroll down to where I need to be (figuring that out was trial and error by simply guessing) and it enter before the monitor turns off. 
 
The installer for Vector Linux doesn't like the monitor either. First it forces me to choose a different resolution, then it still doesn't like any of the choices that it gave me and cuts out. 
 
Do you have a video card installed? If so, you can set that as your main video output and see if that helps. Yesterday I found that if I had my main video output on my graphics card and plug the monitor in there, I had fewer issues with resolution. The downside to that, though, was that I couldn't enable the highest quality desktop appearance setting anymore. 
 
Also, another thing that made me curious is why there is never a setting for 1440X900 on any of the installers' menu where they ask you to select your screen resolution.
 
Lastly, I don't think that it is the monitor interfering with your ability to restart and shutdown the OS. But if you would like to test that, unplug the monitor, press Ctrl + Alt + Delete, then down arrow (if I recall the defaults correctly), then enter, and see if it restarts without the monitor.

---

