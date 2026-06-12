---
title: "Dual monitors OK in Ubuntu, not Xubuntu"
date: 2012-05-19
forum: Desktop Environments
---

### Post by dave0109 on 2012-05-19
I recently tried running 2 monitors on my machine (running Xubuntu 12.04), and whilst the second monitor was detected, it would only mirror the main monitor.

Out of curiosity, I booted Ubuntu 12.04 off a USB stick, and within the settings UI, I could select not to mirror the monitors, and everything worked very slickly indeed.

I thought I'd be clever and grabbed the monitors.xml file from the config, but that doesn't appear to exist in Xubuntu.  So much for that idea.

Anyone know where/how I can set the second monitor up properly.  I just want it to run as an extension to my desktop on the right.

---

### Post by rai4shu2 on 2012-05-19
Multiple monitor support is spotty with the open source drivers. If you want good support, you'll need to use the driver appropriate to your video hardware (which I would guess is an ATI card, in which case you need fglrx).

Once you have the appropriate video driver installed, go to Settings/Settings Manager/Display, and configure your monitors as necessary.

---

### Post by coffeecat on 2012-05-19
> **rai4shu2 said:**
> Multiple monitor support is spotty with the open source drivers. If you want good support, you'll need to use the driver appropriate to your video hardware (which I would guess is an ATI card, in which case you need fglrx).

Not necessarily so. I have a Radeon HD6450 card using the default open source driver, and I can set up dual monitors in Ubuntu 12.04 quite easily. No need for the fglrx driver at all. Ditto 11.10 and ditto with a Radeon HD5450 card when I tried it in this same machine. I've installed Xubuntu 12.04 on another partition and I am finding the same as the OP - I can only get a mirrored display. I too would be interested to hear what, if anything, can be done in Xubuntu to enable dual-monitors with an ATI card without installing the fglrx driver, which I've always found a very unrewarding experience.

@dave0109, it would be useful if you posted details of your graphics card and which driver you are using because discussion of ATI/AMD cards may be irrelevant to your situation.

---

### Post by dave0109 on 2012-05-20
Yeah sorry about that, I'm using the integrated graphics on my motherboard, which is an [ASUS P8Z68-V Pro/Gen3]("http://www.asus.com/Motherboards/Intel_Socket_1155/P8Z68V_PROGEN3/").

I had assumed that the same drivers would be loaded.  Not sure how to find out exactly.  Though I did run the following:-

```

$ lsmod | grep video
video                  19596  1 i915
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

---

### Post by coffeecat on 2012-05-20
It looks as though you have an Intel graphics device, so there will be no proprietary driver to install. It might be useful to see all the video information for your machine. Post the output of this command:

```
sudo lshw -C video
```

Having said that, I think the problem that you and I are experiencing in Xubuntu is a limitation of Xubuntu configuration, not a video driver one. I'm sorry I don't have an answer at the moment, but I will boot into Xubuntu again when I have a chance and do some more investigation. Perhaps someone with more Xubuntu experience will have an answer, and I will keep this thread subscribed.

**EDIT**: you added the outut of lspci while I was posting. :) lshw will not add that much, but it wouldn't do any harm to post it. I will investigate this more.

---

### Post by coffeecat on 2012-05-20
@dave0109, I found this:

[http://askubuntu.com/questions/62681/how-do-i-setup-dual-monitors-in-xfce](http://askubuntu.com/questions/62681/how-do-i-setup-dual-monitors-in-xfce)

I haven't tried it yet with my ATI graphics - I shall do so later today. If you want to try it, let us know how you get on.

---

### Post by Peripheral Visionary on 2012-05-20
If you solve this puzzle it should be "made **sticky**" so other Xubu users can find it quickly! Please.

---

### Post by dave0109 on 2012-05-20
@coffeecat - Thanks mate, it worked perfectly.

In my case I have a second screen using the VGA port and I may not always use it, so I did:-
```

xrandr --output VGA1 --right-of HDMI1 --auto

```

Which gives me exactly what I wanted.  If someone wants sticky edges though, they'll need to do something more.

---

### Post by coffeecat on 2012-05-20
> **Peripheral Visionary said:**
> If you solve this puzzle it should be "made **sticky**" so other Xubu users can find it quickly! Please.

No - two reasons. If we stickied every useful thread, the forum would be a mass of stickies. Also - I've run into a problem with my ATI card. Running xrandr with appropriate parameters for my setup created a usable dual-monitor setup for that session, but after adding the xrandr command to application autostart as described in the askubuntu link, I was unable to log into my Xfce desktop after a reboot. The only way I could rescue my desktop was by deleting ~/.config and all contents - probably an over-drastic way of doing things.

I need to do some more investigation and if I can determine what went wrong, try it with a nvidia card with the nouveau driver as well. People using proprietary video drivers can use the appropriate proprietary config app. For those using open source drivers, this information needs to be on the wiki, and I'll see about arranging that if I can solve what went wrong for me. 

In the meantime, the OP appears to have an answer for their Intel graphics device, although...

@dave0109, were you able to log into your desktop after a reboot or after logging out and in again?

---

### Post by dave0109 on 2012-05-20
No I haven't tried that yet, as I'm in the middle of stuff that "has to be done".  I did find that the VGA screen was taking all the prompts, so I've modified my command to set the HDMI output as primary...

```

xrandr --output HDMI1 --left-of VGA1 --primary --output VGA1 --auto

```

I'll report back on the login after reboot later.

---

### Post by coffeecat on 2012-05-20
I can't reproduce the problem I saw before - logging out and in or rebooting now allows me to log into my Xfce desktop just fine with the xrandr command added to application autostart. It must have been a one-off glitch or perhaps I made an error copying and pasting the command from the terminal into application autostart. Whatever, I can report that I get a usable dual-monitor desktop with my ATI card and open source driver using this method. For the record. my xrandr command was:

```
xrandr --output DVI-0 --left-of HDMI-0
```

That's with identical 1920x1080 monitors, DVI on the left and HDMI on the right. Desktop icons, panel and dock on the left - blank desktop with wallpaper only on the right, but I can move open windows across just fine. I'll add the --auto option that dave0109 used - seems a good idea. And I'll try this with a nvidia card + nouveau driver in due course and see about a wiki page.

---

### Post by dave0109 on 2012-05-21
Yup, just logged in OK.  However, I didn't have the second screen on, so I ended up with a messy desktop as it drew the background image for the second screen on top of the primary screen.  Currently the monitors are different size, as I'm just trying this out.  If they'd been the same size, I doubt that I would have noticed.

As I won't always be using the second monitor, I decided to get rid of the autostart command, and I've added 2 launchers to my desktop.  One to enable the second monitor and put it to the right, as per my previous post.  The second to turn off the second monitor with:
```

xranrd --output VGA1 --off

```

When I ran that, the background got restored to normal as the overwrite disappeared.  I'm happy with that. :)

---

