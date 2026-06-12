---
title: "kubuntu 10.10 as htpc screen resoltuion issues"
date: 2011-02-27
forum: Desktop Environments
---

### Post by savithari on 2011-02-27
Friends:

I have installed KDE on a diff machine and put all the apps.  The monitor
was a LCD 20 inch monitor with resolution of 1600x1200.

Now I moved that to be my HTPC connected to the 60 inch HDTV (max resoltuion
of 1920x1080).  But now tweaking the resolution to see the whole desktop is
a challenge.

I am not sure to take the xorg.conf file route or if kde controls these
things at a different level.

Should I just re-install the os when connected to the TV ?

-Narahari

---

### Post by wizard10000 on 2011-02-28
> **savithari said:**
> Friends:

I have installed KDE on a diff machine and put all the apps.  The monitor
was a LCD 20 inch monitor with resolution of 1600x1200.

Now I moved that to be my HTPC connected to the 60 inch HDTV (max resoltuion
of 1920x1080).  But now tweaking the resolution to see the whole desktop is
a challenge.

I am not sure to take the xorg.conf file route or if kde controls these
things at a different level.

Should I just re-install the os when connected to the TV ?

-Narahari

How is your video connected to the TV?  I know on mine if I use s-video I only get 800x600 (this is normal - s-video only supports 540p) and if I use VGA I can get 1366x768 - the only way for me to get full resolution on my TV is to come in on an HDMI port - which works just fine for me.

You might wanna look at your TV's manual to see which resolutions are supported on which interfaces.

Hope this helps a little -

---

### Post by SeijiSensei on 2011-02-28
If you have a DVI or HDTV connector on the video card, use that.  I have a Sony Bravia connected via an HDMI<>DVI converter cable.

Also, it might depend a bit on the video card you have.  If you're using the proprietary NVIDIA driver, you should be able to fix the problem using the "NVIDIA X Server Settings" app.  If you're lucky the TV will have a known "EDID" code.  The NVIDIA app can detect those automatically and obtain the specifications of the device.

Another issue concerns the TV itself.  My Bravia lets me choose the amount of "overscan" I want on each input.  For the computer, I use the "full-pixel" mode.  If you're having problems with the image being slightly too large, so you're losing content on the edges, you might be able to fix it that way.

---

### Post by savithari on 2011-02-28
TV = Sony Bravia KDS-60A3000
Connection type  = DVI->HDMI.

I am not sure what resolution HDMI supports on the TV.

When I run Kubuntu on this, I dont see the full screen.

Please elaborate on some of the stuff u have said that overscan etc.,

I dont mind if I run Kubuntu or Ubuntu, since the final idea is to run it as a Myth Client.

-Narahari

---

### Post by SeijiSensei on 2011-03-01
> **savithari said:**
> TV = Sony Bravia KDS-60A3000
Connection type  = DVI->HDMI.

I am not sure what resolution HDMI supports on the TV.

It would help to know the video card you're using, and which drivers.

> When I run Kubuntu on this, I dont see the full screen.

Please elaborate on some of the stuff u have said that overscan etc.,

Does the screen have the correct aspect ratio (16:9) but not fill the screen?  How much smaller than the screen is it?  If it's only slightly smaller, you can probably adjust the overscan (see below).  If it's considerably smaller, you're probably running at a resolution smaller than the screen supports.

On my Bravia, if you enter the menus and choose the Screen options, there's a menu item called "Display Area" which actually compensates for over/underscan.  I have values like -2, -1, Normal, and Full Pixel.  The last one works best when using the screen as a monitor.

The TV's native resolution should be 1920x1080.  You should be able to set the video card to the same values.

---

### Post by wizard10000 on 2011-03-01
> **savithari said:**
> TV = Sony Bravia KDS-60A3000
Connection type  = DVI->HDMI.

I am not sure what resolution HDMI supports on the TV.

When I run Kubuntu on this, I dont see the full screen.

Please elaborate on some of the stuff u have said that overscan etc.,

I dont mind if I run Kubuntu or Ubuntu, since the final idea is to run it as a Myth Client.

I have a KDS-50A2020, which is a 50" version about a year older than yours.  The TV supports 1920x1080 through the HDMI port but as I said, only 720p through VGA.

If your video card has a DVI port all you need is a DVI to HDMI adapter and you should be able to get full HD off the card, depending of course on whether the card supports that resolution.

---

### Post by savithari on 2011-03-02
Thanks guys for replying.  I was a bit late on catching up .

I think I have an NVIDIA card but I can confirm that tonight.

My issue has been that the display is too big, aka 

I was execting the screen to fit the display, but I have to scroll to the left to see whats on the left side.

Let me provide VIDEO card info.

-Narahari

---

### Post by wizard10000 on 2011-03-02
> **savithari said:**
> Thanks guys for replying.  I was a bit late on catching up .

I think I have an NVIDIA card but I can confirm that tonight.

My issue has been that the display is too big, aka 

I was execting the screen to fit the display, but I have to scroll to the left to see whats on the left side.

Let me provide VIDEO card info.

This is a problem with projection TVs - the way I solved it was to use a custom screen resolution.  Unfortunately what I ended up doing was putting Windows on the machine since it was considerably easier to get a custom resolution.

---

