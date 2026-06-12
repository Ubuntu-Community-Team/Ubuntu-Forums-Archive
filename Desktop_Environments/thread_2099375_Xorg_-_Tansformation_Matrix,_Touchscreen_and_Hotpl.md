---
title: "Xorg - Tansformation Matrix, Touchscreen and Hotplug Hell"
date: 2012-12-29
forum: Desktop Environments
---

### Post by Krobaruk on 2012-12-29
Hi Everyone,
 
First time poster here and I'm actually using XBMCBuntu (Based on 12.10). 
 
I spent quite a while getting my acient touchscreen to work with Ubuntu including the somewhat confusing Transformation Matrix setting. Hopefully I'm posting this question in the right place as it is a probably a bit specialist.
 
Configuration is Primary display on DVI (1024x768) and secondary display on HDMI (1920x1080) using Geforce 620 on Nvidia closed driver. The problem is the HDMI display comes and goes depending on when the amp is on or off, this is no problem for XBMC but a big problem for Xorg as every time the HDMI display disappears the Transformation Matrix setting becomes wrong and the touchscreen calibration goes very wrong.
 
Is there some sort of way to change the Transformation Matrix setting depending on if Display1/Monitor1 is present?  Or get rid of the need for this setting when using multiple screens when only one screen is a touchscreen?
 
Below is an extract from my Xorg conf.d file:
 
Section "InputClass"
  Identifier "elographics config"
  MatchProduct "Elo Serial TouchScreen"
  Option "Calibration" "30 4081 43 4126"
  Option "Transformation Matrix" "0.347826 0 0 0 0.711111 0 0 0 1"
  Option "InvertX" "on"
  Option "InvertY" "on"
EndSection

---

