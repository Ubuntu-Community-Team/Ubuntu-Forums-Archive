---
title: "Problem AMD graphics Steam games on 16.04"
date: 2016-05-22
forum: Gaming &amp; Leisure
---

### Post by bcellin on 2016-05-22
Hello guys. My notebook has hybrid graphics Intel I7 4th gen + AMD R7 M265. I use Ubuntu 16.04 and kernel 4.6.0-040600-generic.
I'm running open source drivers. If I run a steam game without parameters, typing sudo cat /sys/kernel/debug/vgaswitcheroo/switch returns Dynamic OFF to my discrete card 
and if I add "DRI_PRIME=1 %command%" on game launch parameter, vgaswitcheroo/switch returns Dynamic PWR for discrete card, so I know my discrete card is being used when DRI_PRIME=1 is passed. 
(I did not understand what this DRI_PRIME=1 is. I think it's necessary in order to activate discrete card)

The problem is: there are some black stains on screen on some Steam games like Trine and Never Alone (images attached) using both integrated and discrete card.
And the performance is very poor on these 2 games using both graphics. Settings are on minimum but I can't play them smoothly. I did not notice any improvements using discrete card.
Is the performance really poor with open source drivers? Am I missing something?

Any help would be very appreciated.

EDIT: Setting Trine visual effects to Low instead of Very Low solves the problem of black spots on screen but game becomes unplayable due to heavy lag. I must be missing something because my graphic card is good enough to run Trine. 
Doing the same for Never Alone still does not solve the problem of black stains.

Some information:
```
$ xrandr --listproviders 
Providers: number : 3
Provider 0: id: 0x68 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 5 associated providers: 2 name:Intel
Provider  1: id: 0x3f cap: 0x6, Sink Output, Source Offload crtcs: 0 outputs: 0  associated providers: 2 name:TOPAZ @ pci:0000:03:00.0
Provider 2: id:  0x3f cap: 0x6, Sink Output, Source Offload crtcs: 0 outputs: 0  associated providers: 2 name:TOPAZ @ pci:0000:03:00.0
```

```
$ glxinfo | grep rend
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_packed_depth_stencil, 
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, 
```

```
$ DRI_PRIME=1 glxinfo | grep rend
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: Gallium 0.4 on AMD ICELAND (DRM 3.1.0, LLVM 3.8.0)
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_packed_depth_stencil, 
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, 

```

---

### Post by oldrocker99 on 2016-05-22
Are you using the open source radeon drivers? You might try the proprietary ATI drivers. Or vice versa.

---

### Post by QIII on 2016-05-22
For 16.04, the proprietary driver is AMDGPU.  fglrx is not included with 16.04 because Canonical did not want to wait to deploy the latest X Server and AMD did not want to make the fglrx driver compatible with it.

When installed, Ubuntu will determine whether the AMDGPU driver can be used.  If it cannot, the default Radeon driver is used.  

Given that AMDGPU was not used during installation, I do not believe the AMDGPU driver will work with that adapter at this point,.  However, it may be supported bythe end of Summer.

---

### Post by bcellin on 2016-05-22
> **QIII said:**
> For 16.04, the proprietary driver is AMDGPU.  fglrx is not included with 16.04 because Canonical did not want to wait to deploy the latest X Server and AMD did not want to make the fglrx driver compatible with it.
When I was using 14.04 I installed fglrx once and the performance was  catastrophic. On amdcccle I chose my discrete card to be active and  everything was so laggy. Even desktop and nautilus; I could not watch a  movie on Firefox without lag.
I turned back to radeon (open source  driver) but by that time I did not know about the command "DRI_PRIME=1"  so I was using my integrated card to render everything. That's why I  gave up on heavy games like Trine.

Now I installed 16.04  hoping to get performance with my discrete card with open source driver amdgpu and  "DRI_PRIME=1", that is, to actually use my discrete card. But I am  experiencing same results or even worse as integrated graphics on games.

> Given that AMDGPU was not used during installation, I do not believe the AMDGPU driver will work with that adapter at this point,.  However, it may be supported bythe end of Summer.
I've seen on forums that amdgpu support for my hardware has even gone out of beta on latest kernel. It is supported now. I'm not sure, but that's what I read. I don't have the source link on the top of my mind but here are some:
[http://www.osside.net/?p=16065](http://www.osside.net/?p=16065)
[http://askubuntu.com/questions/767163/ubuntu-16-kernel-bug-oops-0000-1-smp-related-to-amdgpu](http://askubuntu.com/questions/767163/ubuntu-16-kernel-bug-oops-0000-1-smp-related-to-amdgpu)


> Are you using the open source radeon drivers? You might try the proprietary ATI drivers. Or vice versa.
I'm pretty sure I'm using amdgpu because when I type 
```
lsmod | grep radeon
```
I get nothing.

And look the output with amdgpu
```
lsmod | grep amdgpu
amdgpu                987136  1
ttm                    98304  1 amdgpu
i2c_algo_bit           16384  2 i915,amdgpu
drm_kms_helper        147456  2 i915,amdgpu
drm                   364544  8 ttm,i915,drm_kms_helper,amdgpu

```

---

### Post by QIII on 2016-05-23
Ah.  Then yes, you are using the AMDGPU driver.

Here's the next question, however:  Does Steam work with the AMDGPU driver?

That I don't know, since I lost interest in Steam some time ago.  Phoronix (of course) might have some answers for that.

---

### Post by mastablasta on 2016-05-23
since it is all in AMD's hands - have you tried asking them where the issue is?

---

### Post by bcellin on 2016-05-23
Thank you for your willing to help. 

> since it is all in AMD's hands - have you tried asking them where the issue is?
I've contacted suppport on AMD's site. I don't know if it's what you meant. I pretty much copied and pasted what I've said on this thread. I'm waiting for their answer.

> That I don't know, since I lost interest in Steam some time ago.  Phoronix (of course) might have some answers for that.
I'll try to contact him on his website because last posts about R7 M265 are already old and I don't know if I'm gonna get an answer if I post there.

---

### Post by mastablasta on 2016-05-24
it is what i mean. i am not sur ehow good AMD support is. so far i only tried nvidia (user forums and official) - very helpful, but couldn't get to the bottom of it as i couldn't provide results of troubleshooting script for obvious reasons.

so fingers crossed oyu will do better with AMD. perhaps there is a setting or a swtich that was missed.

---

### Post by mörgæs on 2016-05-24
> **QIII said:**
> For 16.04, the proprietary driver is AMDGPU.
No, it's open source. 

> **mastablasta said:**
> since it is all in AMD's hands
As it's open source it's in everybody's hands.

It's a good sign that AMD is going to support the open source drivers also for new cards.

---

### Post by ZoiaGuyver on 2016-05-24
I think QIII was referring to the AMDGPU-Pro driver which is a "Hybrid" proprietary driver that uses the AMDGPU kernel module.

The M265 isn't supported in the AMDGPU-Pro yet though, it only states M395X support. The support for other cards is becoming available as the driver matures but it will be a while yet before it gets to a parity level with what fglrx used to do. It is almost there performance wise from what I've seen on the limited set of cards it does support, sometimes even faster than what fglrx could do.

I've had very little success with Steam on the open source drivers, have only tested a handful of AMD/Nvidia cards but Steam doesn't like either open source driver. It may improve soon with the opensource drivers now pushing into OpenGL 4.3+ but again it's a lot of time.

---

### Post by QIII on 2016-05-24
Yes.  To clarify, since I didn't proof my post:  AMDGPU-Pro is the proprietary.

OOTB, Ubuntu will install with AMDGPU or Radeon depending on the graphics adapter.

---

### Post by bcellin on 2016-05-24
I'm waiting for AMD support and Michael to answer me. Thank you for your time, folks.


> **ZoiaGuyver said:**
> 
The M265 isn't supported in the AMDGPU-Pro yet though, it only states M395X support. The support for other cards is becoming available as the driver matures but it will be a while yet before it gets to a parity level with what fglrx used to do. It is almost there performance wise from what I've seen on the limited set of cards it does support, sometimes even faster than what fglrx could do.


I tried fglrx when I used Ubuntu 14.04. Like I've said, my experience was even worse than with open source drivers. Much worse! I could not play or do anything because everything was so slow. 
Maybe I was missing some configuration too, who knows? But online all I've seen was people with hybrid graphics claiming to have same poor performance with fglrx. 

I hope amdgpu PRO supports my card one day and brings me at least decent performance. At least better than Integrated graphics.

---

### Post by mörgæs on 2016-05-25
> **ZoiaGuyver said:**
> I think QIII was referring to the AMDGPU-Pro driver which is a "Hybrid" proprietary driver that uses the AMDGPU kernel module.


Thanks, now I also learned something.

---

### Post by bcellin on 2016-05-25
Meanwhile I tried to install amdgpu PRO on my laptop. (I know, my card is not officially supported).
I tried installing it with kernel 4.6-generic and with a customized kernel 4.6 with CIK option enabled. Both tries resulted on "kernel not supported" error on installing and lead me to a black screen after rebooting.
Now I'm using amdgpu again.

---

### Post by Retlol on 2016-05-26
> **bcellin said:**
> When I was using 14.04 I installed fglrx once and the performance was  catastrophic. 


This depends on your card. From benchmarking the system on 15.10 with fglrx and again with the radeon driver on 16.04 I have a 20% decrease in performance. This is not a trivial difference. It's the difference of say an r7 360 vs an r9 370 in Windows. 

My card, an r7 360, even tho it's a current gen amd card, isn't supported by amdgpu as of now.

---

### Post by mörgæs on 2016-05-26
15.10 is still in the game. Supported two months more. 

You could keep using it for now, waiting for AMD to develop their other drivers a little more.

---

### Post by Retlol on 2016-05-26
> **mörgæs said:**
> 15.10 is still in the game. Supported two months more. 

You could keep using it for now, waiting for AMD to develop their other drivers a little more.

Performance aside, there's not even a gui available nor are "advanced features" like virtual super resolution (vsr) or video profiles supported. Without VSR I won't even consider playing half my steam library. 

They have a lot of stuff to implement and to be frank I don't see it happening any time soon. They can't even support their current gen cards that have been out for many months.

---

### Post by QIII on 2016-05-26
> **Retlol said:**
> They can't even support their current gen cards that have been out for many months.

They can't?  For any supported Ubuntu release prior to 16.04, the fglrx driver works perfectly well for both my R9 290X and my R9 380X.  AMDGPU actually performs better than fglrx (on 14.04) on 16.04 with my R9 380X.

fglrx is not included in 16.04 because it does not work with the latest X Server.  If you were AMD and you were doing so much work on AMDGPU and AMDGPU-Pro, as well as working on making sure AMDGPU-Pro is compatible with Khronos' Vulkan API, would you work on fglrx to keep it up with X Server or work on AMDGPU and AMDGPU-Pro and then work backwards to make it compatible with GCN 1.1 and possibly GCN 1.0?

AMDGPU-Pro will contain all the niceties and fine-grained control when it comes out at the end of summer.  They already have a beta out that works with 14.04.  Note that the beta works with Ubuntu -- which tells you who has been working with whom.

In case you don't understand what this means:  AMD is going out of its way to work with open source developers (who are primarily folks at Canonical -- so Ubuntu will be the first to reap the benefits) to give us exactly what we have been asking for for years:  a truly useful and complete open source driver (AMDGPU) which will be the basis for the hybrid driver with the closed source parts (AMDGPU-Pro).

What you are seeing here is AMD's commitment to SUPPORTING open source, not walking away from it.

NVIDIA, for their part, became a member of the Linux Foundation and is making similar moves.  So there is no reason for factional fanboyism going either direction.

---

### Post by Retlol on 2016-05-26
> **QIII said:**
> They can't?  For any supported Ubuntu release prior to 16.04, the fglrx driver works perfectly well for both my R9 290X and my R9 380X.  AMDGPU actually performs better than fglrx (on 14.04) on 16.04 with my R9 380X.

fglrx is not included in 16.04 because it does not work with the latest X Server.  If you were AMD and you were doing so much work on AMDGPU and AMDGPU-Pro, as well as working on making sure AMDGPU-Pro is compatible with Khronos' Vulkan API, would you work on fglrx to keep it up with X Server or work on AMDGPU and AMDGPU-Pro and then work backwards to make it compatible with GCN 1.1 and possibly GCN 1.0?

AMDGPU-Pro will contain all the niceties and fine-grained control when it comes out at the end of summer.  They already have a beta out that works with 14.04.  Note that the beta works with Ubuntu -- which tells you who has been working with whom.

In case you don't understand what this means:  AMD is going out of its way to work with open source developers (who are primarily folks at Canonical -- so Ubuntu will be the first to reap the benefits) to give us exactly what we have been asking for for years:  a truly useful and complete open source driver (AMDGPU) which will be the basis for the hybrid driver with the closed source parts (AMDGPU-Pro).

What you are seeing here is AMD's commitment to SUPPORTING open source, not walking away from it.

NVIDIA, for their part, became a member of the Linux Foundation and is making similar moves.  So there is no reason for factional fanboyism going either direction.

My card came out more than half a year ago and as of today it's not supported. Promises are nice, but useless to me. The only option for me at this time is the Radeon driver, which compared to Windows has at least a 30-40% decrease in performance.

For your comment on the fglrx driver, no it didn't work perfectly well. It still lagged behind performance wise by a good margin compared to Windows and lacked any and all features that were advertised on the box when I bought the product (mainly VSR).

Don't get me wrong, I'm excited about AMDGPU and the future (because I'm looking at to upgrade to the 490 when it comes out) but I'm not blind to the state of my card on Linux.

---

### Post by QIII on 2016-05-26
What card is that?  What release of Ubuntu is that?

---

