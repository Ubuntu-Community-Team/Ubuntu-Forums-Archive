---
title: "Howto: Inspiron 1420 (nvidia gfx) switching resolutions/displays with Fn-F8"
date: 2007-12-08
forum: Dell  Ubuntu Support
---

### Post by closey on 2007-12-08
NOTE: After using this method for a few days I've found some problems with:

. Restarting without the external monitor attached (the resolutions for the LCD change to 800x600 and other craziness)
. Closing the lid on the laptop - the resolutions other than the current one seem to disappear

No idea why these problems are happening but you might want to be aware of them before you go all all implementing what I have below :).



Hi guys,

I didn't have any luck 'out of the box' with the Fn-F8 screen switching button in Fiesty or Gutsy with my Inspiron 1420, so I decided to do something about it. :)

If this guide doesn't work please send us a PM. Remember you need to have the latest Nvidia drivers installed (I installed mine using [Envy](http://albertomilone.com/nvidia_scripts1.html)), and of course have an Nvidia GPU in your laptop!

So I've been using the 'MetaModes' in the Nvidia driver to set up a few different resolutions:

1280x800 - direct to the laptop LCD only
1680x1050 - direct to the external display only
2960x1050 - 'twinview' style setup - main screen being the external display

These resolutions were created in the nividia-settings program, but the resulting screen in my xorg.conf looks like this:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1680x1050_60.00_rb +1280+0, DFP: nvidia-auto-select +0+0; CRT: 1680x1050_60.00_rb +0+0, DFP: NULL; CRT: NULL, DFP: nvidia-auto-select +0+0"
EndSection
```

Yours will probably look different. I highly suggest using the nvidia-settings program in 'Advanced' mode as root to generate this for yourself. You may have to restart X after saving the settings to the the /etc/X11/xorg.conf file. (Ctrl-alt-backspace does the trick.)

This exposes the three resolutions to the 'xrandr' program so that you can change resolutions on the fly. e.g. you can go 'xrandr -s 0' to use the first resolution or 'xrandr -s 1' to use the second, etc. We'll use this program to cycle through the resolutions.

I've made a small script to automate cycling through the resolutions. 

```
#!/bin/bash
if [ -f ~/.changeres ]
then
	. ~/.changeres
fi

if [ -z $INDEX ]
then
	INDEX=-1
fi

let INDEX "INDEX += 1"

if xrandr -s $INDEX
then
	echo "OK"
else
	INDEX=0
	xrandr -s $INDEX
fi

echo "#!/bin/bash" > ~/.changeres
echo "INDEX=$INDEX" >> ~/.changeres
```

As root, save the code above into a file /usr/local/bin/changeres.sh . You'll also want to 'chmod 755 /usr/local/bin/changeres.sh'.

(The dodgy bit is I couldn't be bothered figuring out how to use a regex to get the current resolution index out of xrandr. Instead I'm using a file in the user's home directory to store the last index used and incrementing it each time. Someone could probably help me fix this? :) ).

Now if you want to test out this script all you have to do is type 'changeres.sh' at a terminal window (you shouldn't even need to be root). Each time you run it you should swap between the different resolutions that you configured in nvidia-settings. If this doesn't work you probably have something set up wrong.


The next bit is setting up the keyboard shortcut. The key sequence we want to use is Fn-F8 as it has CRT/LCD written on it. This key has already been mapped in the standard Ubuntu install to /etc/acpi/videobtn.sh (via /etc/acpi/events/videobtn)

You should make /etc/acpi/videobtn.sh look like this:
```
#!/bin/bash
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_VIDEOMODECYCLE
```

We're not done yet! We still have to link that shortcut key to the /usr/local/bin/changeres.sh script. I use xbindkeys for this - I think there are some other gnomey type things to do this for you but I haven't used them.

You'll want to install 'xbindkeys' and 'xbindkeys-config':
```
sudo apt-get install xbindkeys xbindkeys-config
```

Now run the xbindkeys-config program as your user account. You should now add a keyboard shortcut for 'changeres' and hit the 'Get Key' button. When the small plain white window pops up, hit the Fn-F8 key sequence. This should close the white window and "NoSymbol | m:0x0 + c:249" should be in the 'Key' field. In the 'Action' field you should enter /usr/local/bin/changeres.sh .

Hit 'Save & Apply & Exit', which will save your settings to the ~/.xbindkeysrc file.

You now have to set xbindkeys to run at log in. I did this in the 'System -> Preferences -> Sessions' screen. I added a 'Startup Program' for xbindkeys.

And that should be it. Try it out by hitting Fn+F8 together.

---

### Post by Ranokivio on 2007-12-12
Just a quick response to thank you for your work! I was trying  to achieve this for days before  I found your thread!
I have a dell M1330, gutsy and a Nvidia 8400m gs and itis now  working great!

There is maybe one more things I would like to get at the moment...I would like my monitor to be automatically detected when I plug it> I have to restart X( or the laptop) at the moment. Any ideas?
Another thing which is not working that great is the full screen with video using adobe flash player. One part of the screen is missing on the monitor (1280*1024) and the size of the window is the same as on my laptop (1280*800) (i.e. not full screen )

---

### Post by closey on 2007-12-12
> **Ranokivio said:**
> I would like my monitor to be automatically detected when I plug it> I have to restart X( or the laptop) at the moment. Any ideas?
No idea on how to do this at the moment :/. I too find it annoying when the resolutions available go to crap when you boot up with the monitor unplugged :/. Restarting X or resetting the display with nvidia-settings is the way I get around it (you don't have to save the changes to the xorg.conf file, so it hopefully won't screw it for next reboot).

> **Ranokivio said:**
> Another thing which is not working that great is the full screen with video using adobe flash player. One part of the screen is missing on the monitor (1280*1024) and the size of the window is the same as on my laptop (1280*800) (i.e. not full screen )

I've had no luck running video with the flash player fullscreen... I usually just end up crashing firefox :lol:

---

### Post by Ranokivio on 2007-12-12
> **closey said:**
> No idea on how to do this at the moment :/. I too find it annoying when the resolutions available go to crap when you boot up with the monitor unplugged :/. Restarting X or resetting the display with nvidia-settings is the way I get around it (you don't have to save the changes to the xorg.conf file, so it hopefully won't screw it for next reboot).:

Actually, the resolution of my laptop is just fine when I boot up with the monitor unplugged. Have you tried this in your Xorg file?

 Option         "metamodes" "CRT: 1280x800 +0+0, DFP: nvidia-auto-select +0+0; CRT: 1280x1024 +0+0, DFP: nvidia-auto-select +0+0"
> **closey said:**
> 
I've had no luck running video with the flash player fullscreen... I usually just end up crashing firefox :lol:

Have you installed the last adobe flash player? 

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by closey on 2007-12-12
Ah yes the resolution is fine when I boot up with the monitor unplugged, it's more that if I plug the monitor in and then Fn-F8 it will cycle between some resolutions (that I hadn't actually defined) for the inbuilt LCD. It might have something to do with my xorg.conf though...

And no I haven't tried the latest flash player :). I'll give it a go, cheers!

---

### Post by Ranokivio on 2007-12-13
> **closey said:**
> Ah yes the resolution is fine when I boot up with the monitor unplugged, it's more that if I plug the monitor in and then Fn-F8 it will cycle between some resolutions (that I hadn't actually defined) for the inbuilt LCD. It might have something to do with my xorg.conf though...


OK, I see what you mean now...Same thing here.

---

### Post by Guranic on 2007-12-13
Jiihaa! Got it work with this HowTo! And I have Asus A6K laptop (sempron mobile, nvidia go 6200) Thanks! Hope it will work with projectors also. I got it work with my lcd display at home...

---

### Post by closey on 2007-12-13
After a bit more research it seems the hot key switching *should* work by default with the Nvidia drivers, but for some reason doesn't. See here for info [http://www.nvnews.net/vbulletin/showthread.php?t=68382](http://www.nvnews.net/vbulletin/showthread.php?t=68382)

Hope it gets fixed soon, then maybe the hot plugging of devices might work (fingers crossed :) )

---

### Post by Ranokivio on 2007-12-14
the problem with the hotpluging seems to come from the xrandr 1.2 which is not (yet) supported by the graphic card... even with the new nvidia  beta driver (169.04) I have recently installed.
[http://www.nvnews.net/vbulletin/showthread.php?t=92648](http://www.nvnews.net/vbulletin/showthread.php?t=92648)
[http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

---

### Post by jr0ck on 2008-02-05
First off, thank you for this post! I've been wanting to do this for awhile and couldn't find anything to allow me to do it. I'm ALMOST there, but there are a few snags.

First snag: xbindkeys won't start, no matter what. From terminal I type "xbindkeys" and press Enter and it never starts. Looking in System Monitor (with View -> All Processes chosen) and it never loads. However, the xbindkeys-config loads and saves the file and everything is fine from that end, except when I click "Save & Apply & Exit", the terminal spits out:
```
xbindkeys: no process killed
Exit
```
Also, if I start xbindkeys in verbose mode, I get this:
```
~$ xbindkeys -v
displayName = :0.0
rc file = /home/jr0ck/.xbindkeysrc
rc guile file = /home/jr0ck/.xbindkeysrc.scm
getting rc guile file /home/jr0ck/.xbindkeysrc.scm.
initializing guile fns...
ERROR: In procedure read:
ERROR: Unknown # object: #\space

Some deprecated features have been used.  Set the environment
variable GUILE_WARN_DEPRECATED to "detailed" and rerun the
program to get more information.  Set it to "no" to suppress
this message.

```
So something's wrong with my xbindkeys program or the guile libraries it depends on. I've tried reinstalling both xbindkeys and guile but the problem remains. Any ideas on that one?

----------------------------------------------------------
2nd problem:
I configured my 3 metamodes in nvidia-settings and saved it to xorg.conf. I can get two of the configurations to load using both "xrandr -s 0" (or "xrandr -s 1") and using the changeres.sh command we created in this tutorial, but for some reason the third config isn't seen by xrandr and gives this error:
```
Size index 2 is too large, there are only 2 sizes
```
When I simply run xrandr, I get this:
```
Screen 0: minimum 1680 x 1050, current 3360 x 1050, maximum 3360 x 1050
default connected 3360x1050+0+0 0mm x 0mm
   3360x1050      50.0* 
   1680x1050      51.0     52.0 
```
As you can see, there really are only two sizes listed, which gives me my problem. Both my laptop LCD and external monitor have a native resolution of 1680x1050, so my xorg.conf looks like this:
```
"metamodes" "CRT: 1680x1050 +0+0, DFP: nvidia-auto-select +1680+0; CRT: NULL, DFP: nvidia-auto-select +0+0; CRT: 1680x1050 +0+0, DFP: NULL"
```
I want it to cycle like thus: Twinview -> Built-in LCD -> External LCD only
But xrandr thinks that since my built-in LCD and external have the same resolution, they are the same choice and doesn't give me the option. Please note that I can swap the order of my last two choices in xorg.conf so that it cycles from Twinview to my external LCD and back to Twinview, or from Twinview to built-in LCD and back to Twinview, but it never can cycle through all three options, the 3rd metamode is simply ignored by xrandr.

Btw, I'm on a Dell Vostro 1500 using Ubuntu 7.10 Gutsy. Thanks in advance for any help.
EDIT: I realized I don't have the latest Nvidia drivers, as I am using the default Gutsy "Restricted Drivers" (which show version 100.14.19). I'm going to disable those and install "envy" and get the latest drivers and try this again.

---

### Post by jr0ck on 2008-02-05
Okay, I installed the latest Nvidia drivers (169.09) using Envy and all the same problems still persist. Nothing has changed, so if anyone has any insight into the problems I listed in the previous post, that'd be great. Thanks!

---

