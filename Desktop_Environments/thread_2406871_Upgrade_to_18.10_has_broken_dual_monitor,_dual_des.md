---
title: "Upgrade to 18.10 has broken dual monitor, dual desktop operation"
date: 2018-11-27
forum: Desktop Environments
---

### Post by cjsmall on 2018-11-27
**System:**[INDENT]Machine:   Intel Dual Xeon E5-2630
    OS:          Xubuntu 18.10
    GPU:        Nvidia K4000 GPU
    Monitors:  Dual Planar PX212M 1600x1200 Monitors[/INDENT]

**Problem:**[INDENT]System has been running fine for years under all past versions of Xubuntu.  The dual monitors are configures without Xinerama so that separate desktop sessions with separate panels launch on each screen.

    However, after the recent upgrade to Xubuntu 18.10, I cannot get the second monitor to be recognized.   When the machine boots the second monitor receives signal and goes active with the screen turning a uniform grey.   An xfce4 desktop session starts on monitor #1 (display :0.0) but not on the second monitor (:0.1) located to the left.  Nevertheless, the mouse navigates to the second monitor and appears as a pointer on the screen.  Also, the screen saver (Xscreensaver) starts up on the second monitor at the same time as on the first.

    From the Settings menu:[/INDENT]
[INDENT=2]* Nvidia  shows a single display  ([image]("http://smallthoughts.com/files/181125_xfce_nvidia_1.jpg"))
        * ARrandR shows a single display  ([image]("http://smallthoughts.com/files/181125_xfce_arandr.jpg"))
        * Display shows a single display  ([image]("http://smallthoughts.com/files/181125_xfce_display.jpg"))
[/INDENT]
[INDENT] 
    However, the system is properly configured for two monitors as can be seen by the Nvidia X Server Configuration  ([image]("http://smallthoughts.com/files/181125_xfce_nvidia_2.jpg")) and by inspecting [/etc/X11/xorg.conf]("http://smallthoughts.com/files/181125_xfce_xorg.conf").[URL="http://smallthoughts.com/files/181125_xfce_xorg.conf"]
[/URL]
[/INDENT]
[B]
Attempted fixes:[/B][INDENT]Xubuntu 18.04 was using the proprietary v390 driver package and this was retained after the upgrade to 18.10.  A change was made to use the open source v415 drivers, but this had no effect.  ([image]("http://smallthoughts.com/files/181125_drivers.jpg"))

    The second monitor was initially attached to the GPU DP-2 port.  To rule out any possible hardware problem, the monitor was moved to DP-3 with no change.
[/INDENT]
  
**Questions:**[INDENT]Why is the second monitor active but not being detected by the OS?  What needs to be addressed to rectify this?
[/INDENT]
[INDENT] 
    Why didn't the dual-desktop configuration get preserved between 18.04 and 18.10?  What needs to be done to reactivate a desktop on the second monitor?

Thanks for any insights you can offer. [/INDENT]
 

**More info follows:**[INDENT]-------------------------------------------------------------------------------
# xrandr
Screen 0: minimum 8 x 8, current 1600 x 1200, maximum 16384 x 16384
DVI-I-0 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 432mm x 324mm
   1600x1200     60.00*+
   1280x1024     85.02    75.02    60.02
   1024x768      85.00    75.03    70.07    60.00
   800x600       85.06    75.00    72.19    60.32    56.25
   640x480       85.01    75.00    72.81    59.94
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
# lshw -c video
  *-display
       description: VGA compatible controller
       product: GK106GL [Quadro K4000]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
resources: irq:84 memory:b2000000-b2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:a000(size=128) memory:c0000-dffff
-------------------------------------------------------------------------------
[/INDENT]

---

### Post by T.J. on 2018-11-28
It is important to say that 18.10 is intended for developers and enthusiasts who can handle a few bugs. If you upgraded in place from 18.04 to 18.10, you should expect bugs, especially in your settings files.  In place upgrades from an LTS to a non-LTS version are not recommended.

  That said, it sounds like the monitor is active but the session is not configured properly.  Have you tried creating a new user account and logging in to see if it is a bad account setting from old user files?  Nvidia cards retain settings in the users' files.

---

### Post by cjsmall on 2018-11-30
I did try creating a new account as well as removing my .cache directory and this had no effect.  I've been offsite for a couple of days and will tackle this problem again tomorrow.  Thanks for the suggestions.  I'll happily take others if anyone has any ideas.  I'm just finding it hard to understand how the monitor can be there, but none of the config tools, including NVIDIA's can see it.  This seems to suggest that there is something elsewhere in the OS initialization that is the problem.

---

### Post by Autodave on 2018-11-30
Upgrading from one release to the next rarely works for me. So rarely that I no longer try it at all.  I stay with the LTS releases and only do clean installs.

---

