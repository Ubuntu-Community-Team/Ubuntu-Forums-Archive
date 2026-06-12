---
title: "X crashing on resume from suspend, restarts itself without hardware acceleration"
date: 2020-10-07
forum: Desktop Environments
---

### Post by m2001 on 2020-10-07
Hi! I'm running Xubuntu 18.04.5 LTS, kernel 4.15.0-118-generic x86_64
Sometime in the past month or so, almost every time I resume from suspend, the screen looks scrambled, the mouse pointer moves but everything else is frozen, and usually X gets killed and then restarts itself. The most infuriating part about this is that X restarts without hardware acceleration, and I can't seem to re-enable it except by rebooting.

Basic details:
VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250]

vainfo before crash:
```

vainfo: VA-API version: 1.1 (libva 2.1.0)
vainfo: Driver version: Mesa Gallium driver 20.0.8 for AMD RS880 (DRM 2.50.0 / 4.15.0-118-generic, LLVM 10.0.0)
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc
libva info: VA-API version 1.1.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/r600_drv_video.so
libva info: Found init function __vaDriverInit_1_1
libva info: va_openDriver() returns 0

```

vainfo after X restarts:
```

libva info: VA-API version 1.1.0
libva info: va_getDriverName() returns -1
libva error: va_getDriverName() failed with unknown libva error,driver_name=(null)
vaInitialize failed with error code -1 (unknown libva error),exit

```

As well, if DISPLAY isn't set, I get the message "error: can't connect to X server!" BUT the rest of the output is similar to the "before crash" output.


part of dmesg output related to resume problems:
```

[63999.130770] [drm] ring test on 5 succeeded in 1 usecs
[63999.130774] [drm] UVD initialized successfully.
[63999.130855] [drm:r600_ib_test [radeon]] *ERROR* radeon: fence wait failed (-35).
[63999.130879] [drm:radeon_ib_ring_tests [radeon]] *ERROR* radeon: failed testing IB on GFX ring (-35).
[63999.130894] [drm:radeon_resume_kms [radeon]] *ERROR* ib ring test failed (-35).

```

Thanks for any help.

---

### Post by m2001 on 2021-02-12
In case anyone reads this looking for a solution to a similar problem...

I have not solved it but am having some success with a work-around. I've found that simply attempting to suspend and wake again, randomly wakes with X in a working state. I've had the best success by suspend/wake while the computer is in the following state:

- Disable all CPUs except CPU0
- throttle cpu to lowest speed
- sending SIGSTOP to browsers and other processes with typically higher cpu usage
- suspend from tty1 instead of in X

I'm not sure all those steps are necessary. I do all this, suspend, and restore it on wake, all in a bash script, so it's painless.


This makes me think there must be a race condition with the cpu/gpu or in the radeon drivers.

---

