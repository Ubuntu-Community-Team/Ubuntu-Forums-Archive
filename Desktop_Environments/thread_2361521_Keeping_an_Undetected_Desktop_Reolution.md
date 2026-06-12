---
title: "Keeping an Undetected Desktop Reolution"
date: 2017-05-17
forum: Desktop Environments
---

### Post by rolfUser on 2017-05-17
I use an Insignia 27" HDTV w/VGA output as my computer monitor. I also have Ubuntu 16.04 LTS dual-booted with Windows 10 and while the full 16:9 aspect ratio is utilized on Windows, the resolutions detected under Ubuntu are:
[LIST]
[*]1024 x 768 (4:3)
[*]800 x 600 (4:3)
[/LIST]
Well I found a solution to utilize the entire screen. I chose 1280 * 720 screen resolution and applied as you see here to the terminal:
```

sudo cvt 1280 720 60

sudo xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync

sudo xrandr --addmode VGA-0 1280x720_60.00

```
The result of this code is successful for the time being. The entire screen is used up and I get extra space to wok with.
The problem is that this new screen resolution goes away after a restart. There was a video tutorial ([https://youtu.be/LiP-YqtZoNQ](https://youtu.be/LiP-YqtZoNQ)) on how to keep the resolution. I followed instructions, but did not get the intended result. The screen just goes back to 4:3 and an error message pops up on start up. I cannot create a screenshot or use the computer until I X out the message. 
From there I can just re-input the above code and get the same result.

[https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions)
In spite of the resources, there's not much progress. It seems the instructions are not meant for my circumstances since mine are probably not that popular.
How do you keep the desired screen resolution in my case?

---

### Post by Bashing-om on 2017-05-18
rolfUser; Well, well .

> 
How do you keep the desired screen resolution in my case?

IRT: [https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions)
Have you tried making up the ~/.xprofile and setting it as executable ?

Post back:
```

xrandr

```
so that "we" know the outputs and the resolutions available.
In a simple config, seems the ~/.xprofile is the way to go.

But in linux
[INDENT][INDENT][INDENT]many paths to an end
[/INDENT][/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-18
input:
```
xrandr
```
output:
```
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 16384 x 16384DVI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1280x720+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00  
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
   1280x720_60.00  59.86*
```
> **Bashing-om said:**
> rolfUser; Well, well .
IRT: [https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions)
Have you tried making up the ~/.xprofile and setting it as executable ?

No I have not. That involves right-clicking a file and adjusting something under permissions, right? You'd have to walk me through it.

---

### Post by Bashing-om on 2017-05-18
rolfUser; Welp; .....

Let's give this a try:

make up the file:
```

touch  ~/.xprofile 

```
( yeah could also create the new file in the gedit text editor )

Open the file in gedit:
```

gedit  ~/.xprofile 

```
copy and paste into this file:
xrandr --output VGA-0 --mode 1280x720

save the file in gedit.
Make the file executable:
```

chmod +x ~/.xprofile

```

reboot to see the effect .

[INDENT][INDENT]maybe, YeS
[/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-18
After
```
gedit ~/.xprofile
```

output:```

(gedit:30042): GtkSourceView-WARNING **: could not parse scheme file '/usr/share/gtksourceview-3.0/styles/blue_dream.xml'


(gedit:30042): GtkSourceView-WARNING **: no color named 'white'

```
I could not type anything into the terminal until the gedit file was closed, which I think is normal. I got a new error message after restarting. No changes.

---

### Post by rolfUser on 2017-05-18
[ATTACH=CONFIG]275164[/ATTACH]
The new error message. It appears on startup, before the desktop and I cannot proceed to the desktop until I click OK.



[ATTACH=CONFIG]275165[/ATTACH]The usual error message that has been on startup ever since I created the file to keep the undetected resolution. I cannot proceed to use the computer or create a screenshot until I navigate the cursor over to the top of the message, move the window, and X out the error message. From there, I can just type up on the terminal until I get the old commands I used to get the 1280x720 resolution.

---

### Post by Bashing-om on 2017-05-18
rolfUser; Ouch !

Here I no not know what to advise . We best await those with the greater experience.

[INDENT][INDENT]a know-it-all I am not
l[/INDENT][/INDENT]

---

### Post by Autodave on 2017-05-18
I am wondering if you have the correct video driver for you card. Do you know what video card you have? Have you installed any drivers for it? Have you tried going into *Settings -> **Software & Updates -> Additional Drivers *and see if Ubuntu makes a suggestion?

---

### Post by rolfUser on 2017-05-18
Just tell me what you want me to input into the machine so you can help me to devise a solution. Otherwise, I'm thinking a fresh upgrade to 17.04 might.... only remove the error messages. Of course I could just buy a computer monitor, but you know, money and it's not a priority right now. Besides, we're having fun here.

---

### Post by Autodave on 2017-05-19
You can buy all the monitors you want, but until you have the correct video driver for your particular video card, you are not going to get any better resolution. As I posted before (and I am sorry if I wasn't clear) go to *Settings -> **Software & Updates -> Additional Drivers. *That will search for additional drivers that you machine can/could/should use.  We are interested in any video driver that it finds and recommends. 

Assuming that it finds video driver(s), pick the recommended one and allow it to install it. Then see what your video does.

---

### Post by Bashing-om on 2017-05-19
@Autodave; Thanks for jumping in here ./

The correct driver is loaded :
see: [https://ubuntuforums.org/showthread.php?t=2361283&p=13645891#post13645891](https://ubuntuforums.org/showthread.php?t=2361283&p=13645891#post13645891)
```

lspci -nnk | grep -iA3 vga
output:
Code:
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330] [1002:9832]    Subsystem: Hewlett-Packard Company Kabini [Radeon HD 8330] [103c:2b18]
    Kernel driver in use: radeon
    Kernel modules: radeon

```

I had expected the .xprofile file to be effective . Reckon 16,04 (systemd) handles the config different than that of upstart ?
Real strange that from terminal the resolution change is good .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by rolfUser on 2017-05-19
> **Autodave said:**
> You can buy all the monitors you want, but until you have the correct video driver for your particular video card, you are not going to get any better resolution. As I posted before (and I am sorry if I wasn't clear) go to *Settings -> **Software & Updates -> Additional Drivers. *That will search for additional drivers that you machine can/could/should use.  We are interested in any video driver that it finds and recommends. 

Assuming that it finds video driver(s), pick the recommended one and allow it to install it. Then see what your video does.
[ATTACH=CONFIG]275187[/ATTACH]

---

### Post by yetimon_64 on 2017-05-20
> **Bashing-om said:**
> ...Real strange that from terminal the resolution change is good ...


If the commands work OK in terminal and the .xprofile adjustments fail, I'd try putting the original commands in the /etc/rc.local file so as to run the commands each boot up. May be a bit of a "hack" and not the proper way of setting the resolution, but with using a TV as the monitor it may be worth trying to see whether the resolution will stick that way.

@ OP, you could try putting the commands that work in the terminal you posted in your first post in the file /etc/rc.local; without the sudo command as /etc/rc.local is executed as root each start up.
You can edit /etc/rc.local with the command ...
```
sudo -H gedit /etc/rc.local
```
Then add the commands so the rc.local file looks like ...
```
!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

cvt 1280 720 60
xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
xrandr --addmode VGA-0 1280x720_60.00

exit 0
```
As I note above to Bashing-om this is a bit of a hack to set the resolution manually on each start up but by using the /etc/rc.local file. It would be a much better idea to find the correct way to set the resolution with the driver if possible, but in the mean time this may be worth a try; it may possibly work from here if you can set it from terminal once booted into the system. Good luck, yeti.

---

### Post by rolfUser on 2017-05-20
Maybe I should have said something sooner. Thing is, there's already a format for the file you need to create to keep the resolution on your PC. The links are covered here:
[https://youtu.be/LiP-YqtZoNQ](https://youtu.be/LiP-YqtZoNQ)
[https://wiki.ubuntu.com/X/Config/Res...ed_resolutions]("https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions")

I just thought that the wording on the file had to be adjusted... tailored to my PC. Instructions seen are just some general cookie-cutter solution, but this is doable.
I'm not doubting you, Yeti. I'm just interested in a second or third opinion before moving forward on your instruction.

---

### Post by Autodave on 2017-05-21
How is the monitor connected to the TV: what cable: VGA, DVI, HDMI, etc?

---

### Post by rolfUser on 2017-05-21
> **autodave said:**
> how is the monitor connected to the tv: What cable: Vga, dvi, hdmi, etc?
vga

---

### Post by Autodave on 2017-05-21
That could be limiting you. Some cheaper VGA cables do not have the extra wire i9n them to report the monitor to the video card. On my own system, VGA would only allow me to go to 780. DVI or HDMI allowed me to go to 1960 (?) or something close to that.

---

### Post by rolfUser on 2017-05-21
> **yetimon_64 said:**
> If the commands work OK in terminal and the .xprofile adjustments fail, I'd try putting the original commands in the /etc/rc.local file so as to run the commands each boot up. May be a bit of a "hack" and not the proper way of setting the resolution, but with using a TV as the monitor it may be worth trying to see whether the resolution will stick that way.

@ OP, you could try putting the commands that work in the terminal you posted in your first post in the file /etc/rc.local; without the sudo command as /etc/rc.local is executed as root each start up.
You can edit /etc/rc.local with the command ...
```
sudo -H gedit /etc/rc.local
```
Then add the commands so the rc.local file looks like ...
```
!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

cvt 1280 720 60
xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
xrandr --addmode VGA-0 1280x720_60.00

exit 0
```
As I note above to Bashing-om this is a bit of a hack to set the resolution manually on each start up but by using the /etc/rc.local file. It would be a much better idea to find the correct way to set the resolution with the driver if possible, but in the mean time this may be worth a try; it may possibly work from here if you can set it from terminal once booted into the system. Good luck, yeti.

input:
```
sudo -H gedit /etc/rc.local
```
I copied and pasted the text to the file as shown. Output is here:
```
(gedit:2831): GtkSourceView-WARNING **: could not parse scheme file '/usr/share/gtksourceview-3.0/styles/blue_dream.xml'


(gedit:2831): GtkSourceView-WARNING **: no color named 'white'


(gedit:2831): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


** (gedit:2831): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported


** (gedit:2831): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported


** (gedit:2831): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported



```

---

### Post by rolfUser on 2017-05-21
Well after restarting and even shutting down to start again, there are no changes to the screen resolution. I get the same error messages, but at least I can still program the resolution onto the screen.

If nothing else, I'd like to know how to edit those files back to normal -- I got tips from more than one person.
Maybe I am thinking a fresh upgrade to 17.04 will rid the error messages if that doesn't work.

I used to run 14.04 and I remember that when the PC was upgrading, I think got prompted twice asking me if I want to use the same installation files or replace them with new ones. I was indecisive at the time, but I think if I get prompted now, I will choose to refresh on everything.

Any more ideas?

---

### Post by rolfUser on 2017-05-23
> **Autodave said:**
> You can buy all the monitors you want, but until you have the correct video driver for your particular video card, you are not going to get any better resolution. As I posted before (and I am sorry if I wasn't clear) go to *Settings -> **Software & Updates -> Additional Drivers. *That will search for additional drivers that you machine can/could/should use.  We are interested in any video driver that it finds and recommends. 

Assuming that it finds video driver(s), pick the recommended one and allow it to install it. Then see what your video does.
[ATTACH=CONFIG]275260[/ATTACH]
Yes. I posted this already. But never mind  going back forth abouit repeating... whatever.
Just where do we go from here??

---

### Post by rolfUser on 2017-05-26
[https://www.amazon.com/Universal-Converter-Support-Adapter-SY-ADA31025/dp/B006FILNV6](https://www.amazon.com/Universal-Converter-Support-Adapter-SY-ADA31025/dp/B006FILNV6)

---

