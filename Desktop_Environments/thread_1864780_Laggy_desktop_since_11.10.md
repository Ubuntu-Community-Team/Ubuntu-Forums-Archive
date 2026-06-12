---
title: "Laggy desktop since 11.10"
date: 2011-10-19
forum: Desktop Environments
---

### Post by senning on 2011-10-19
I've been experiencing strange lagging since upgrading to 11.10. These things fail to show up properly, leaving artifacts where the screen should be refreshed:

[LIST]
[*]Unity dash and dash home
[*]Text input into Firefox and chrome
[*]Text selection in Firefox and Chrome
[*]Window dragging and resizing
[*]Totem crashes when playing movies; VLC doesn't update the window, but it 'works'
[/LIST]

These things work okay:
[LIST]
[*]Window scrolling in Firefox, but not Chrome
[*]Switching between virtual desktops
[*]Resizing photos in image viewer
[/LIST]

This may be related to other reported Unity slowdowns but the symptoms seem different and I'm not sure it's all related to Unity. Anybody have any ideas on what might be causing this?

---

### Post by weelk on 2011-10-19
I've had the same problem after upgrade - decreased performance lagging  etc.. For me the problem was gone after I have backed up my data and did  clean install of 11.10 rather than upgrade. In my opinion there is  something unhealthy with upgrade procedure - at least for my setup,

---

### Post by 2F4U on 2011-10-19
What are the hardware specs and what graphics driver are you using?

---

### Post by jimbo99 on 2011-10-19
Please stop asking people about their graphics driver as the primary cause of their computer lag for problems in Ubuntu 11.10.  It is not the problem. Using the fallback driver for Ubuntu would not cause this sort of issue either.

Please check your system monitor and observe the cpu utilization.  That usually is the indicator of your lag.  The first guy to respond to you said he backed his data up and reinstalled.  That does certainly help in my experience.

What I have found is that cpu utilization across multiple cores is excessive and constant.  I also found that Akonadi has been contributing to my issues.

I have a set up with a separate drive as my home folder.  I had serious performance issues and chose to, after a lot of investigating, wipe and reinstall.  Doing this put me in a position where I had the default home folder (not the separate drive) and my performance was rather nice.  My next step was to put the separate partition with my home folder in place.  That caused a serious cpu utilization spike.  So, I switched back and forth several times and found every time I did the cpu utilization shot up and Akonadi was loading itself 25+ times just chewing up my RAM (4 gigs--no it didn't chew up 4 gigs).  I then tested my hard drive for defects and ran a check against the file system.  Neither had any sort of problem.

My next and only choice was to rename my .kde folder and reboot.  After doing this the cpu utilization was under control, but akonadi was still loading and ubuntu one was nagging like crazy, so I shut both of them off.

My performance is under control and the desktop is snappy but when I use the web browser opening a new folder takes 2-3 seconds and closing one takes an equal amount of time. And, sometimes when I begin to type a url in the address bar the window that pops up showing the predictions tends to freeze and the browser becomes unusable and can't be closed.  I have to ctrl+alt+esc to kill it.

This version of Ubuntu is terrible.  I chose to upgrade because I didn't think Canonical could do worse than their last update.  I found that's not a good reason to upgrade, lol.  I also found that someone created crippled version of gnome 2 and put that in place instead of the real version of gnome 2.  It turns out that the gnome devs created that piece of junk as a fallback for those that can't run gnome 3.  I guess they didn't consider those that didn't like their product, and what their wishes would be.

So, with Unity and Gnome 3 this release sucks bad.  The sheer volume of people having problems clearly indicates that Canonical is sliding either out of control or down hill.  KDE seems to be the only saving grace, except they too sometimes just ignore the wishes of their users and dictate to us how things will be done.

---

### Post by jakob42 on 2011-10-20
I have the same problems and discovered there seems to be a bug with my on board nvidia graphics card: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/859979](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/859979)

I removed the nvidia drivers and Unity was still laggy, but the dash opened faster. It still wasn't really usable and I switched to gnome-shell. I'm still having problems, but at least it runs faster on my machine.

AMD Dualcore with 2.3Ghz, 3GB RAM and a Nvidia 7050 onboard graphics card.

---

### Post by SuperUserDO on 2011-10-21
I have same exact problem........where 3d acceleration in needed there is always lags.
GeForce 7025 / nForce 630a
NVIDIA Driver Version:285.05.09

---

### Post by stunrock on 2011-11-12
does anyone have a solution yet?

when i install ubuntu the desktop is crappy and none of the drivers are working.

if I use the live usb-stick evythings fine

I don't know what the problem is?????

I have a nvidia 7050 grafik chip

---

