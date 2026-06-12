---
title: "How to make Plasma 5 run on Wayland with the proprietary NVIDIA Driver?"
date: 2020-02-19
forum: Desktop Environments
---

### Post by pascalcnrad on 2020-02-19
Hello dears, I have a lLnovo Thinkpad P43S with a NVIDIA Quadro P520 GPU. I've switched back to X.Org due to my GPU. But thinking about the future, I would like to adopt to Wayland again because it'll truely be "the future". These days, I use current developer edition Kubuntu 20.04 but, this does not seem to be specific for Focal Fossa because I've had the same issue when I was using 19.10 Eoan Ermine for a few weeks.
When my system is running on the NVIDIA GPU I can select »Plasma on Wayland« in SDDM — theoretically. When I did this for the first time everything seemed working fine and for this reason, I have not realised what's going on first. **[B][B]The issue is that d**espite the fact that I've chosen »nvidia« as PRIME Profile,[/B] SDDM silently switches to the iGPU as I select Wayland.
[/B] 
I can surely determine this behavior by viewing X-Plane's Log-File. Starting »nvidia-settings« returns an error message when done from the command line and »nvidia-settings« doesn't offer any specific GPU options as it does when running on X.Org although »nvidia« is displayed as the current PRIME profile.
Plasma 5.18 should actually support the NVIDIA Driver because support for EGLStreams has been merged into KWin in april last year when version 5.16 was the latest one. 
This is ten months ago now.

So, how can I force SDDM to really use the NVIDIA GPU and not to switch the GPU mode?
Are there any debug settings that I have to enable or some other special configurations?

---

### Post by mc4man on 2020-02-21
Search this out, maybe you can get something going..
KWIN_DRM_USE_EGL_STREAMS=1

---

