---
title: "[SOLVED] Gutsy +  XGL +compiz + Mplayer + Fullscreen + Intel GMA X3100"
date: 2007-11-21
forum: Desktop Effects &amp; Customization
---

### Post by realn on 2007-11-21
= High CPU usage = slow + jitter frames.
Notes:
1) This is on a Dell Latitude D630 machine.
2) The same behavior with all the other players: VLC, Kaffeine, Xine.
3) Kubuntu Gutsy

 Compiz + XGL working fine otherwise.
Anyway, if I cannot make it work I will have to uninstall compiz. Such a pity.
This should be quite a common configuration and still I couldn't find any solution. There are some other threads, all with different suggested solutions : I tried every output driver, no success.

PLEASE HELP, I am desperate.
Thank you all !!

---

### Post by realn on 2007-11-24
Upping the post. Please let me know if anyone has any suggestions.
Thank you all!

---

### Post by kshane on 2007-11-24
> **realn said:**
> Upping the post. Please let me know if anyone has any suggestions.
Thank you all!

I have an ATI Radeon X1650 and have the same troubles with video.  I just do:
```

metacity --replace

```

I restart x after watching what ever.  None of the suggestions I found helped me either.

Kevin

---

### Post by realn on 2007-11-25
Kevin, thanks for the reply. Could you please be more explicit: you do "metacity --replace" in order to do what ? I understand that this command will launch ubuntu default windows manager, but what is the effect of this command on the above mentioned problem,
As well - you say you restart the X AFTER watching the movie, I cannot watch the movie at all because of the hi CPU usage.
 Thanks for the help.
realn

---

### Post by realn on 2007-11-25
Another thing I forgot to mention - the problem seems to lie within Xgl-server. I replaced xserver-xgl + compiz with xgl+beryl : the result is that xserver-xgl and xgl respectively have a high CPU usage.
 Everybody seems to have this proble, nobody seems to have the solution.

---

### Post by realn on 2007-11-27
And yet another piece of info : fullsrceen + mplayer + beryl +xgl + ati worked OK on Kubuntu feisty.
Thank you all!

---

### Post by realn on 2007-12-13
UPed the post. No one has this issue? Then there must be a solution....

---

### Post by realn on 2008-01-29
After having found many other issues with compiz + kubuntu, I do not recommend using compiz at all.

---

### Post by timseal on 2008-02-04
go into the preferences, on the video tab change the driver to x11.  it won't be very fast, but it shouldn't look too bad.

-tim

---

### Post by realn on 2008-02-09
Thanks a lot for your answer, Tim.
Unfortunately I tried every output (x11 included) and it didn't improve at all. Please let me know if you have any other suggestions. 
Thanks a lot.

---

### Post by realn on 2008-02-27
Hello,

Please, can someone help me with this problem??
I'm still not using the beautiful 3D effects only because of this.

 Thanks a lot to anyone who might have ideas/suggestions/fixes.

---

### Post by Yellow Pasque on 2008-02-27
The recent intel graphics chips on p965 chipset or later don't work well with video playback (the earler ones are explicitly blacklisted).

The only way this is going to get fixed is if the intel driver is fixed. No one can help you until then.

---

### Post by realn on 2008-03-03
Hi, 

PROBLEM SOLVED:
1) Get rid of XGL - the X3100 card works with AIGLX
2) Run compiz with SKIP_CHECKS=yes (as per sticky post)
3) ENJOY
 I am so happy, because IT'S  REALLY NOT only eye-candy. That's why I've been trying so hard - I find it very natural and ergonomic all this stuff.

Thank you all and please let me know if someone needs more details.
PS One single glitch: as described in [http://forum.compiz-fusion.org/showthread.php?t=7045](http://forum.compiz-fusion.org/showthread.php?t=7045)

---

### Post by karush on 2008-06-10
Hi,
I'm using Debian on a Dell latitude D630, with X3100 graphic. So it should be as yours.
Could you please tell me the options you have enabled in /etc/X11/xorg.conf? (above all the "Device" section).
I managed to use Compiz Fusion, everything works quite well (obviuously not the water plugin :-) ) but when I watch fullscreen videos on totem mplayer or vlc the video is not fluent. I've also tried changing the video options on totem (xv, x11 ....) but always the same.
Please let me know.

bye

---

### Post by realn on 2008-06-10
You are lucky, it's been a while since I didn't watch my posts.

Here is the relevant part from the xorg.conf:

Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphic
s Controller"
        Driver          "intel"
        Option      "XAANoOffscreenPixmaps" "true"
        Option      "DRI"     "true"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphic
s Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        Option      "AIGLX" "true"
        InputDevice     "Generic Keyboard"
#       InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "Module"
  Load         "dri"
  Load         "glx"
  Load         "dbe"
EndSection

Section "DRI"
  Group      "video"
  Mode       0660
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

Please make sure to uninstall the XGL and run compiz like this:
SKIP_CHECKS=yes compiz --replace

Hope it helps,
Please let me know.

---

### Post by realn on 2008-06-10
I just remembered, I have a friend who just installed H.H. and the 3D thing worked out of the box, apparently. Try first my solution, if not you can upgrade to H. Heron.

---

