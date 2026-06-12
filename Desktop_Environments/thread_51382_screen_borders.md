---
title: "screen borders"
date: 2005-07-23
forum: Desktop Environments
---

### Post by charliez on 2005-07-23
My screen resoulutio is 1024 x 768 but but wallpaper background etc

will not fill monitor,  side borders stop short of actual screen width.

Did not have this issue with Warty or any other distro.

 :?  :?

---

### Post by Lunde on 2005-07-23
Are also your menus short of the actual screen? 
if not what happens if you right click on your desktop, choose change background and stretch as option for you wallpaper?

---

### Post by charliez on 2005-07-23
Menus are okay, do you mean the widescreen ? If so it remains the same.

---

### Post by Lunde on 2005-07-24
[QUOTE=charliez]Menus are okay, do you mean the widescreen ? If so it remains the same.[/QUOTE]
 No I meen **Style: Scaled ** under Desktop Background Preference. **Right click** on the desktop and choose **Change Desktop Background**

Can you also do a screen shot and post it here

---

### Post by charliez on 2005-07-24
Style is scaled

---

### Post by Lunde on 2005-07-24
I don't see anything wrong on the screenshot. Is ot OK now?

---

### Post by charliez on 2005-07-24
No, it doesn't fill the physical monitor screen.

---

### Post by recce101 on 2005-07-24
I have exactly the same problem on one machine (Asus A7S-VM motherboard with onboard SIS630/730 video). Using a 17-inch monitor (Sony Multiscan E210) and screen resolution 1024x768, there is a 1-inch margin (no menus, mouse, anything) on the left side and 3/4-inch margin on the right. Top and bottom are okay, to the edge of the screen. Items that should be round, such as the Firefox icon, are squished -- width less than height. This is true for all desktop background options, including no wallpaper. If I switch to 600x800 resolution, the display fills the entire screen as it should. I can fill the screen horizontally on 1024x768 if I stretch the display with monitor controls, but of course this messes up the display when I switch back to Windows.

Another machine, with an ATI video card, has normal display with a 17-inch monitor at 1024x768. I reinstalled 5.04 on the problem machine, but there's no change. I'm just getting into Linux and am not yet familiar with the various configuration files.

---

### Post by recce101 on 2005-07-24
Hold on - I stand corrected on one point! Saying that stretching the screen with monitor controls would mess up Windows was an assumption on my part, and turned out to be untrue. When I booted back into Win2000 the display was perfect, right to the edges and not beyond. If I stretched the monitor settings while IN Windows, yes, the icons would go beyond the edge. But apparently on startup Win2000 was able to adjust for the new monitor settings I had applied while in Ubuntu. When I went back into Ubuntu, the 1024x768 display was good there too, and the 600x800 display was also okay (though I never use that resolution). Back and forth Windows and Ubuntu, both good now. Life is full of little surprises, isn't it??

---

### Post by Lunde on 2005-07-24
**EDIT: **messed up a litle here, this is for **recce101** 
..but you figured it out anyway.
**charliez** I need to know your Video card model and number and I'm sure to find a similar solution.
----------------------------------------------

OK for the SIS video driver.
I've checked a bit on the net and it looks like the installation should have found that by default. The SiS driver should be integrated with Xorg.

Your xorg.conf should have something like this:
------------------------------------------------
 xorg.conf has the following:

Section "Device"
Identifier "Silicon Integrated Systems (SiS) 300/305 PCI/AGP VGA Display Adapter"
Driver "sis"
BusID "PCI:1:0:0"
EndSection
--------------------------------------------------------
This I found on the net from somebody that Installed Ubuntu and by default got the correct drivers:
[http://forums.whirlpool.net.au/forum-replies.cfm?t=359542](http://forums.whirlpool.net.au/forum-replies.cfm?t=359542)
Are you sure about the SiS630/730?

If so, try to change the xorg.conf Device section** Driver "sis"** and see if it works, if not change back. 

These options should regulate the screen zoom (**Option "SISTVXScale" "integer"**  & **Option "SISTVYScale" "integer"** )

Reference:
X.org configuration options for the SIS driver:
[http://linux.com.hk/PenguinWeb/manpage.jsp?section=4&name=sis](http://linux.com.hk/PenguinWeb/manpage.jsp?section=4&name=sis)

Driver Download form developer (Should not be needed):
[http://www.winischhofer.at/linuxsispart3.shtml#download](http://www.winischhofer.at/linuxsispart3.shtml#download)

Sis 3d Warty
[http://ubuntuforums.org/showthread.php?t=11154](http://ubuntuforums.org/showthread.php?t=11154)
I know this link is a bit off topic, just adding some reference if someone wants to try with Hoary. It may work the same way.

---

### Post by charliez on 2005-07-24
the machine is a dell dimension 2400 with integrated intel vga

lspci -output 

0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)


Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Int
egrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

  I could try stetching with monitor controls but I use a kvm with several other 

machines connected

---

### Post by Lunde on 2005-07-24
[QUOTE=charliez]the machine is a dell dimension 2400 with integrated intel vga

lspci -output 

0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)


Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Int
egrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

  I could try stetching with monitor controls but I use a kvm with several other 

machines connected[/QUOTE]
 There are no easy options that I can find for your driver, but I wonder if it may help to configure "HorizSync" and "VertRefresh". There is also an option for "DisplaySize" to set under Section "monitor" that you don't have. 

If nobody else posts a better answere, or you don't find a solution, I'll check a bit more for you tomorrow. It's so long since I had a similar problem I can't remember exactly how this work.

There are a possibuility to try the driver "vesa", but it's a less functional one.

If you do any changes to xorg.conf, do a backup first with:
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup **

Options supprted by the i810 driver:
[http://linux.com.hk/PenguinWeb/manpage.jsp?section=4&name=i810](http://linux.com.hk/PenguinWeb/manpage.jsp?section=4&name=i810)

Information for i810 Users
[http://www.x.org/X11R6.8.2/doc/i810.html](http://www.x.org/X11R6.8.2/doc/i810.html)

Other links:
[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

---

### Post by charliez on 2005-07-24
Hi,

    I had "HorizSync" and "VertRefresh"

    Tried vesa but would only work with 640X480 or

                                                           1024x768 with a default depth of 8

    
    I finally got it to work with the i810 driver at 1280x1024 
     with a default depth of 24

    I'm attaching my xorg.conf(as xorg.txt), hopefully it will help others

    thanks for all your help I appreciate it

---

### Post by charlieg on 2005-07-24
I wouldn't be surprised if you were using a different refresh rate or some other parameter in Windows which would be causing the disparity.  (i.e. the settings are subtly different between your Windows and Linux video resolutions so the monitor is treating them as different setups with their own stretch/skew values.)

---

### Post by Lunde on 2005-07-25
Glad it worked out for you. I also got to a similar conclusion of Charlieg last night and this I think can be manipulated through the "HorizSync", "VertRefresh" and "DisplaySize" options.

---

