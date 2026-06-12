---
title: "Problems with HDMI....Help!!"
date: 2023-03-13
forum: Desktop Environments
---

### Post by Justin534 on 2023-03-13
Plugging in my computer via HDMI to my TV was just working fine yesterday. I'm stumped with what's going on. Im running xubuntu (ubuntu 22.10). When I plug my computer into tv via HDMI the TV is displaying there's no input signal. But it does seem to register something because it shows me the HDMI port that the computer is plugged into from the input menu. When I plug in the cable I get a Display window that pops up but it only shows my laptop as a display and not the TV. As far as I can tell it doesn't seem to be an issue with the TV because it can get the HDMI signal just fine from my chromecast.

---

### Post by ActionParsnip on 2023-03-14
Does the system have a make and model?

---

### Post by Justin534 on 2023-03-16
My computer? Its an Acer Nitro AN515-53

Also I just noticed this when I run apt upgrade:

The following packages have been kept back:
  grub-efi-amd64-bin grub-efi-amd64-signed libnvidia-cfg1-525 libnvidia-compute-525 libnvidia-compute-525:i386 libnvidia-decode-525 libnvidia-decode-525:i386
  libnvidia-encode-525 libnvidia-encode-525:i386 libnvidia-extra-525 libnvidia-fbc1-525 libnvidia-fbc1-525:i386 libnvidia-gl-525 libnvidia-gl-525:i386
  linux-modules-nvidia-525-generic nvidia-compute-utils-525 nvidia-driver-525 nvidia-kernel-common-525 nvidia-kernel-source-525 nvidia-utils-525 shim-signed
  xserver-xorg-video-nvidia-525

Most of these are video related packages. I don't get why they would be kept back and not be upgraded.

---

### Post by DuckHook on 2023-03-16
> **Justin534 said:**
> The following packages have been kept back:
  grub-efi-amd64-bin grub-efi-amd64-signed libnvidia-cfg1-525 libnvidia-compute-525 libnvidia-compute-525:i386 libnvidia-decode-525 libnvidia-decode-525:i386
  libnvidia-encode-525 libnvidia-encode-525:i386 libnvidia-extra-525 libnvidia-fbc1-525 libnvidia-fbc1-525:i386 libnvidia-gl-525 libnvidia-gl-525:i386
  linux-modules-nvidia-525-generic nvidia-compute-utils-525 nvidia-driver-525 nvidia-kernel-common-525 nvidia-kernel-source-525 nvidia-utils-525 shim-signed
  xserver-xorg-video-nvidia-525
This is not a problem. The newer apt messages give almost too much information and the "kept back" message is misleading. All it is telling you is that these packages are slated for future implementation, but not yet ready.

It's a courtesy heads&#8209;up.

It could be worded better.

---

### Post by Justin534 on 2023-03-18
Oh...well, good! You know what happened if I ran apt dist-upgrade and it got rid of the message that they were held back? I feel like I've only used that command to upgrade from lets say 22.04 to 22.10. Even though there isn't a new version of ubuntu it still ran, installed a few things, and got rid of the held back message. I'm a little confused on what actually happened.

---

