---
title: "Xubuntu 22.04 HDMI audio out stopped working"
date: 2023-08-25
forum: Desktop Environments
---

### Post by JimLS on 2023-08-25
Have been running this system for a couple months.  Connected to an HDMI TV.  HDMI audio has always worked before but today I get audio on PC internal speaker.  I opened the sound settings and don't have a selection for HDMI output.  Video output on HDMI works ok.  I tried pulseaudio -k in terminal window but still no selection for HDMI audio.  The TV isn't always on but that hasn't caused an issue with audio before.

---

### Post by #&amp;thj^% on 2023-08-25
There has been tons of sound problems as of late, can you show us this:
```
cat /sys/class/drm/card0-HDMI-A-1/status

```

---

### Post by JimLS on 2023-08-25
it shows:
connected

---

### Post by #&amp;thj^% on 2023-08-25
But sound still goes through you speakers?? and not HDMI?
Have you still been trying the 1920x1080 Res thing?

---

### Post by JimLS on 2023-08-25
I rebooted and sound through HDMI worked.  The command still gave "connected" just like when it was trying to use the in case speaker.

After I rebooted I used the sound gui.  The 'output devices' tab showed 'speakers' and didn't have a selection for HDMI.  The 'configuration' tab showed profile 'analog stereo output'.  There were other selections that included HDMI in their names but that wasn't what showed.  Seems like that would have been in case speaker but it was working through HDMI.  

I haven't solved the resolution issue.  Seems to be something wrong with my xorg file so it ignores it or perhaps something to do with wayland.  Hard to believe it isn't easier to deal with this.  Very low SAF...  :)

---

### Post by JimLS on 2023-08-29
I used a program to save the edid from the TV and added the edid.bin file to the grub line.  This solved my video and audio issues.

---

### Post by JimLS on 2023-08-29
Thought the problem was fixed but the audio shifted back to the PC internal speaker when the tv was off for an extended period.  At least the video is still working well.

---

### Post by JimLS on 2023-08-31
Adding intel_iommu=on,igfx_off to the grub line seems to fix it.  So to force output to the HDMI port even when the tv is off my complete line is:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on,igfx_off video=HDMI-A-1:e drm.edid_firmware=HDMI-A-1:edid/LG72.bin"

---

### Post by simonsaysthis on 2023-08-31
Not directly related to the problem but I had sound problems with 22.04 no end until I switched to full pipewire. The problem is that 22.04 has only partially enabled pipewire and in my case this was causing my headphone jack to not produce any sound. 

You can switch completely to WirePlumber and test the stability of sound output. If it doesn't help you can always go back to the initial state.

---

### Post by #&amp;thj^% on 2023-08-31
Well sound on Ubuntu is just a bit buggy for some hardware.
I have also used Wireplumber and continue to do so, but with all the sound problems creeping in on 22.04 I have just the stock
sound system running ATM
```
*inxi -A | grep Server-1 && inxi -A | grep Server-2
  Sound Server-1: PulseAudio v: 16.1 running: yes
  Sound Server-2: PipeWire v: 0.3.65 running: yes

```
And just can not reproduce what I'm seeing reported with sound, and some very nice members have added pipewire/wireplumber
to their systems, and by my studies around 50 to 60% of those it helped, the other's it did not help. 
So it's still a crap shoot with sound on Ubuntu...I don't see the same on Debian.

---

### Post by JimLS on 2023-08-31
Well, thought it was fixed but it's not.  AGAIN!  but when I ran speaker-test from the command line the sound went to the TV and after that the sound worked as desired (until I turn off the tv for a bit).  What to do?

---

### Post by JimLS on 2023-09-02
Set audio to hdmi rather than default in mythtv front end which is the main use and seems to work at least at the moment.  Will see how this works for a while.  I have thought it was fixed several times but then with a bit more time issues came up again.

---

