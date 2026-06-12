---
title: "Hello World!"
date: 2009-02-27
forum: General Help
---

### Post by OxentroT on 2009-02-27
Hello Everyone.
I am new to the wonderful world of linux as well as the Ubuntu forum and I have installed Ubuntu 8.10intrepid it alongside my windows vista OS on an HP slimline. I like it and I look forward to switching over completely someday. However it seems I have a lot to learn I now get an error after activating the NVidia drivers for a more palatable resolution(monitor is LGflatronL1717s). After restart it tells me 'OUT OF RANGE 81.0kHz / 65Hz' need I reinstall, dust myself off and try again?
 I apologize for this thread being at all amess as I have been up all night and too soon off to work. But any light on the situation would be appriceated. 


Thank You!

---

### Post by 3rdalbum on 2009-02-27
No need to reinstall Ubuntu.

Press Control-Alt-F2 to switch to a virtual terminal; your monitor should turn on again at this point and you will be at a text-only screen.

Log into this terminal using your username and password. Then type the following:

```
sudo nano /etc/X11/xorg.conf
```

This opens the graphical display configuration file for editing.

In this file, under Section "Device", you need to add the following line:

```
     Driver     "nv"
```

Or if you already have Driver   "nvidia", change it to nv.

Press Control-X to exit, Y to save and Enter to confirm. Then type this:

```
sudo reboot
```

You will have your graphical display back, albeit with 2D drivers rather than 3D drivers. In the file you just edited, under SubSection "Display" there is a bit where you can add Modes - in other words, you can specify what resolution and refresh rate your monitor can handle. You will need to do this, because the Nvidia driver doesn't seem to detect your monitor properly.

When you have put the correct mode in, change the Driver part from "nv" to "nvidia" again, reboot and you should have a fully 3D-accelerated display.

I am not sure of the actual format you specify video modes in. I believe your Modes section should look something like this:

```
SubSection    "Display"
      Modes      "1280*1024@50Hz" "800*600@50Hz"
EndSubSection
```

---

### Post by OxentroT on 2009-03-04
Thank you for that.:o will try next time

---

