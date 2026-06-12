---
title: "Graphics problems - Zino HD - ATI 4250 - Panasonic VIERA TC-P42S30"
date: 2011-07-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MarlonNelson on 2011-07-31
I have a new Dell Zino HD using integrated graphics, the ATI Radeon 4250.  It's hooked up, with an HDMI cable, to an HDTV, a Panasonic VIERA TC-P42S30, which supports Full HD at 1080p.  I'm running Ubuntu 11.04.

When it boots, most of the time, the colors are off.  Black is displayed as green.  The other major color seems to be pink.  Pink and green.  Blech.  I'll try to attach a picture I took of it.  If I access the machine via Remote Desktop, the screen looks normal on my laptop, so I don't think the Zino is deliberately displaying pink & green.

Sometimes when it boots, the colors are the normal Ubuntu 11.04 colors.  Sometimes I can fix the problem by using Monitors to switch to 720p and then restore back to 1080p.  When I switch inputs on the HDTV, and then switch back to the HDMI input hooked up to the Zino, the colors are back to pink and green.

When I run with the ATI proprietary drivers (fglrx), I don't get this problem, but I get an overscan/underscan problem where the screen is displayed with black borders on top, bottom, left & right.  Booting to Windows 7, the ATI Catalyst Control Center (CCC) applet lets me fix this by adjusting the overscan/underscan scaling.  This overscan/underscan scaling adjustment isn't available under Ubuntu using the proprietary drivers.  Also, under Ubuntu, CCC thinks my HDTV is a Projector.

I'd like to use the open-source Radeon driver, so my preference is to fix the Pink/Green problem.  Alternatively, if someone knows how to adjust the fglrx driver to fix the overscan/underscan problem (maybe with a change to /etc/ati/amdpcsdb), I'd be willing to go with that.

---

### Post by MarlonNelson on 2011-07-31
Pink & Green - using the default/open source radeon_drv driver

[IMG]http://dl.dropbox.com/u/1149457/Preppy.jpg

---

### Post by s8472 on 2011-09-02
I have almost exactly the same problem.  My Ubuntu 10.04 is intended as an HTPC with a Gigabyte mobo with Radeon HD 4250.  It was connected to my full HD monitor through HDMI and did not display any of these problems.  I took it to TV set (Panasonic TX-P50GW30, a full HD plasma) and connected it to one of the HDMI ports using the exact same cable.  When I turned it on, it was as if I had a green sheet of glass in front of the display and neither the status nor the menu bars were visible.  So unplugged the cable, reversed the ends and plugged it in, still the green cast.  However, after several boots, it suddenly went away.  Then came back again.  So I decided to try ATI driver.  Downloaded and installed 11.8.  This got rid of the green cast, but I had thick black borders around the display area on the TV screen.  Yes, I remember playing with that Overscan Slider on the ATI Catalyst Center but I don't remember when.  I tried several older drivers to no avail.  With some, X would not even start.  So I am stuck with ATI 11.8.  Turning the Overscan on on the TV set got rid of the top and bottom bars, but I still have black borders on both right and left sides, albeit narrower ones.

Code:
> sudo aticonfig --tv-geometry=100x100

did not work, complaining that "TV connection not detected", although Catalyst Center correctly identified it as a 1920x1080 Panasonic TV.

Since ATI driver fixed the green cast problem and turning the TV's Overscan mode on got rid of the top and bottom bars, rendering menu and status bars accessable, I am going to stick with the ATI driver.  But I would very much like to hear about a better solution if anybody happens to have any ideas.

---

