---
title: "4K screens and DPI"
date: 2020-11-05
forum: Desktop Environments
---

### Post by holysword on 2020-11-05
Plasma-desktop INSISTS in increasing the scaling of my 4K up to God knows how many DPI, instead of the standard 96 dpi. This seems to happen just in my new installation of Ubuntu 20.04, and never happened in Ubuntu 18.04. 

- "force DPI setting" in systemsettings5 is simply ignored
- the scaling setting in systemsettings5->Display is also ignored
- restarting causes unpredictable behaviour - sometimes the new session starts upscaled, sometimes it starts with 96 dpi
- xrandr works, but just until it doesn't (I guess that after the screen locks, plasma starts ignoring it again)

Is there anything akin to xorg.conf where I can force the DPI settings without having plasma try to decide for me what I want?

---

### Post by similar2 on 2020-11-21
Maybe manually creating/editing the sddm.conf file?

Hints:
[https://itectec.com/ubuntu/ubuntu-kde-5-56-sddm-login-screen-resolution-on-hidpi-fhd-screen/](https://itectec.com/ubuntu/ubuntu-kde-5-56-sddm-login-screen-resolution-on-hidpi-fhd-screen/)
[https://www.reddit.com/r/Kubuntu/comments/aff2g2/sddm_config_file_nowhere_to_be_found/](https://www.reddit.com/r/Kubuntu/comments/aff2g2/sddm_config_file_nowhere_to_be_found/)
[https://en.opensuse.org/High_DPI](https://en.opensuse.org/High_DPI)

---

