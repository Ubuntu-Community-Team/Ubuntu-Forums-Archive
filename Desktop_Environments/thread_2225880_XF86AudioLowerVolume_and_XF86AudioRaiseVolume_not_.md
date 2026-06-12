---
title: "XF86AudioLowerVolume and XF86AudioRaiseVolume not working"
date: 2014-05-23
forum: Desktop Environments
---

### Post by xubuntu84 on 2014-05-23
I recently installed Xubuntu 14.04 desktop environment alongside my original Ubuntu install.  In Ubuntu, the Fn keys for volume up/down/mute all work properly.  In Xubuntu, however, they do not adjust the volume properly after it has been unmuted from the keyboard.  For example, I can adjust the volume using the function keys fine, and I can mute sound using the mute function key.  However, once it has been muted, I must unmute from the sound menu on the top bar.

In Settings > Keyboard > Application Shortcuts, I have created "amixer set Master 5%+" and assigned that to XF86AudioRaiseVolume, as well as "amixer set Master 5%-" and assigned that to XF86AudioLowerVolume.  I have also set "amixer set Master toggle" to XF86AudioMute.

Running the command "amixer", I have
Simple mixer control 'Master',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 127
Mono: Playback 113 [89%] [-10.50dB] [on]

When the mute keyboard shortcut is pressed, the last [on] switches to [off], as expected, and when mute is pressed again, it goes back to [on].  However, the sound icon in the top bar displays that it is muted.

Other items listed when I run amixer are:
Headphone
Speaker
PCM
Mic
Mic Boost
IEC958
Beep
Capture
Auto-Mute Mode
Internal Mic Boost
Loopback Mixing

The Speaker mixer control says [off] for both left and right speakers until I unmute from the menu icon, in which case they both toggle to [on].  Does anyone know how to control both Master and Speaker at the same time when using the keyboard mute function key? I have tried "amixer set Master toggle | amixer set Speaker toggle" and "amixer set Master toggle && amixer set Speaker toggle" with no luck.

As extra credit, the translucent window that shows notification balloons below the clock does not show up in Xubuntu as it did in Ubuntu, while other notifications (e-mail, battery low, etc.) do show up.  Any ideas?

Thanks!
Ben

---

### Post by xubuntu84 on 2014-05-23
It appears this is a long-standing bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1026331](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1026331) and [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/878986](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/878986)

Also, I found another forum post: [http://askubuntu.com/questions/118675/mute-key-mutes-alsa-and-pulseaudio-but-unmutes-only-alsa](http://askubuntu.com/questions/118675/mute-key-mutes-alsa-and-pulseaudio-but-unmutes-only-alsa) that says to do:
```
amixer -D pulse set Master 1+ unmute
```

However, I decided to try 
```
amixer -D pulse set Master 1+ toggle
``` and it toggled nicely.

So I guess my only question now is (besides why isn't this fixed yet!), how can I make the notification balloon show the volume info?  It is not essential, just a creature comfort I was used to in Ubuntu, and that works fine on my Xubuntu desktop.

Thanks again,
Ben

---

