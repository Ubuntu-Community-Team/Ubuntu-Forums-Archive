---
title: "No Output from RTX 3080"
date: 2021-09-09
forum: Gaming &amp; Leisure
---

### Post by zeitrif on 2021-09-09
Hello Ubuntu Forum, beginner user here.

I've got a server box loaded with an Intel S2600ST, an Intel Xeon Silver 4216, and an RTX 3080, and either Ubuntu 20.04.03 or 21.04.
When I've had the LTS loaded, it would recognize my nVidia as a generic device, however 21.04 directly identifies it as a 3080.

I currently have this system connected with a VGA from the baseboard, which outputs fine. During the OS Boot, my main monitor (Or at least, what I'd like to use) over DisplayPort will activate with the Ubuntu loading animation, and then once that's completed, turn right back off.

I've been working on this for probably 10 hours, not understanding exactly what I'm missing.

I've installed the latest nVidia driver 470 a variety of ways, from the general Update menu for Tested and Propietary, to CLI, to the actual .run file from nVidia.

I've confirmed that the driver is installed right or at least contacting the hardware with ```
nvidia-smi
```, and it generates a usage report. I've used ```
prime-select query
``` to see which mode it's currently on, it reports back nvidia.

I think a major issue pointing in the possible solution is that my nvidia-settings and X Server has the following error:
```
[FONT=var(--ff-mono)](nvidia-settings:2458): GLib-GObject-CRITICAL **: 11:57:02.390: g_object_unref: assertion 'G_IS_OBJECT (object)' failed[/FONT]
** (nvidia-settings:2458): CRITICAL **: 11:57:02.392: ctk_powermode_new: assertion '(ctrl_target != NULL) && (ctrl_target->h != NULL)' failed

ERROR: nvidia-settings could not find the registry key file or the X server is
       not accessible. This file should have been installed along with this
       driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       prepopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.

** Message: 11:57:02.434: PRIME: No offloading required. Abort
** Message: 11:57:02.434: PRIME: is it supported? no
```
The display of nvidia-settings looks exactly like this [https://i.stack.imgur.com/PB1EG.png](https://i.stack.imgur.com/PB1EG.png)

This is a new install, so I must be missing something, and I feel like I've tinkered around so much I've ran myself in a circle.

EDIT #1: Throughout my looking around, I also see my issue pop-up with users with Secure Boot enabled, but I've double-checked in both BIOS and have seen cmd statements about Secure Boot being disabled (I can't remember what command it was that I saw that pop-up on, just that I remember seeing it...)

Any suggestions would be absolutely helpful

---

### Post by mastablasta on 2021-09-10
```
nvidia-settings could not find the registry key file [B][COLOR=#ff0000]or the X server is
       not accessible[/COLOR][/B].
```
your settings app looks wrong. make sure you are using xorg session instead of wayland for nvidia (you can change it at login i believe). hopefully that will help.


otherwise on my monitor nvidia displays to T&V first (via DVI) and then to SVGA monitor. in nvidia settings and Kubuntu settings i have set monitor as primary display and turned off the TV. now it would output to TV at boot and then at login switch to monitor and turn off TV. 

driver install method through additonal drivers application or via PPA is best for Ubuntu. method through .run file sometimes does not work.

---

### Post by zeitrif on 2021-09-10
I decided to check which one I was running on (Xorg vs Wayland)
```
echo $XDG_SESSION_TYPE
```
Returns an answer of "X11"

I've tried installing the drivers through Software & Updates, PPA, .run, none of them ever really worked for the most part. (Not worked in terms of outputting a graphics signal)
The driver sure installs, and it definitely works through ```
nvidia-smi
``` for contacting the Device, and it recognizes the specific nVidia model within Software & Updates as RTX 3080...

There was one time where I did manage it to contact the display and have it detect that it's connected in the Displays app, but no graphical output. Otherwise the display stays unrecognized unless it's at the bootloading screen for Ubuntu.

---

### Post by zeitrif on 2021-09-10
The issue was resolved-
It was a hardware issue with my BIOS, where for some reason my onboard would override my add-in RTX 3080, even if I saved the correct settings to disable onboard and enable add-in and the fix was to default the entire settings on the board and the graphics adapter immediately corrected itself.

---

