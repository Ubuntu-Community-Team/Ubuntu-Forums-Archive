---
title: "Vulkan/Mesa Questions..."
date: 2022-06-14
forum: Gaming &amp; Leisure
---

### Post by mongo42 on 2022-06-14
Hi all,

I have been pulling my hair our trying to make sense of these "Vulkan" drivers (which I understand to be an update to OpenGL...?), and what I need to do to use them.  I just found that Workstation 16.2.3 has added support for Vulkan rendering when researching how to make my games run smoother, and have been exhausting Google trying to figure out what I need to do to install these (and WHAT to install, for that matter).  All of the solutions I have found assume that I also need to grab the proprietary drivers from the Ubuntu repository in addition to the Vulkan drivers.  My video card is an NVidia GTX 1050ti, and I already have the NVidia proprietary drivers installed, so I do not need to re-install them (or do I...?).  Then there is this thing about "Mesa" drivers (do I need to install them as well, and what are they for?).  I have a bad habit of not seeing the forest through the trees, so please consider me as an Ubuntu newbe (which is not that far from the truth).  Basically, my questions are:

1) How do I install just the Vulkan stuff that I need?  Can I simply update my repository and 'sudo apt install vulkan vulkan-tools'?

2) My understanding is that Vulkan is a replacement for OpenGL.  Are there any incompatibilities, or is Vulkan completely back-ward compatible?

3) Is there a way in Ubuntu to specify what graphics renderer is used, and be able to switch between them (if there is an incompatibility where I might need to revert back to OpenGL)?

4) Am I all wet in my understanding (or lack thereof)?

Please help!

---

### Post by Perfect Storm on 2022-06-14
Simple install the latest Propriety Nvidia driver should be sufficient (v510). When a game can use Vulcan it will usually do automatically.

---

### Post by mongo42 on 2022-06-15
Thank you for your quick reply Perfect Storm!  So, am I to understand that Vulkan is included in the NVidia proprietary driver package?  When I tried to invoke the diagnostic stuff (glxinfo, glxgears) to verify that Vulkan is working, I am told that these tools are not yet installed.  Do I just need to install an add-on tool set, and that the actual Vulkan drivers were already installed alongside the NVidia (v510.73.05)?

---

### Post by Perfect Storm on 2022-06-16
I'm not sure regarding extra tool for vulcan. But when I run games that requires Vulcan I don't have to run extra step other than driver for my nvidia card.

---

### Post by mongo42 on 2022-06-22
Thanks, Perfect Storm!

That is exactly what I was hoping.  I did install both the mesa stuff (mesa-utils) and the vulkan stuff (vulkan-tools), and the verified that I do indeed have everything already on my system, and I didn't even know it...

---

### Post by Tadaen_Sylvermane on 2022-06-23
For wine stuff you will likely need DXVK in your wine directory as well. It doubles my fps in Battle.net stuff. It helps translate DirectX stuff to Vulkan.

[https://github.com/doitsujin/dxvk](https://github.com/doitsujin/dxvk)

I know you didn't mention wine but in this case it's a likely necessity to cover any bases when games are concerned. For me it's a requirement.

---

