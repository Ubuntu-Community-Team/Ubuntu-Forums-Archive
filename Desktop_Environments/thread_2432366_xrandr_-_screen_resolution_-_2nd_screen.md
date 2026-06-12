---
title: "xrandr - screen resolution - 2nd screen"
date: 2019-12-01
forum: Desktop Environments
---

### Post by Caleb.Robertson on 2019-12-01
So I on my laptop I have a custom external screen and when it comes on it has a crazy big screen resolution of 2048x1536 and that is the only mode it has in xrandr, 

Well I followed this how-to trying to get it to be close to my laptops screen resolution. 

[https://askubuntu.com/questions/377937/how-to-set-a-custom-resolution](https://askubuntu.com/questions/377937/how-to-set-a-custom-resolution)

But when I do that it come out like this, 


I am not new to linux but I am new to xubuntu so I haven't ever seen this before I figured maybe someone else has. 

[IMG]https://ubuntuforums.org/asset.php?fid=278744&uid=822278&d=1575291494[/IMG]

---

### Post by TheFu on 2019-12-02
For changing EDID/monitor provided resolutions, I like the **lxrandr** GUI tool.  EDID is how monitors have provided their capabilities to GPUs for a very long time, at least 15 years, since the VGA days.  HDMI, DVI, and DP support this too.

If you need to override the resolutions (called "modes" in X11), then manually creating an xorg.conf file will be needed.  Looking up the native resolution, refresh rates, horizontal and vertical sync rates will be needed. That data goes into the "modeline".  There are examples of X11 config files on the internet. I can post one of mine, but yours WILL be different and must be customized for the GPU, monitors, settings.  Copy/paste will not work.

I have know idea how Wayland does it. None. Sorry.

Perhaps someone else knows how to get the EDID information to work.  I've had to manually dump it because a DVI-i -to- VGA adaptor didn't pass it on to the GPU.  Previously, the system was using a VGA KVM without any issues, but the new GPU doesn't support VGA.

---

### Post by Caleb.Robertson on 2019-12-02
Thank you for your reply I will try tonight when I get home. 

If it helps this is the LCD to DisplayPort Adapter I used 
[http://abusemark.com/store/index.php?main_page=product_info&cPath=3&products_id=47](http://abusemark.com/store/index.php?main_page=product_info&cPath=3&products_id=47)

After thinking about it I am pretty sure that the resolution is hard wired into the adapter...considering it is printed on the board. I just haven't ever heard of a driver not accepting a lower resolution. Ill do some testing and report back.

---

### Post by Caleb.Robertson on 2019-12-02
So I tried lxrandr and now luck, I am not very good at making an xorg.conf from scratch I have really only done it with nvidia drivers. 

Is there a way you could post yours and I can edit it from there? 

Also I contacted the manufacturer and asked them if what I am trying is even possible.

---

### Post by TheFu on 2019-12-03
Here's a modeline:
```

Section "Monitor"
....
   Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync 
....
EndSection

```

See why you'll need all the technical details before starting?  That's 1 of 12 versions and the settings were provided by the monitor using an EDID dump program.  From the EDID, you can find a tool to make the modelines.

Overview of the steps:
* directly connect the monitor and some Linux computer.
* use a edid dump program to get the raw/binary information ```

$ man -k edid
get-edid (1)         - read-edid tools to retrieve and interpret monitor spec...
parse-edid (1)       - read-edid tools to retrieve and interpret monitor spec..
```
* move that dumped data in a file to the other computer
* figure out how to have the GPU use the edid file information, not whatever some adaptor is seeing:
```
Section "Device"
...
    Option "UseDisplayDevice" "DFP-0"
    Option "CustomEDID" "DFP-0:/etc/X11/xorg-monitor.dell-2412m.edid.raw"
...
EndSection
```

Check the /var/log/Xorg.0.log for errors and fix those.

I have doubts any of this will help with that converter.

---

### Post by Caleb.Robertson on 2019-12-03
[COLOR=#1D2228][FONT=&amp]Welp what I am trying to do is apparently not possible per the manufacture. I guess we can close this, thank you for your help.

Here is the reply i got from them.
[/FONT][/COLOR]> [COLOR=#1D2228][FONT=&amp]Hi there,[/FONT][/COLOR][COLOR=#1D2228][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1D2228][FONT=&amp]There is no "scaler" on that board, it will only support native panel resolution of 2048x1536.[/FONT][/COLOR]
[COLOR=#1D2228][FONT=&amp]Which is why it requires DisplayPort input.[/FONT][/COLOR]
[COLOR=#1D2228][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1D2228][FONT=&amp]Regards[/FONT][/COLOR]
[COLOR=#1D2228][FONT=&amp]
[/FONT][/COLOR]

---

### Post by TheFu on 2019-12-03
Only you can mark the thread as "SOLVED" using the thread tools button near the top.

---

