---
title: "Lost compiz/gl desktop"
date: 2007-12-23
forum: Desktop Effects &amp; Customization
---

### Post by mathenge on 2007-12-23
I had compiz with amazing desktop effects working but kept loosing the titlebar. Under advise from the IRC support forum I tried upgrading to the latest nvidia driver. Now the gl desktop will not load. Compiz won't work. I've tried removing the installed driver by typing:

sudo apt-get remove nvidia*

and then installing the nvidia driver that was there from the repositories using synaptic, but still I can't get the gl desktop to start, so compiz isn't working.

This would be a sore point for Ubuntu if this causes a re-install. I'm hoping the fix is simple.

---

### Post by sigmarhophi on 2007-12-23
first off, bummer for the loss of 3-d effects.  I recently did the latest updates and the settings I had went for a walk.

ok, are you getting any particular errors? navigate: System -> Preferences -> Appearances then try activating the effects there.

---

### Post by mathenge on 2007-12-23
Thank you for posting a reply. I've tried going to SYSTEM > PREFERENCES > APPEARANCE. When I try to enable desktop effects, I get the error message "Desktop Effects could not be enabled."

Here's some additional information from /var/log/Xorg.0.log

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU Quadro NVS 110M (G72) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.21.fc
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro NVS 110M at PCI:1:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (121, 120); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
.
.
.
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "UseFBDev" is not used

From this there seems to be a problem with the GLX module in NVIDIA. I don't know how to resolve this.

Andrew.

---

### Post by joshuachad on 2007-12-23
check and see if you xorg.conf has an entry for glx.
$more /etc/X11/xorg.conf


Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"  <---------------------should be in the section modules

Also what card do you have?

If you xorg.conf doesnt have that entry then insert it in the file and save it. Restart X.

---

### Post by mathenge on 2007-12-23
Thanks for posting your reply. My xorg.conf file has the entry

Load "glx"

in the Modules section.

I was searching and saw another post. It mentioned something to do with the difference between the kernel glx module and the nvidia one. The nvidia module is:

libGL.so.169.07

I don't know what the kernel module is. What I'm going to try is to downgrade the nvidia module since I suspect that this is the problem - kernel vs nvidia module mismatch.

That module (169.07) is the latest one. It was installed from Nvidia's site. For some reason, even when I remove the module and try to install from Ubuntu sources (synaptic) This module is not removed.

Let me know if you have any other thoughts on this.

---

### Post by joshuachad on 2007-12-23
lately when i install nvidia drivers i have been using envy. Have you tried that?

---

### Post by mathenge on 2007-12-23
I haven't tried envy. I don't know what it is. How do I install/use it?

---

### Post by mathenge on 2007-12-23
I've downloaded and installed envy. Went through the install. The latest nvidia driver was installed and the system rebooted OK. However,  the same problem still exists. When I go to SYSTEM > PREFERENCES > GL DESKTOP the entire system hangs. I have to restart X with CTRL+ALT+BACKSPACE. This get's me back to the login prompt.

I suspect that the only way to get compiz working again is a clean install. I'll attempt that over the holidays if I cannot find a solution. This is very, very frustrating.

---

### Post by mathenge on 2007-12-23
I'm happy to report that I'm almost there. This is what I did.

I reinstalled the nvidia drivers (a second time) using envy. When envy started, there were additional missing packages and it asked for my Gutsy CD which I provided. Additional packages from the CD were installed. Envy then asked for a reboot and I complied.

After reboot, I tried to go to SYSTEM > PREFERENCES > GL DESKTOP.

Once again, the system hung.

I hit CTRL+ALT+BACKSPACE and then logged in again.

This time I went to SYSTEM > PREFERENCES > APPEARANCE.

From there I selected the "Visual Effects" tab.

I changed the setting from "None" to "Normal."

A second dialog box came up informing me that "Restricted Drivers" were not enabled and asked if I would like to enable them. I agreed. Once the dialog disappeared I was asked to reboot. I complied.

When I returned to my desktop after this reboot, I selected SYSTEM > PREFERENCES > APPEARANCE again and changed the settings from "None" to "Normal."

VOILA.... COMPIZ IS WORKING!

I have a cube that's spinning happily and the mouse and key combinations that I had set for compiz actions are still working.

Only one thing left to solve now. The title bar on all windows is transparent. I can't see any window titles unless there's a white background behind them. My desktop is black and so, because the title bar is black it seems like there's no title bar. You can faintly see the window title in a very light grey font. You can clearly see the three close/minimise/maximise buttons though.

I suspect that this is an easy setting to change. If anyone has any information on how to change this, let me know.

Thanks Joshuachad on the suggestion to use Envy. I suspect that there were more packages to install than just enabling the nvidia-glx-new in Synaptic which was breaking too many things.

Thanks again, but if you have a suggestion on how to fix the titlebar issue please let me know.

Andrew.

---

### Post by Forlong on 2007-12-26
What window decorator are you using (emerald || gtk-window-decorator || kde-window-decorator)?

---

### Post by mathenge on 2007-12-26
Hi Forlong, 

I'm using emerald. I had also installed mac4lin ([http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)) after following the long installation document to make my desktop look like a mac.

I've now removed the mac4lin theme but from time to time the title bar still disappears. It's not consistent behaviour. Sometimes it won't go away for a long time but other times it will keep disappearing. If I run "compiz --replace" I get my title bar back.

I think that it may be theme related so I'm going to try out different themes and see which one works. Compiz and emerald are supposed to be very compatible so I might have to reinstall compiz and/or emerald.

Thanks for replying.

Andrew.

---

### Post by Forlong on 2007-12-27
Emerald is not really stable at the time, so it crashes sometimes (although I have to say it does this pretty seldom on my machine).
You don't have to re-run Compiz then, though. Just open [Alt]+[F2] and run **emerald** (you don't need the --replace option, since there's nothing to replace then ;)).

---

