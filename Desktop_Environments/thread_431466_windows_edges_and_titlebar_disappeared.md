---
title: "windows edges and titlebar disappeared"
date: 2007-05-03
forum: Desktop Environments
---

### Post by jringoot on 2007-05-03
Hi,

I have an issue using the desktop effects in ubuntu 7.04 (apparently available after the upgrade from 6.10)
The windows edges and titlebar disappear.
To get them back I first had to uncheck both wobbly windows and workspaces on the cube.
Now to go back and forth it is not longer necessary to uncheck those... but I still loose my edges and titlebar when trying desktop effects.

remark: I have installed the NVIDIA graphics driver from their site (1.0-9755) this is IMHO the main difference from my other PC (which has an ATI card :-)). If I don't use that driver, display options appear very limited.


Anyone got a similar issue?
Anyone got a solution? 
A workaround?

---

### Post by jringoot on 2007-05-04
I still have the  same issue using beryl and selecting the Beryl window manager.
The cube works but the windows edges and titlebar disappear.
Also using Compiz manager, the  same issue, compiz is the one used to enable  the ubuntu desktop effects I believe, so this is mainly another way to demonstrate the previous described issue

Luckely when going back to the Metacity Window manager (or the KWin (kde windows manager))  everything the windows edges and titlebar reappear.
If 

I am unsure if this is a(n unreported) bug, an incompatibility with the NVIDIA driver/card or a faulty setting, haven't found any info yet.

Some conf details from Nvidi-serttings:

NVIDIA Driver Version: 1.0-9746
X Server Version Number: 11.0
X Server Vendor String: The X.Org Foundation
X Server Vendor Version: 7.2.0

GPU: GeForce 7600 GS
VBIOS Version: 05.73.22.51.06
Memory: 512 MB
Bus Type:  PCI Express 16X

I believe the rest is irrelevant: type of monitor and display settings.

except maybe: kernel image used: 2.6.20-15

---

### Post by xbalanque on 2007-05-06
Similar problem here on compiz in a recently upgraded to feisty system -- it is a 64bits, nvidia gtx8800.

Digging around I noticed gnome-window-decorator program is not present on feisty distribution. Is this a bug ?

---

### Post by glmeece on 2007-06-05
I have the same problem as well with an nVidia 6200 LE.  I can get the neat effects/eye-candy, but it's pretty much worthless if the window border widgets disappear.  It's a shame since I can tell the card would otherwise be able to handle everything else.
:(

---

### Post by Gabriev on 2007-06-05
try this and reboot ;)
[http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#My_windows_don.27t_have_any_decorations_.28title_bar.2C_resize_handles.2C_minimize.2Fmaximize.2Fclose_buttons.29](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#My_windows_don.27t_have_any_decorations_.28title_bar.2C_resize_handles.2C_minimize.2Fmaximize.2Fclose_buttons.29)

---

### Post by mikebeecham on 2007-11-19
The link is dead, and I am experiencing similiar issues?

Any further help would be gratefully received.

---

### Post by larryfroot on 2007-11-29
I went into System > Preferences > GL Desktop and unchecked the Enable GL Desktop box. Window widgets returned instantly. A relief as not only did I not get window widgets but apps were loading on the extreme far left top corner of my screen (zero x, zero y) or even partly off screen (like synaptic - of all apps I needed the most!). Also alt + drag was spannered as well, so couldn't simply drag windows back onto the full desktop! But anyways, the above worked for me.

Will now be a lot less wildly experimental when it comes to compiz. Just a tweak here and a tweak there....step lightly on a tigers tail, my friends.....

---

