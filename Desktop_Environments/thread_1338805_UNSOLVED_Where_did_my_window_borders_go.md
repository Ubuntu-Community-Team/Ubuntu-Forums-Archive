---
title: "UNSOLVED Where did my window borders go?"
date: 2009-11-26
forum: Desktop Environments
---

### Post by desaturated on 2009-11-26
[quote=QUOTE]
**Where did my window borders go?** - cc7gir[INDENT]This is a common mistake caused by disabling some plugins in CompizConfig Settings Manager. To fix, open the manager (System > Preferences > CompizConfig Settings Manager) and find the "Window Decorations" plugin. Check the box and you're all set.
  
[/INDENT][/quote][INDENT]
  
  
STILL not working... my windows border gone after i activate desktop effect... 
im using Geforce 2 using Geforce driver... 
the effect works fine but it got the border gone..
why?
im already follow everything steps i find ond google 
  
im desperade.. help please im already fall in love with UBUNTU
  
thanks.
[/INDENT]

---

### Post by tgalati4 on 2009-11-26
metacity --replace
compiz --replace

---

### Post by desaturated on 2009-11-26
> **tgalati4 said:**
> metacity --replace
compiz --replace


nope.. do that too
the problems still exist...

i think my VGA doesnt support the transclued border

---

### Post by falconindy on 2009-11-26
Enable window decoration in Compiz. Make sure you have

```
gtk-window-decorator --replace
```
for the 'command' field.

---

### Post by dunbrokin on 2009-11-26
I have the same problem on my Dell Latitude E4300...I have a 19" screen attached. If I try and increase the resolution to 1280x1024, I lose my boarder panels.

---

### Post by desaturated on 2009-11-27
> **falconindy said:**
> Enable window decoration in Compiz. Make sure you have

```
gtk-window-decorator --replace
```for the 'command' field.

]
i did that too
even im re installing window decorator..
still not working

---

### Post by tgalati4 on 2009-11-27
Look for errors in /var/log/Xorg.0.log

It's possible that there is a rendering problem due to a driver issue or perhaps a hardware fault.

---

### Post by dunbrokin on 2009-11-27
> **tgalati4 said:**
> Look for errors in /var/log/Xorg.0.log

It's possible that there is a rendering problem due to a driver issue or perhaps a hardware fault.

(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)

I was able to get 1280x1024 working in Jaunty.....also the Desktop extends past the screen in my 19" monitor which is now running on 1024x768...too large for my liking.

---

### Post by tgalati4 on 2009-11-28
tgalati4@tpad-Gloria7 ~ $ gtf 1280 1024 60

  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

Run gtf for your resolution and desired refresh rate (usually 60 Hz for LCD, but 55 Hz and 50 Hz also sometimes works)

Cut and past and put into the correct place in your /etc/X11/xorg.conf file.

---

### Post by dunbrokin on 2009-11-28
Thanks for that....but

a) where exactly is the "correct" place in this file

and

b) do I cut and paste everything which comes up as a result of that command?

---

### Post by tgalati4 on 2009-11-28
Place it in the monitor section.

Cut and paste both the comment (#) line and the modeline.

Make a backup first:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg_orig.conf

gksudo gedit /etc/X11/xorg.conf

Save the file, and log out then back in again.  No need to reboot.

Now realize that this just tells xorg (the X graphical server) the exact parameters to address the resolution and refresh rate that you specified.  Normally this would be the native LCD resolution and the native refresh rate.  You might have to do some research to confirm those numbers.

Now, your graphics chip may not be able to drive those specific frequencies.  If that is the case, the errors will show up in your home directory (.xsession-errors) or in /var/log/Xorg.0.log.

If you do get errors, post them for diagnosis.  That is why log files exist.

---

### Post by dunbrokin on 2009-11-29
Tried at both 60 and 80 refresh rate....neither worked.

ov 30 15:28:04 pj-indulgence kernel: [90295.234206] i915 0000:00:02.0: HDMI Type A-2: no EDID data
Nov 30 15:28:05 pj-indulgence kernel: [90295.740127] [drm] LVDS-8: set mode  57
Nov 30 15:28:05 pj-indulgence kernel: [90296.008235] dell-wmi: Unknown key ffd0 pressed
Nov 30 15:28:05 pj-indulgence kernel: [90296.162690] [drm] DAC-6: set mode  62
Nov 30 15:28:06 pj-indulgence kernel: [90296.764890] dell-wmi: Unknown key ffd1 pressed

II) intel(0):  
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff003064072239353130
(II) intel(0): 	2f120103901d12780a11a5975a528d24
(II) intel(0): 	234e5700000001010101010101010101
(II) intel(0): 	0101010101013a20007751201f304880
(II) intel(0): 	36001fb41000001afe15009e51201f30
(II) intel(0): 	488036001fb41000001a000000fe004d
(II) intel(0): 	54323931803133334556330a000000fe
(II) intel(0): 	00000000000000000001010a20200006
(II) intel(0): EDID vendor "LCD", prod id 8711
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   82.50  1280 1352 1480 1655  800 803 809 831 +hsync -vsync (49.8 kHz)
(II) intel(0): Modeline "1280x800"x0.0   56.30  1280 1352 1480 1694  800 803 809 831 +hsync -vsync (33.2 kHz)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   82.50  1280 1352 1480 1655  800 803 809 831 +hsync -vsync (49.8 kHz)
(II) intel(0): Modeline "1280x800"x40.0   56.30  1280 1352 1480 1694  800 803 809 831 +hsync -vsync (33.2 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP1
(II) intel(0): EDID for output HDMI2
(II) intel(0): EDID for output DP2
(II) intel(0): EDID for output DP3
(II) intel(0): EDID for output TV1
(II) intel(0): Allocate new frame buffer 1024x768 stride 1024

---

### Post by tgalati4 on 2009-11-30
Try 50, 55 and 56 Hz.

---

### Post by dunbrokin on 2009-11-30
> **tgalati4 said:**
> Try 50, 55 and 56 Hz.

No different....all give exactly the same screen.

---

### Post by eugen_nicoara on 2009-12-02
Try this one: 
[http://ubuntuforums.org/showthread.php?t=1138713&highlight=window+manager+karmic]("http://ubuntuforums.org/showthread.php?t=1138713&highlight=window+manager+karmic")

---

### Post by dunbrokin on 2009-12-02
Did not work for me....

---

### Post by desaturated on 2009-12-05
little wierd. 
today im tryng again the old method enabling the Window Border Option on confizconfig manager
then it work find... 
the effect and my border run very smooth!

---

