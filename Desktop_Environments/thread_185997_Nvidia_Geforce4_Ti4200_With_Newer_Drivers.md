---
title: "Nvidia Geforce4 Ti4200 With Newer Drivers"
date: 2006-06-01
forum: Desktop Environments
---

### Post by mesapiegrande on 2006-06-01
I want to report an issue I'm having with the current NVIDIA drivers and my Geforce4 Ti4200.

Dapper installs just fine and is beautiful IMO.  As is the standard practice the default device driver is "nv".  I attempted to install the nvidia drivers using the post at [Ubuntu Forums.]("http://www.ubuntuforums.org/showthread.php?t=75074") I have used both methods 1 and 2 in the attempt to enable 3D acceleration.

Upon installing the newer drivers (anything from 7676 to 8762), configuring the necesary files, and restarting the x-server (or rebooting, I tried both) the following occurs.  Once the x-server restarts I get an image on my screen that is reduced.  It is like running an 800x600 in the upper left corner on a 1024x768 screen.  The right hand side is dark and the portion below the 'normal' 800x600 box is the top of the same 800x600 section.

I have verified this running Suse 10.1 and I get the same results upon enabling the new driver.

Using method 2 of the aforementioned process with the 7667 drivers does yield a normal screen with 3D acceleration enabled.  From what I understand this was the driver that generally installed on Breezy, which always worked for me.  I guess I can just call myself lucky but I wanted to see if anyone else had similar problems and if they were able to get it fixed somehow.

I also plan to post this in the NVIDIA Linux discussion forum.

Mesapiegrande ](*,)

---

### Post by tseliot on 2006-06-01
[QUOTE=mesapiegrande]I want to report an issue I'm having with the current NVIDIA drivers and my Geforce4 Ti4200.

Dapper installs just fine and is beautiful IMO.  As is the standard practice the default device driver is "nv".  I attempted to install the nvidia drivers using the post at [Ubuntu Forums.]("http://www.ubuntuforums.org/showthread.php?t=75074") I have used both methods 1 and 2 in the attempt to enable 3D acceleration.[/QUOTE]
That guide is for Ubuntu Breezy. The following is for Dapper:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

[QUOTE=mesapiegrande]Upon installing the newer drivers (anything from 7676 to 8762), configuring the necesary files, and restarting the x-server (or rebooting, I tried both) the following occurs.  Once the x-server restarts I get an image on my screen that is reduced.  It is like running an 800x600 in the upper left corner on a 1024x768 screen.  The right hand side is dark and the portion below the 'normal' 800x600 box is the top of the same 800x600 section.

I have verified this running Suse 10.1 and I get the same results upon enabling the new driver.

Using method 2 of the aforementioned process with the 7667 drivers does yield a normal screen with 3D acceleration enabled.  From what I understand this was the driver that generally installed on Breezy, which always worked for me.  I guess I can just call myself lucky but I wanted to see if anyone else had similar problems and if they were able to get it fixed somehow.

I also plan to post this in the NVIDIA Linux discussion forum.

Mesapiegrande ](*,)[/QUOTE]
Try adding this option to the Section device of your xorg.conf
```
Option "UseEDID" "false"
```

Then get to the Section Screen of the same file:

```
Section "Screen"
    Identifier  	"Screen[0]"
    Device      	"Device[0]"
    Monitor     	"Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024[COLOR="Red"]_75[/COLOR]" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024[COLOR="Red"]_75[/COLOR]" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
SubSection "Display"
                Depth           1
                Modes           "1280x1024_[COLOR="Red"]75[/COLOR]" "1024x768" "800x600" "640x480"

```

and make sure that the resolution you need to use (1280x1024 in my case) has the refresh rate beside it. The part in red is the refresh rate. In the example I set the resolution to 1280x1024 at 75hz ( = 1280x1024_75).

---

### Post by Zdravko on 2006-06-01
This is important for me. I have a "GeForce4 Ti 4200 AGP 8x". Via "dpkg-reconfigure xserver-xorg" I managed 85Hz@1024x768. So far, so good. But running "glxgears" was very slow. Do I need to enable manually hardware acceleration?

---

### Post by jackqu7 on 2006-06-01
[QUOTE=tseliot]
...and make sure that the resolution you need to use (1280x1024 in my case) has the refresh rate beside it. The part in red is the refresh rate. In the example I set the resolution to 1280x1024 at 75hz ( = 1280x1024_75).[/QUOTE]
Thanks for this, I've been having a similar problem all day with my ti4200 but this solved it right away :)

---

### Post by tseliot on 2006-06-01
[QUOTE=Zdravko]This is important for me. I have a "GeForce4 Ti 4200 AGP 8x". Via "dpkg-reconfigure xserver-xorg" I managed 85Hz@1024x768. So far, so good. But running "glxgears" was very slow. Do I need to enable manually hardware acceleration?[/QUOTE]
Did you install Nvidia's proprietary driver?
If not, please try my guide:
[http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia]("http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia")

---

