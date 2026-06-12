---
title: "How to force custom edid?"
date: 2023-08-26
forum: Desktop Environments
---

### Post by JimLS on 2023-08-26
Xubuntu 22.04.  I have a TV for display.  If the system boots with the tv off or if I shutoff the TV the display is the wrong resolution when turned back on.  I am looking at using a edid file rather than reading from the TV so it remains constant.  I don't have any other displays so locking it to this resolution is fine.  I found a few posts about the format of the edid file and calculated the numbers from cvt output but it also seems there may be a default 1920 x 1080 file that would work.  It looks like I need some of the kernel tools so I loaded this:
sudo apt install linux-tools-generic

But I am completely lost on where to put the lines mentioned to add to files and how to compile the edid file.  I have messed with grub files and the like a little but very limited experience with this sort of thing.

BTW, when I put in a link it seems to not end correctly and I had trouble putting in other links.  I added a code tag to complete my links and then deleted the code tags.  Must be doing something wrong...

Here's a couple sites I used for reference:
[https://billauer.co.il/blog/2020/08/linux-override-fake-edid/](https://billauer.co.il/blog/2020/08/linux-override-fake-edid/)

[URL="https://docs.kernel.org/admin-guide/edid.html"]https://docs.kernel.org/admin-guide/edid.html

[/URL][URL="https://www.osadl.org/Single-View.111+M5315d29dd12.0.html"]https://www.osadl.org/Single-View.111+M5315d29dd12.0.html



[/URL]

---

### Post by TheFu on 2023-08-26
The GPU driver settings for your specific GPU control it.  I've posted in these forums how to do it for an nVidia 1030GT.  Look for those posts.  

The overview is to connect the GPU to the TV and use the edid tools to get the data directly from the monitor. Save that as binary by redirecting the output to a file.  Then, depending on your GPU X11 settings, there is a xorg.conf file setting to load a specific EDID and ignore what the monitor says or doesn't say.  Sadly, I've removed all nvidia from my systems to avoid driver hassles unrelated to the EDID, and the exact file settings that I used are long gone, except what I posted in these forums.

---

### Post by JimLS on 2023-08-26
I searched for keywords nVidia 1030GT in posts by you and read every post - there was nothing there like you describe.  Must have been using the wrong keywords.  

I appreciate the post but it's things like:

> use the edid tools to get the data directly from the monitor. Save that  as binary by redirecting the output to a file.  Then, depending on your  GPU X11 settings, there is a xorg.conf file setting to load a specific  EDID

that I am having trouble with.  Which edid tools?  I need an example of the command line used or similar because I have NO EXPERIENCE with this level of detail.  I would think there would be a page somewhere on the net that would show how to do this in detail.  Found lots of pages that hit the high points.

Found this page that looks to have enough detail 
[https://kodi.wiki/view/Archive:Creating_and_using_edid.bin_via_xorg.conf](https://kodi.wiki/view/Archive:Creating_and_using_edid.bin_via_xorg.conf)
and the edid-generator package has a 1920x1080.bin file that is likely usable without changes (or it has tools to build a modified one) but I don't have an xorg.conf file that they say to add the line to.  I only have these so where to put the reference to the edid file?
```
jim@jim-myth:/usr/share/X11/xorg.conf.d$ ls -al
total 36
drwxr-xr-x 2 root root 4096 Aug 26 13:43 .
drwxr-xr-x 5 root root 4096 Jul 10 06:56 ..
-rw-r--r-- 1 root root   92 Aug 21  2022 10-amdgpu.conf
-rw-r--r-- 1 root root 1350 Apr  4 01:20 10-quirks.conf
-rw-r--r-- 1 root root   92 Jul 11  2022 10-radeon.conf
-rw-r--r-- 1 root root 1429 Feb 11  2022 40-libinput.conf
-rw-r--r-- 1 root root  590 Apr  6  2020 51-synaptics-quirks.conf
-rw-r--r-- 1 root root 1751 Apr  6  2020 70-synaptics.conf
-rw-r--r-- 1 root root 3458 Apr  6  2022 70-wacom.conf
jim@jim-myth:/usr/share/X11/xorg.conf.d$

```
I think there are other ways to use the edid file but that's another place I am lost.

---

### Post by TheFu on 2023-08-26
a) if instructions say to use a file and you don't have that file, MAKE IT!

b) that link to the Kodi wiki seems complete to me.  The steps are labeled, commands are provided, examples of what to run are there.  I don't see the issue.

The edid file goes into a stanza section inside the xorg.conf file.  They show this.  

Do you have an nvidia GPU?  If not, then this won't help, though AMD GPUs might have a similar method, I don't know and haven't needed to use it with my AMD GPUs.  To be fair, since I stopped using nvidia, I did completely change how my computers connect to monitors - swapped out a VGA KVM-switch for an 4K HDMI KVM-switch, so the connections are all a bit cleaner.

Also, there can be multiple xorg.conf files. As long as you follow the naming convention, it doesn't matter. Config files don't go under /usr/ BTW.  They go under /etc/  ... somewhere.  Have a look. The X11 directories should exist.  Again, the instructions on the Kodi page are pretty clear about that as well.

---

### Post by Holger_Gehrke on 2023-08-27
The tool to read the edid information from a connected display is named 'get-edid' and is in the package 'read-edid'. It reads the information and sends it out to standard output, so to save it into a file you have to redirect it. Since it directly accesses the i2c bus that's part of all modern display connections you need to have elevated permissions to use get-edid.

Holger

---

### Post by JimLS on 2023-08-27
GPU is Intel:```
jim@jim-myth:~$ inxi -G
Graphics:
  Device-1: Intel HD Graphics 530 driver: i915 v: kernel
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1080
  OpenGL: renderer: Mesa Intel HD Graphics 530 (SKL GT2)
    v: 4.6 Mesa 22.2.5-0ubuntu0.1~22.04.3
jim@jim-myth:~$
```
Tried adding a video setting to grub line with name as HDMI-1 and as HDMI-A-1 (both appear in different places) but it made no effect.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=HDMI-A-1:1920x1080@60"

Main issue with the kodi page is I don't have a x conf file with a device section in it and the details of how to generate a file to add the lines to uses nvidia tools I don't have.  So I grabbed a very sparce intel .conf file from here
[https://wiki.archlinux.org/title/intel_graphics](https://wiki.archlinux.org/title/intel_graphics)
and added the lines from the kodi page here
[https://kodi.wiki/view/Archive:Creating_and_using_edid.bin_via_xorg.conf](https://kodi.wiki/view/Archive:Creating_and_using_edid.bin_via_xorg.conf)
 along with the .bin for the desired resolution from the edid-decode package mentioned on the kodi page
to get this
```
jim@jim-myth:/usr/share/X11/xorg.conf.d$ cat 20-intel.conf
Section "Device"
  Identifier "Intel Graphics"
  Driver "intel"
 Option         "ConnectedMonitor" "HDMI-1"
 Option         "CustomEDID" "HDMI-1:/lib/firmware/edid/1920x1080.bin"
 Option         "IgnoreEDID" "false"
 Option         "UseEDID" "true"
EndSection
jim@jim-myth:/usr/share/X11/xorg.conf.d$


```
and it works!  Praise be and thanks for sticking with me on this!

---

### Post by TheFu on 2023-08-27
I'm a little surprised that Intel supports the CustomEDID option.  That's great!

If this is solved, please use the "thread tools" button at the top of the page to mark it.  Help the community out!

---

### Post by #&amp;thj^% on 2023-08-27
> **TheFu said:**
> I'm a little surprised that Intel supports the CustomEDID option.  That's great!
That makes a few of us :)
> **TheFu said:**
> 
If this is solved, please use the "thread tools" button at the top of the page to mark it.  Help the community out!

Always a Good practice, nice work TheFu

---

### Post by JimLS on 2023-08-27
I spoke a bit too soon.  I have MythTV front end (playback screen for DVR) automatically starting at boot and it starts now full screen as desired but when I exit to the normal desktop the resolution is set to much higher and the desktop icons are tiny.  Not sure why my setting the resolution only fixes the MythTV display.  Perhaps I should start a new topic since I marked this as solved?  I could disable mythtv front end starting and see if the system shows 1920x1080 desktop - I suppose that would be useful information when looking into this.

---

### Post by TheFu on 2023-08-28
If you use X11, then the xrandr program can be used in your ~/.xinitrc file to for a resolution.  99% of the time, you want the native resolution for the monitor to be your default.  There are GUI tools to manage the resolution - lxrandr and arandr are examples.  When I'm doing presentations, I show up to the room, connect my laptop to the projector, ask the IT nerd what resolution the projector likes then choose that for my 2nd screen in lxrandr.  Almost always, it is 1920x1080 @ 60hz.

The new-fangled GUIs each have their own resolution management tool.  If you look up the "desktop guide" for the specific Ubuntu flavor and release, it shouldn't be hard to find it.   [https://help.ubuntu.com/stable/ubuntu-help/prefs-display.html.en](https://help.ubuntu.com/stable/ubuntu-help/prefs-display.html.en)  <---- google found that for 22.04 Gnome.

Running xrandr on my workstation:
```
$ xrandr 
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 16384 x 16384
DisplayPort-0 disconnected primary (normal left inverted right x axis y axis)
**HDMI-A-0** connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   **1920x1200     59.95*+**
   1920x1080     60.00  
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     60.02  
   1440x900      59.95  
   1280x960      60.00  
   1280x800      59.95  
   1280x720      59.95  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
   720x400       70.08  
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
DisplayPort-2 disconnected (normal left inverted right x axis y axis)
```
So, if I wanted to force a different resolution, I can pick from one of those. The GPU port being used will need to be addressed and the specific resolution.  For my setup, the specific command is:
```
xrandr  --output HDMI-A-0   --mode  1920x1080
```
if I wanted a 1080p setup for some reason.  I'd feel like I was lacking 200px.  Drop that line into the .xinitrc (create it if you don't have one) and make it have read and execute permissions.  [https://wiki.debian.org/Xinitrc](https://wiki.debian.org/Xinitrc) has more details and caveats.

I do need to be clear.  **xrandr** only works with X11, not Wayland.

---

### Post by JimLS on 2023-08-28
I have Wayland.  xrandr seems to work ok at getting the possible resolutions but maybe some functions don't work.  Not opposed to changing that though if it isn't too difficult.  Starting to think maybe I should have chosen an older version of Ubuntu that didn't try to be so smart at choosing what it thought would be best for me.  

I deleted the xorg conf file I added.  If I boot with the TV on it starts at 1920 x 1080 and everything works fine.  Until I turn off the TV and something changes the resolution.  

Maybe an edid emulator?  Seems crazy that I need to add something like that but it may be the simplest way to fix this.

---

### Post by TheFu on 2023-08-28
I don't see how the EDID stuff added to an X11 config file would be used with wayland in any way.  Are you really using Wayland? I have doubts.  It is either Wayland or X11 for the display server. Not both.  I can't use Wayland because it breaks my workflows - to do lots of remote windows and screen scrapping/capturing.  The Wayland tools are all inferior from a capability standpoint, even if they are more secure.  

For example, on my workstation right now, I have .... 14 windows open and about 10 more iconified. Of all those, 5 are local windows. All the others are running on other systems.  For me, "the network is the computer."   [https://en.wikipedia.org/wiki/The_Network_is_the_Computer](https://en.wikipedia.org/wiki/The_Network_is_the_Computer)  My systems are highly interdependent.  I run email and browsers on a different system than the one I'm actually sitting behind.  This is how I work, constantly.

---

### Post by jawilljr2 on 2023-08-28
[Try using drm.edid_firmware in grub.](https://wiki.archlinux.org/title/Kernel_mode_setting#Forcing_modes_and_EDID)

Below is my "GRUB_CMDLINE_LINUX_DEFAULT"

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=DP-2:e drm.edid_firmware=DP-2:edid/edid.bin"
```

Yes it works with Intel GPU's.

---

### Post by JimLS on 2023-08-28
Thanks jawilljr2!  Some of the solutions I found weren't clear on exact syntax and what file to put the edits into so the example is very helpful.  Such as drm_kms_helper.edid_firmware related stuff.   I will give your suggestion a try.... 

What's the 'e' right after 'video=DP-2: for?  I have seen some examples that have a resolution there such as:

GRUB_CMDLINE_LINUX_DEFAULT="video=HDMI-A-2:640x480D drm.edid_firmware=HDMI-A-2:edid/640x480p60.bin"

My real question is where can I find the options and syntax for variations on what you posted?  Would like to understand what I am doing...

---

### Post by #&amp;thj^% on 2023-08-28
> **JimLS said:**
> 

What's the 'e' right after 'video=DP-2: for?  
```
-e             : Set environment variable
```
I just like TheFu I have hard believing this will work on wayland, and I wouldn't mind being proved wrong. ;)

---

### Post by JimLS on 2023-08-28
I will double check if I am using wayland tonight when I get back to the machine.  It's whatever is the default in xubuntu 22.04.

---

### Post by jawilljr2 on 2023-08-28
The "video=DP-2:e" part forces the output to on.

The option are in the link I posted under "Forcing Modes"

---

### Post by JimLS on 2023-08-28
Excellent!  I missed that...

---

### Post by JimLS on 2023-08-28
Hmmm...

I have X11 not wayland.

updated the grub line and it seems to work!  I am going to give it a couple days to really tell though because I have thought I had it before.

---

### Post by JimLS on 2023-08-28
But for some reason now I don't have audio selection for the HDMI output so no sound on the TV....

---

### Post by JimLS on 2023-08-29
used read-edid to save edid from the tv which included the audio in that the generic resolution edid file did not.  Then put the link to that in the grub line.  Now I have video and sound.  Had to reset the audio setting in myth front end to system default and all seems to work.  I will report back in a few days after I have had some more time to see...

---

