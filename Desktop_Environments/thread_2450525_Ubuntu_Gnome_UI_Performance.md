---
title: "Ubuntu Gnome UI Performance"
date: 2020-09-15
forum: Desktop Environments
---

### Post by ahmetulusoy on 2020-09-15
Hi;

 I have a Intel® 965GM (CL) onboard gpu , t9300 core 2 duo cpu and 4 gb ram. I installed ubuntu 20.04 on this machine. My problem was laggy ui and browsing experience. To solve this problem I added CLUTTER_DRIVER=gles2 to /etc/environment file. This made ui very smooth and snappy. I am very happy with general shell but if I enable hardware acceleration on browsers, smooth scrolling not working and makes scrolling choppy. Is there anyway to fix this problem. Because It was not even an issue with ubuntu 16.04 but all other ubuntu's with gnome have this issue. Is there any solution except disabling hardware acceleration?

---

### Post by TheFu on 2020-09-15
Gnome3 is hard on machines like yours and mine.  It wants a fast GPU.

Choose almost any other GUI for a better experience.  Mate, Cinnamon, LXQt or go crazy and don't use any DE, just use a pure WM setup.

There might be a non-bloated gnme verson, but I gave up on Gnome long ago.

---

### Post by ahmetulusoy on 2020-09-15
Actually apart from browsers gnome is working very well after changing clutter driver, only issue is browsers. Chromium is also working fine actually with hardware accelerated but couldn't figure out how to work with firefox. Enabling hardware acceleration makes it laggy.

---

### Post by Autodave on 2020-09-16
Like TheFu said, your equipment just isn't that fast: you either need to put up with lagginess or choose a lighter desktop.

---

### Post by TheFu on 2020-09-16
> **ahmetulusoy said:**
> Actually apart from browsers gnome is working very well after changing clutter driver, only issue is browsers. Chromium is also working fine actually with hardware accelerated but couldn't figure out how to work with firefox. Enabling hardware acceleration makes it laggy.

The problem is usually about overall GPU and CPU usage. Everything combined makes marginal performance just a little less. It all adds up.  Modern browsers do things that tax systems more than people realize, especially if they don't also have good ad blocking and disable most javascript on different websites. Every little bit helps.

I consider chromium to be laggy on my Ryzen 5 desktop. On older system, it is nearly unbearable due to bloat. Much of the time, I use dillo for browsing. Light and fast, but it isn't a fully, do anything, modern, browser.

---

### Post by ahmetulusoy on 2020-09-20
I tried to install unity-desktop, I can't still get performance, ubuntu 16.04 was working perfect. So I checked Xorg.0.log files of 16.04 and 20.04 and something is different. 

**Here 16.04 glamor settings:**

[    47.738] (II) glamor: OpenGL accelerated X.org driver based.
[    47.755] (II) glamor: EGL version 1.4 (DRI2):
[    47.759] (II) modeset(0): glamor initialized

**and also some extensions of AIGLX:**

[    47.930] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    47.930] (II) AIGLX: enabled GLX_ARB_create_context
[    47.930] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    47.930] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    47.930] (II) AIGLX: enabled GLX_INTEL_swap_event
[    47.930] (II) AIGLX: enabled GLX_SGI_swap_control
[    47.930] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    47.930] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    47.930] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    47.930] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    47.930] (II) AIGLX: Loaded and initialized i965

***They are diffferent in 20.04:***

glamor ;

[    32.762] (II) modeset(0): glamor X acceleration enabled on Mesa DRI Intel(R) 965GM (CL)
[    32.762] (II) modeset(0): glamor initialized

***and extensions:***

[    32.839] (II) Initializing extension Generic Event Extension
[    32.839] (II) Initializing extension SHAPE
[    32.839] (II) Initializing extension MIT-SHM
[    32.840] (II) Initializing extension XInputExtension
[    32.841] (II) Initializing extension XTEST
[    32.841] (II) Initializing extension BIG-REQUESTS
[    32.841] (II) Initializing extension SYNC
[    32.842] (II) Initializing extension XKEYBOARD
[    32.842] (II) Initializing extension XC-MISC
[    32.842] (II) Initializing extension SECURITY
[    32.842] (II) Initializing extension XFIXES
[    32.842] (II) Initializing extension RENDER
[    32.842] (II) Initializing extension RANDR
[    32.843] (II) Initializing extension COMPOSITE
[    32.843] (II) Initializing extension DAMAGE
[    32.843] (II) Initializing extension MIT-SCREEN-SAVER
[    32.843] (II) Initializing extension DOUBLE-BUFFER
[    32.844] (II) Initializing extension RECORD
[    32.844] (II) Initializing extension DPMS
[    32.844] (II) Initializing extension Present
[    32.844] (II) Initializing extension DRI3
[    32.844] (II) Initializing extension X-Resource
[    32.844] (II) Initializing extension XVideo
[    32.845] (II) Initializing extension XVideo-MotionCompensation
[    32.845] (II) Initializing extension SELinux
[    32.845] (II) SELinux: Disabled on system
[    32.845] (II) Initializing extension GLX
[    32.855] (II) AIGLX: Loaded and initialized i965
[    32.855] (II) GLX: Initialized DRI2 GL provider for screen 0
[    32.855] (II) Initializing extension XFree86-VidModeExtension
[    32.855] (II) Initializing extension XFree86-DGA
[    32.855] (II) Initializing extension XFree86-DRI
[    32.855] (II) Initializing extension DRI2

Also vpdau drivers are different, it is i965 for 16.04 and va-gl for 20.04. 

  I think my problem is I can not use opengl with glamor and those extension. They are some important extensions used by compiz.

---

### Post by ahmetulusoy on 2020-09-21
Wow, this issue seems to be solved with ubuntu 20.10. Everything is really smooth know, with hardware accelerated firefox works really good. I hope it remains like that.

---

