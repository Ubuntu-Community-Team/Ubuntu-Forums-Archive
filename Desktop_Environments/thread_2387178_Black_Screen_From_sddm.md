---
title: "Black Screen From sddm"
date: 2018-03-15
forum: Desktop Environments
---

### Post by springshades on 2018-03-15
Hi everyone,

After a recent "apt-get dist-upgrade", I started to get a black screen from sddm. The system boots successfully otherwise, so Ctl + Alt + 1 gives me a command line, but I can't get to a graphical environment.

Per /var/log/apt/term.log, the main things that seem like they may have caused the issue are updates to:

nvidia-settings
pulseaudio (Seems unlikely to cause this, but I know many people have had issues in the past?)
Many packages with "mesa" in the name.
Several "libgl" packages.
A single package that starts with "libwayland".


Things that I have done to try to fix this myself:

1. Booted in "nomodeset". No effect.

2. I installed nvidia-390 which replaced my previously installed nvidia-384 just in case there was an issue with that specific driver. No effect.

3. Ran "systemctl isolate multi-user" followed by "systemctl isolate graphical" as a turn it off turn it on again type of thing. No effect.

4. Ran "systemctl --failed" to look for boot failures. Found one unrelated thing that wasn't causing the issue (vmware). Just in case, I disabled it and rebooted. No effect. I'm running vmware as a host, not as a client, so it shouldn't be causing a boot issue.

5. Emptied the contents of ~/.cache and rebooted since that causes issues for some people. No effect.

6. Searching through kernel logs doesn't show anything coming up consistently that didn't also show up before I started having the problem.


Any ideas?

---

### Post by springshades on 2018-03-16
After installing lightdm, installing xubuntu-desktop to see if it was a KDE problem, purging nvidia drivers, installing different nvidia driver versions, removing the graphic drivers PPA to make sure there wasn't anything coming from there, trying to reconfigure X... and several other things I don't remember.

This was a stupid kernel issue...

Kernel version 4.4.0-116 in the newest update broke the nvidia drivers. Downgrading to an older kernel version fixed everything immediately. Rather than messing around with the whole... which version of the kernel contained which security fix... thing. I changed to the HWE kernel version instead of the LTS version. That also fixed everything. It's that specific kernel, and it doesn't play well with either nvidia-384 (from the main Ubuntu repositories) or nvidia-390 (from the graphics drivers PPA).

---

