---
title: "MATE and selecting sound cards"
date: 2014-06-14
forum: Desktop Environments
---

### Post by Brandon_MacEachern on 2014-06-14
I'm having a problem with MATE, and selecting sound cards on my desktop.  Here's the hardware configuration.

Intel HD Audio (onboard) - Used only for headphones.
USB Sound card - Used for speakers.

When in MATE, it seems to keep defaulting to the onboard sound, and I have to go into the Pulseaudio volume control, and send the app to the USB sound, which then works fine, that app will then produce sound on the USB sound card.  But when I open another app, it's back to the Intel HD Audio again.  If I set the USB sound card as the "fallback", it STILL seems to go to the onboard sound.  I can't get a simple switch between the sound cards.

In Unity, simply going to the Sound Settings, and selecting a different output, works just fine.  It switches all apps to that output, and everything keeps working on that output.

Why can't I get this on MATE?  Even on KDE I ran into a similar problem with this.

---

### Post by tgalati4 on 2014-06-14
Open a terminal:

```
apropos pulse
```

It might look like:


tgalati4@tpad-Gloria7 ~ $ apropos pulse
default.pa (5)       - PulseAudio Sound Server Startup Script
esdcompat (1)        - PulseAudio ESD wrapper script
pabrowse (1)         - List PulseAudio sound servers on the network
pacat (1)            - Play back or record raw audio streams on a PulseAudio sound server
pacmd (1)            - Reconfigure a PulseAudio sound server during runtime
pactl (1)            - Control a running PulseAudio sound server
**padevchooser (1)     - PulseAudio Device Chooser**
padsp (1)            - PulseAudio OSS Wrapper
paman (1)            - PulseAudio Manager
paplay (1)           - Play back audio files on a PulseAudio sound server
paprefs (1)          - PulseAudio Preferences dialog
parec (1)            - Play back or record raw audio streams on a PulseAudio sound server
pasuspender (1)      - Temporarily suspend PulseAudio
**pavucontrol (1)      - A volume control for the PulseAudio sound server**
pavumeter (1)        - A volume meter for the PulseAudio sound server
pax11publish (1)     - PulseAudio X11 Credential Utility
pulse-client.conf (5) - PulseAudio client configuration file
pulse-daemon.conf (5) - PulseAudio daemon configuration file
pulseaudio (1)       - The PulseAudio Sound System

---

### Post by Brandon_MacEachern on 2014-06-14
Ok here's the result.

```
brandon@BrandonsLinuxLaptop:~$ apropos pulsedefault.pa (5)       - PulseAudio Sound Server Startup Script
pacat (1)            - Play back or record raw or encoded audio streams on a ...
pacmd (1)            - Reconfigure a PulseAudio sound server during runtime
pactl (1)            - Control a running PulseAudio sound server
padevchooser (1)     - PulseAudio Device Chooser
padsp (1)            - PulseAudio OSS Wrapper
paman (1)            - PulseAudio Manager
pamon (1)            - Play back or record raw or encoded audio streams on a ...
paplay (1)           - Play back audio files on a PulseAudio sound server
paprefs (1)          - PulseAudio Preferences dialog
parec (1)            - Play back or record raw or encoded audio streams on a ...
parecord (1)         - Play back or record raw or encoded audio streams on a ...
pasuspender (1)      - Temporarily suspend PulseAudio
pavucontrol (1)      - A volume control for the PulseAudio sound server
pavumeter (1)        - A volume meter for the PulseAudio sound server
pax11publish (1)     - PulseAudio X11 Credential Utility
pulse-cli-syntax (5) - PulseAudio Command Line Interface Syntax
pulse-client.conf (5) - PulseAudio client configuration file
pulse-daemon.conf (5) - PulseAudio daemon configuration file
pulseaudio (1)       - The PulseAudio Sound System
start-pulseaudio-kde (1) - PulseAudio Sound Server KDE Startup Script
start-pulseaudio-x11 (1) - PulseAudio Sound Server X11 Startup Script
brandon@BrandonsLinuxLaptop:~$ 

```

---

### Post by tgalati4 on 2014-06-14
If you run *padevchooser*, you should get a small, panel icon that allows you to switch audio devices.  I'm running MATE and not Unity, so you would have to search as to what Unity is setting to cause the device to be selected.  Ultimately, it is pulseaudio that is being set, so start going through the pulseaudio documentation.

[http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/PerfectSetup/](http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/PerfectSetup/)

---

### Post by Brandon_MacEachern on 2014-06-25
I gave up trying to figure this out.  As a simple user, this is way over my head.  I come from operating systems where it's a simple point and click to just select which device I want to use.

I'll stick with Unity's way of doing this, which is just that, point and click.

---

