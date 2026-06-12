---
title: "Openbox Volume Control"
date: 2013-12-28
forum: Desktop Environments
---

### Post by mooreted on 2013-12-28
Running Ubuntu 13.10 with Openbox. I cannot seem to get volume control to work using the volume controls on my keyboard. I have tried several key bindings such as the following, but nothing happens when I use them.


<!-- Keybindings for Media Keys -->
    <keybind key="XF86AudioMute">
      <action name="Execute">
        <command>amixer set Master toggle</command>
      </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
        <command>amixer set Master 2dB- unmute</command>
      </action>
    </keybind>
    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
        <command>amixer set Master 2dB+ unmute</command>
      </action>
    </keybind>

and

<keybind key="XF86AudioRaiseVolume">
  <action name="Execute">
    <command>pactl -- set-sink-volume 0 +5%</command>
  </action>
</keybind>
<keybind key="XF86AudioLowerVolume">
  <action name="Execute">
    <command>pactl -- set-sink-volume 0 -5%</command>
  </action>
</keybind>

---

### Post by mooreted on 2013-12-28
Ok, I think I see the problem. Pulse Audio is using my multimedia keys for the HDMI port on my video card. I have not figured out how to change that yet.

---

### Post by mooreted on 2013-12-28
Ok, disabled HDMI through pavucontol and rebooted. Keys are working now.

It's always the simple stuff that trips me up.

---

