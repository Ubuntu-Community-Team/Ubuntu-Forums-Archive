---
title: "Where is fglrx 8.42??"
date: 2007-10-16
forum: Desktop Effects &amp; Customization
---

### Post by superyounan1 on 2007-10-16
Wasn't it supposed to be out by now? Anyone know the release date?

---

### Post by _rust on 2007-10-16
It was meant to be yesterday according to Phoronix.

---

### Post by superyounan1 on 2007-10-16
yeah, I've been waiting for it eagerly, hoping it would come out before the quake wars demo and before gutsy

---

### Post by pupdawg on 2007-10-16
Yea, I've been checking the site every 5 min... having AIGLX and faster performance is what I'm looking forward too. I also should be able to use sync to Vblank in Compiz Fusion and maybe even get some AA for the cube etc.

---

### Post by ruscoe on 2007-10-16
Is AIGLX confirmed in 8.42? I haven't heard anything for sure yet.

---

### Post by _rust on 2007-10-16
Yea, AMD confirmed AIGLX and r600 for 8.42.

I want it because I borked my compiz upgrading to Gusty and now I can't get XGL to work.

Have found out I can't work well without expose and scale :(

---

### Post by ruscoe on 2007-10-16
> **_rust said:**
> Yea, AMD confirmed AIGLX and r600 for 8.42.
Great stuff. I like AWN but XGL doesn't play nice with my laptop.

---

### Post by scottDkoDer on 2007-10-17
So who knows the actual release date, and what link to get them from?

---

### Post by blazercist on 2007-10-17
No one knows except maybe Michael from Phoronix, but he's under an NDA so he can't tell you anyway.  He says "soon" but that can mean Oct 31st for all we know.

---

### Post by superyounan1 on 2007-10-17
argh, whats with all this secrecy? its just a video driver, they really have an overstated sense of self importance. As if ati users haven't been alienated enough already.

i think even if they finally bring my (then) $400 video card up to speed with older cheaper nvidias, i'll still be sure to get nvidia for my next one

---

### Post by blazercist on 2007-10-17
agreed

---

### Post by DestroyMicroshaft on 2007-10-18
Apparently someone jumped the gun over at phoronix and posted the review article of 8.42, and someone at Digg got it and posted it, then it was quickly removed and the link to the driver taken down, and changed, so, no driver yet, but hey, heres the article your not supposed to read : )

[http://digg.com/linux_unix/AMD_8_42_4_Display_Driver_AIGLX_Is_Here]("http://digg.com/linux_unix/AMD_8_42_4_Display_Driver_AIGLX_Is_Here")

For ATI Linux customers, last month was certainly an exciting time from AMD announcing open specifications (and the subsequent delivery of the first batch and the creation of the RadeonHD driver) to the release of the fglrx 8.41 display driver. The AMD 8.41.7 driver was the first driver to be based upon AMD's new code-base and had not only delivered R600 support for the Radeon HD 2900XT, but clear performance improvements across the board from the R300 to the R500. However, this 8.41.7 driver was not well received by all. AMD had intended this driver to be targeted solely for the R600 customers, but many with older GPUs had immediately upgraded with some then having a foul experience.

Today it's now time where the fglrx driver reaches yet another milestone. Not only does today's release address many of the outstanding bugs for the earlier GPUs while also introducing a few new features, but also it delivers AIGLX support! Yes, you read that right. You can finally run your ATI graphics card with the fglrx driver and run Compiz, Beryl, or Compiz Fusion without using XGL! This is coming 13 months after NVIDIA had introduced its AIGLX support, but now in time for Ubuntu 7.10 Gutsy Gibbon it's here for ATI hardware. Granted, if you were using an older ATI GPU with the open-source Radeon driver, you could have been benefiting from AIGLX already.

In addition to the AIGLX support, the fglrx 8.42.4 driver includes X.Org server 1.4 support, video playback improvements, more performance improvements, and Rialto AGP fixes. While this driver quite promptly supports X.Org 7.3 / X server 1.4, it does not contain Linux 2.6.23 kernel support. The Linux 2.6.23 support isn't found in fglrx 8.42.4 due to issues with x86_64 support. However, we do expect that fglrx 8.43 will contain the Linux 2.6.23 kernel support.

The video playback improvements consist of a fix in TexturedVideo playback, which should result in smoother video playback. Though if you do continue running into TexturedVideo (X-Video) playback problems, be sure to report them in the Phoronix Forums. Likewise, the AGP (Rialto bridge) problem should be resolved, but report it if you're continuing to run into problems.

This release is tested for all ATI Radeon GPU products from the R300 to R600 series. This does not include support for the FireGL series, but the workstation compatibility will be introduced next month in fglrx 8.43.

While not nearly as exciting as the AIGLX support, the fglrx 8.42.4 driver also contains a few AMD Catalyst Control Center (AMDCCCLE) improvements. The 3D area of the control center (AMDCCCLE v1.5) has been reworked and now features improved anti-aliasing and anisotropic filtering controls as well as a vertical refresh control. When adjusting the AA and AF overrides, there is now a preview pane that shows a picture at that AA or AF level and a close-up view where any jaggies can be seen.

While this is a great improvement for the Catalyst Control Center, the anti-aliasing and anisotropic filtering can be improved. Presently the AA can be overridden only up to 8x while AF goes up to 16x. Now that the fglrx performance problems have been resolved, it would be really nice to see 16x AA support and ideally even their new adaptive or multi-sampling AA modes supported by their newer GPUs. This driver does introduce support for AA and AF on the R600 series.

From the "More Settings" page, the vertical refresh setting can be set to: always off, off - unless application specifies, on - unless application specifies, or always on. Now that the fglrx driver is on its new codebase and there are a few AMDCCCLE improvements already, don't be surprised if CATALYST AI makes its debut on Linux in the very near future for enhanced performance.

Now onto arguably the most sought after feature... AIGLX. It's been a long time coming, and it's here today, but there are a few words of caution. Be forewarned that there is a bug in Compiz 0.3 affecting the fglrx 8.42.4 driver and there may be a few other situations where Compiz or Compiz Fusion may not work immediately. The bug found in Compiz 0.3 and that's causing havoc with fglrx 8.42.4, has been resolved in Compiz 0.6. Next month in fglrx 8.43, AMD will be introducing a workaround for Compiz 0.3 support. If you try enabling the "desktop effects" in Fedora 7 with fglrx 8.42.4, it will fail. However, if you install Beryl or Compiz Fusion on Fedora 7 from a repository, it should work.

At Phoronix we have tested Ubuntu 7.10 "Gutsy Gibbon" quite extensively with the fglrx 8.42 series and have found it to work well with Compiz Fusion and its default effects. Whether you're using Ubuntu or another distribution, be sure to add "fglrx" to the Compiz driver white list, if needed. If you want more than pictures, in the new video area of Phoronix announced earlier today, there is a video of the fglrx 8.42 driver with Compiz Fusion Ubuntu 7.10. We also have two videos of the Radeon HD 2900XT with fglrx 8.42 running Enemy Territory: Quake Wars with all settings maxed (Video 1 and Video 2).

We'll have another article out shortly dedicated to using the fglrx driver with Compiz Fusion, but we will say that the experience has been very smooth and has been working great. Using a Radeon HD 2900XT has worked out great with Compiz Fusion as well, but we have run into a few small bugs where for example when alt-tabbing the windows during that effect have been white. Nevertheless, the bugs we have run into have not been show stopping aside from the compatibility issues with old versions of Compiz. If you are running an ATI Radeon X300 or another low-end Radeon graphics card with a slow single-core CPU, don't expect to get much out of AIGLX. Like NVIDIA, you do need a modestly powered graphics card and processor in order to be able to handle the advanced Compiz or Compiz Fusion effects.

Last month with fglrx 8.41.7 we saw some massive performance improvements on all of ATI's supported Radeon products, but that's not the end of the performance improvements. With fglrx 8.42.4 we had experienced some smaller performance boosts as well. We are continuing our testing of the fglrx 8.42.4 driver and may deliver some additional benchmarks shortly.

With Unreal Tournament 3 and Enemy Territory: Quake Wars for Linux, this timing of AMD's 8.41.7/8.42.4 driver has worked out phenomenally. With the 8.42.4 driver and a supported Radeon graphics card, you should be able to experience a great frame-rate for your hardware, stunning image quality and be easily able to manipulate the 3D settings through AMDCCCLE, AIGLX support with Compiz or Compiz Fusion should you chose to do so, smooth video playback through TexturedVideo, and all around a great experience. We have been running the ATI 8.42 driver for a couple weeks internally on different graphics cards, and aside from the problems mentioned in this article, we haven't been plagued by any other issues.

If you run into any new problems or still outstanding bugs with fglrx 8.42.4, be sure to report them in the Phoronix Forums. The fglrx 8.42 doesn't include Linux 2.6.23 kernel support by default, but if you are in a rush, check out the forums for patches. We'll be back next month telling you about the new features in fglrx 8.43.

---

### Post by superyounan1 on 2007-10-18
sweet, thanks for posting. They probably prepared this article a while back and posted on the day they were told the driver will be release, but when 8.42 was a no-show they had to pull it

---

### Post by tommy666 on 2007-10-18
So the link to the driver was there for a moment?

Did anyone download it in time?

---

### Post by BungaMan on 2007-10-19
They don't pull it back for nothing.  If it already showed to be unstable then you don't want to use it.

---

### Post by cybrid on 2007-10-19
> **BungaMan said:**
> They don't pull it back for nothing.  If it already showed to be unstable then you don't want to use it.
Ok, I agree, but in that case why don't they say a word about it ?

---

### Post by BungaMan on 2007-10-19
why should they talk about a driver that is not ready for release?  It is constantly not ready for release until they freeze code, fix bugs and aprove for release.

---

### Post by superyounan1 on 2007-10-19
> **BungaMan said:**
> why should they talk about a driver that is not ready for release?  It is constantly not ready for release until they freeze code, fix bugs and aprove for release.

why keep their customers in the dark, if its going to be delayed, it would be polite to let us know. Lots of ati users just feel like they've been short changed, so we're sensitive to little things

---

### Post by jelofson on 2007-10-23
I believe fglrx 8.42.3 is out. Here's hoping it fixes some issues. AIGLX supported.

[http://www.phoronix.com/scan.php?page=news_item&px=NjE0Ng]("http://www.phoronix.com/scan.php?page=news_item&px=NjE0Ng")

Not sure when it will be available via automatic updates. I am sure you can just dload and go for it.

---

### Post by djuniah on 2007-10-23
just installed that file on my gutsy laptop. I'm running a mobility 200m and I had full "desktop effects" enabled and configured pretty heavily and it ran at a VERY nice and high frame rate before the upgrade.  Now if i try to rotate the desktop i get 1 frame every 4-5 seconds.  Something just completely killed the performance.  I'm guessing that this has something to do with some sort of configuration but i havent been able to nail it down yet.  Any advice would be greatly appreciated. (and by advice i dont mean telling me that i should have waited for the auto-update)

edit: also, i had that VERY prominent "suspend" mode bug related to the old drivers, i'm going to give it a try now and see what happens.  I'll post my results here soon.

edit2: sadly, did not alleviate the suspend issues and now the x server seems to be restarting on its own occasinally

---

### Post by cybrid on 2007-10-24
Not on Envy yet :( . Hope to get them soon since 8.42 promised a great improvement in speed and AIGLX support.

---

