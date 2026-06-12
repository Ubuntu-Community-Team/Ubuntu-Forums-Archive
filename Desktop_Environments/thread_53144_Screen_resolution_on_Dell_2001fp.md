---
title: "Screen resolution on Dell 2001fp"
date: 2005-07-30
forum: Desktop Environments
---

### Post by john deere on 2005-07-30
I posted this in the Hardware section yesterday. That part of the forums seems like ghost town though, so I'll give it a shot here instead. Here we go:

Hoary 5.04 AMD64 on a system with a GeForce 6600 GT and a 20-inch Dell 2001 FP with the native resolution of 1600x1200. I've tried to change just about anything in the xorg.conf file but I can't seem to get the res above 1024x768. Below are my current settings. Any help would be dearly appreciated.

Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
Driver "nv"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 31-80
VertRefresh 60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1600x1200" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

### Post by bored2k on 2005-07-30
1. Execute the commands in Terminal mode (Applications -> System Tools -> Terminal)
2. sudo dpkg-reconfigure xserver-xorg
* Select those you want *
3. Reboot

---

### Post by heimo on 2005-07-30
Add this to your monitor section:
```
Modeline "1600x1200"   162   1600 1664 1856 2160   1200 1201 1204 1250  +hsync +vsync
``` 

Check my other instructions:
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

Post errors in your xorg.log (exact filename in the post linked abowe)

Hopefully this gets you closer to 1600x1200! (I'd love to have one of those displays!)

---

### Post by john deere on 2005-07-30
Thanks for the replies, bored2k and heimo.

Well, the 2001fp is a sweet monitor and most of all great bang for the buck. Unfortunately I can't enjoy it fully due to these resolution problems...

Anyway, I reconfigured the x-server, re-booted and got a xorg.conf file with the desired resolution (1600x1200), but I still had no such option in the settings>resolutions section. 

Ok, so I cut&pasted the modeline line heimo provided into the monitor section in my .conf, saved and re-booted. Guess what? X-server can't start. I'm a newbie so I have no idea  what to do when I see that flicking cursor on a black background. "Do you want to see a detailed error report?" Yeah, I guess. But I have no idea what to do of it.

Fortunately I set up dual boot so I can access these forums with XP. Please help.

---

### Post by john deere on 2005-08-01
I finally got xserver up and running again, but I still can't get the resolution up to 1600x1200. I have attached my xorg.log. Being a newbie, I really don't know how to interpret all this info. I hope someone here can.

---

### Post by heimo on 2005-08-01
Thanks for the log file, I'll have a look at it this evening (~7-8 hours), if the problem still exists. In the mean while, if you have no other ideas, I'd try tweaking HorizSync and VertRefresh lines (maybe different driver too, vesa, perhaps? just to get more information on this subject).

---

### Post by john deere on 2005-08-01
Problem solved! Ahh, how sweet to be back in 16x12 :)

For future users with the same problem, here's what I did:

I had the wrong video driver for my 6600 GT so I followed the instructions here: [Nvidia driver](http://ubuntuguide.org/#installnvidiadriver) 

That didn't change much right away though because my xorg.conf was back to default with 1024x768 as highest res. Ok, I added 1600x1200 under the Screen section of the file and rebooted. No change, still no 16x12 option. 

Opened up xorg.conf again and changed HorizSync	and VertRefresh to 31-80 and 56-76, respectively. Rebooted and voila!

To conclude: Initially I changed my .conf to the correct settings, but since I had the wrong driver it didn't work. Than I had the right driver but wrong setting and that obviously didn't work either. Correct driver+ correct settings in the xorg.conf is the way to go(doh).

Thanks for the input guys.

---

### Post by heimo on 2005-08-01
Great to hear you got it solved! Believe me, next time is easier. :D

---

### Post by john deere on 2005-08-01
Hi again. Still one problem left. (Two actually, but that's for another post.)

Like I said in the earlier post, I can now access 1600x1200 from the drop down menu and that's nice. The problem is that after every reboot, Gnome (xserver?) starts in 1024x768 and I have to go System>Settings>Screen Resolution to change to 1600x1200. I've ticked the "as default"-box, but that doesn't help - it still defaults to 1024x768 after reboot.

Ideas?

*Edit: I just noticed there was a live thread on the same subject, sorry about that. That thread didn't solve the problem for me though, but I'll delete this post if prompted. *

---

### Post by heimo on 2005-08-01
In xorg.conf is the 1600x1200 option at the beginning of Screen->Display->Modes line?

EDIT: Oh, on your first post it seems to be. If you don't need the other resolutions, you can try removing the other resolutions.

---

### Post by john deere on 2005-08-02
I don't need the lower resolutions so I guess I could remove them. I'll try that tonight. Thanks.

---

### Post by john deere on 2005-08-02
Update: I deleted every resolution in xorg.conf except 1600x1200, but Gnome still starts at 1024x768 and I have to up the resolution via the drop down menu after every reboot. 

Could this be a Gnome problem rather than xserver? The reason I'm asking is because the log in screen is 1600x1200 but when the desktop loads it goes back to 1024x768.

Suggestions?

---

### Post by heimo on 2005-08-02
[QUOTE=john deere]Update: I deleted every resolution in xorg.conf except 1600x1200, but Gnome still starts at 1024x768 and I have to up the resolution via the drop down menu after every reboot. 

Could this be a Gnome problem rather than xserver? The reason I'm asking is because the log in screen is 1600x1200 but when the desktop loads it goes back to 1024x768.

Suggestions?[/QUOTE]

I'm quite lost. No idea why it would ever do that. :-\ But I have a shortcut for you - this may make living with that quirk a little easier. ctrl+alt++ or ctrl+alt+- (plus or minus on numpad) changes through available resolutions - no need to use menu for this.

---

### Post by john deere on 2005-08-02
Ok, it's not a major problem anyway. Thanks for tip and taking the time trying to help.

---

### Post by john deere on 2005-08-04
Fixed! Here's how (cut& pasted):

> do the following:

Click the applications menu, select Configuration Editor from the System Tools menu.

Now go to the following key (location):

/desktop/gnome/screen/default/0/

In the right pane you should see a key called 'resolution', double click this and enter your preferred resolution in the value box.

restart

You should find that everytime u login your preferred resolution is in use.

From this thread: [How to set default resolution when tweaking xorg.conf doesn't help](http://www.ubuntuforums.org/showthread.php?t=47601&highlight=default+resolution)

---

### Post by heimo on 2005-08-04
Great! Thanks, I'll update my unofficial [FAQ]("http://ubuntuforums.org/showpost.php?p=129379&postcount=21").

---

