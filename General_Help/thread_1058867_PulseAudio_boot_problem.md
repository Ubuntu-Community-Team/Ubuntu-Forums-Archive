---
title: "PulseAudio boot problem"
date: 2009-02-03
forum: General Help
---

### Post by Nisuspi on 2009-02-03
Hi all,

I've got a problem with (I think) PulseAudio slowing down the boot process by around 30 secs from the Gnome login page to a usable desktop. It seems to be fairly common, but other than uninstalling Pulse (which I don't want to do) I can't find a fix. The error messages from the logs are:

Feb  3 13:04:53 Linux pulseaudio[8798]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb  3 13:04:53 Linux pulseaudio[8798]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb  3 13:04:54 Linux kernel: [   44.004005] vmnet8: no IPv6 routers present
Feb  3 13:05:20 Linux x-session-manager[8515]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 

As I dual boot this machine a lot, speeding up getting into Gnome would be enormously helpful. If anyone has any advice I'd love to hear it...

---

### Post by SqRt7744 on 2009-02-03
> **Nisuspi said:**
> Hi all,

I've got a problem with (I think) PulseAudio slowing down the boot process by around 30 secs from the Gnome login page to a usable desktop. It seems to be fairly common, but other than uninstalling Pulse (which I don't want to do) I can't find a fix. The error messages from the logs are:

Feb  3 13:04:53 Linux pulseaudio[8798]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb  3 13:04:53 Linux pulseaudio[8798]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb  3 13:04:54 Linux kernel: [   44.004005] vmnet8: no IPv6 routers present
Feb  3 13:05:20 Linux x-session-manager[8515]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 

As I dual boot this machine a lot, speeding up getting into Gnome would be enormously helpful. If anyone has any advice I'd love to hear it...

I might be wrong, but I don't think those pulseaudio messages are errors or are slowing down the boot process. Pulse is configured to run as a daemon with user privileges and therefore can't set its priority...

I'm not convinced that pulse is the problem. Try installing a boot profiler to see what's really slowing you down.

---

### Post by Nisuspi on 2009-02-03
Can you recommend a good one?

---

### Post by Nisuspi on 2009-02-13
I've been digging around this issue a lot and one thing seems odd to me - disabling services in Preferences/Sessions does work. All the default sessions are being loaded into my ~/.config/autostart folder every time I boot, and I'm wondering if double starting Pulse (and loading unnecessary services like Bluetooth) is part of the problem.

---

