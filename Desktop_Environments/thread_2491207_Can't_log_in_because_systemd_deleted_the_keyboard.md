---
title: "Can't log in because systemd deleted the keyboard"
date: 2023-09-29
forum: Desktop Environments
---

### Post by John Nagle on 2023-09-29
This is new. Twice now, I've been unable to log into a desktop system that is not turned off or hibernating, but is only in "lock" mode. Nothing I can do
with the keyboard will wake up the system. 

Looking at syslog, I can see systemd doing its daily thing:

```
Sep 29 06:54:48 user-desktop systemd[1]: Starting Daily apt upgrade and clean activities...
...
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "40"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event1  - Power Button: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "43"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event0  - Power Button: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "44"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event4  - Logitech USB Optical Mouse: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "45"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event6  - ASRock LED Controller: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "46"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event5  - Generic USB DESKTOP MIC: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "47"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event2  - Logitech USB Keyboard: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "48"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "48"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event3  - Logitech USB Keyboard: device removed
```

More log file as attachment: [ATTACH]292810[/ATTACH] There's a lot of stuff there involving NVidia Hibernate, which may be related.

OK, so systemd ran something that **deleted the keyboard**. Of course I can't get the system to wake up. Had to reset the computer.

Most days, that doesn't happen, and the log looks like this:

```
Sep 24 06:13:46 user-desktop systemd[1]: Starting Daily apt upgrade and clean activities...
Sep 24 06:13:46 user-desktop snapd-desktop-i[694725]: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
Sep 24 06:13:46 user-desktop snapd-desktop-i[694725]: Failed to do gtk init. Waiting for a new session with desktop capabilities.
Sep 24 06:13:46 user-desktop snapd-desktop-i[694725]: Checking session /org/freedesktop/login1/session/_32...
Sep 24 06:13:46 user-desktop snapd-desktop-i[694725]: Checking session /org/freedesktop/login1/session/_38...
Sep 24 06:13:46 user-desktop snapd-desktop-i[694725]: Is a desktop session! Forcing a reload.
Sep 24 06:13:46 user-desktop snapd-desktop-i[694725]: Checking session /org/freedesktop/login1/session/c2...
Sep 24 06:13:46 user-desktop snapd-desktop-i[694725]: Checking session /org/freedesktop/login1/session/c1...
Sep 24 06:13:46 user-desktop snapd-desktop-i[694725]: Loop exited. Forcing reload.
Sep 24 06:13:47 user-desktop systemd[1]: apt-daily-upgrade.service: Deactivated successfully.
Sep 24 06:13:47 user-desktop systemd[1]: Finished Daily apt upgrade and clean activities.

```

What is systemd *doing*? 

22.04 LTS, x86-64, updated to about two weeks ago. 
Nvidia driver 535, the recommended driver. 
NVidia 3070 GPU
X-windows, not Wayland.

---

### Post by #&amp;thj^% on 2023-09-29
Very vague info to go off, not your fault of course.
Can you show us this please:
```
sudo bootctl

```
have you changed anything in grub?
And i see your not on a Wayland session.

---

### Post by John Nagle on 2023-09-29
```
systemd-boot not installed in ESP.
System:
     Firmware: n/a (n/a)
  Secure Boot: disabled
   Setup Mode: setup
 TPM2 Support: no
 Boot into FW: supported

Current Boot Loader:
      Product: n/a
     Features: &#10007; Boot counting
               &#10007; Menu timeout control
               &#10007; One-shot menu timeout control
               &#10007; Default entry control
               &#10007; One-shot entry control
               &#10007; Support for XBOOTLDR partition
               &#10007; Support for passing random seed to OS
               &#10007; Boot loader sets ESP information
          ESP: n/a
         File: &#9492;&#9472;n/a

Random Seed:
 Passed to OS: no
 System Token: not set
       Exists: no

Available Boot Loaders on ESP:
          ESP: /boot/efi (/dev/disk/by-partuuid/5c55660e-0921-421b-8dd4-6db456a>
         File: &#9492;&#9472;/EFI/BOOT/bootx64.efi

Boot Loaders Listed in EFI Variables:
        Title: ubuntu
           ID: 0x0000
       Status: active, boot-order
    Partition: /dev/disk/by-partuuid/5c55660e-0921-421b-8dd4-6db456a06fe2
         File: &#9492;&#9472;/EFI/UBUNTU/SHIMX64.EFI

Boot Loader Entries:
        $BOOT: /boot/efi (/dev/disk/by-partuuid/5c55660e-0921-421b-8dd4-6db456a>

0 entries, no entry could be determined as default.
```

Haven't changed anything in Grub.

This is a new problem on a system that's been running well for several years.

---

### Post by #&amp;thj^% on 2023-09-29
> **John Nagle said:**
> 

Haven't changed anything in Grub.

This is a new problem on a system that's been running well for several years.

Understood, and the same on mine, many many years. (in short a semi-rolling mash)
I also have nvidia, but I've not seen anything like you report, but not a Gnome user either.
This: Logitech USB Optical Mouse: device removed, and many other removals sounds to me as Power Feature problem more so than a systemd issue.```
bootctl status
Failed to read "/boot/efi/EFI/systemd": Permission denied
Failed to open '/boot/efi//loader/loader.conf': Permission denied
System:
      Firmware: n/a (n/a)
 Firmware Arch: x64
   Secure Boot: disabled (disabled)
  TPM2 Support: yes
  Boot into FW: supported

Current Boot Loader:
      Product: GRUB 2.12~rc1-10ubuntu2
     Features: &#10007; Boot counting
               &#10007; Menu timeout control
               &#10007; One-shot menu timeout control
               &#10007; Default entry control
               &#10007; One-shot entry control
               &#10007; Support for XBOOTLDR partition
               &#10007; Support for passing random seed to OS
               &#10007; Load drop-in drivers
               &#10007; Support Type #1 sort-key field
               &#10007; Support @saved pseudo-entry
               &#10007; Support Type #1 devicetree field
               &#10003; Boot loader sets ESP information

```
nothing is set in concrete yet, but you peaked my curiosity.
```
sudo systemctl list-units --failed
[sudo] password for me: 
  UNIT                    LOAD   ACTIVE SUB    DESCRIPTION                     >
&#9679; casper-md5check.service loaded failed failed casper-md5check Verify Live ISO >
&#9679; networking.service      loaded failed failed Raise network interfaces

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.
2 loaded units listed.

```

---

### Post by John Nagle on 2023-09-29
A somewhat similar problem was reported back in 2021 on NVidia forums. [https://forums.developer.nvidia.com/t/ubuntu-20-04-with-nvidia-460-driver-freezes-randomly-after-resume-from-suspend-hibernate/173818/2](https://forums.developer.nvidia.com/t/ubuntu-20-04-with-nvidia-460-driver-freezes-randomly-after-resume-from-suspend-hibernate/173818/2)

That was back at Ubuntu 20.04 and NVidia driver 460, and I'm at  22.04 and the current 535 driver. So the advice there to upgrade the  driver is not helpful.

There's a good chance that this has something to do with NVidia's "hibernate" system. Why systemd called for a GPU hibernate at 6 AM on a system that had been locked overnight is not clear. Any ideas?

I don't normally suspend or hibernate this system. That's never worked well on Linux.

---

### Post by John Nagle on 2023-09-29
More years-old discussion on this: [https://askubuntu.com/questions/1345073/suspend-not-working-properly-cannot-wake-up-on-ubuntu-20-04-with-nvidia](https://askubuntu.com/questions/1345073/suspend-not-working-properly-cannot-wake-up-on-ubuntu-20-04-with-nvidia)

There are hacks there to work around the problem, statements that the hacks stop working after a while, more hacks, all for old Ubuntu 20.04.

Apparently the way NVidia suspend/resume interacts with systemd changed at some driver version. Did this ever get fixed properly?

The "fixed problem and problem came back later" suggests that all the file patching and state changes suggested were overridden by some later software update. So manual tweaking may be undesirable here.

---

### Post by #&amp;thj^% on 2023-09-29
Yes I now remember that one as well,
Well i'll look with you, please show:
```
sudo cat  /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```
as a start point

---

### Post by John Nagle on 2023-09-29
```

[Mounting, checking, etc. of internal drives]
Identity=unix-group:admin;unix-group:sudo
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*;org.freedesktop.udisks2.filesystem-mount-system;org.freedesktop.udisks2.encrypted-unlock-system;org.freedesktop.udisks2.filesystem-fstab;
ResultActive=yes

[Change CPU Frequency scaling]
Identity=unix-group:admin;unix-group:sudo
Action=org.gnome.cpufreqselector;org.mate.cpufreqselector
ResultActive=yes

[Setting the clock]
Identity=unix-group:admin;unix-group:sudo
Action=org.gnome.clockapplet.mechanism.*;org.gnome.controlcenter.datetime.configure;org.kde.kcontrol.kcmclock.save;org.freedesktop.timedate1.set-time;org.freedesktop.timedate1.set-timezone;org.freedesktop.timedate1.set-local-rtc;org.freedesktop.timedate1.set-ntp;com.canonical.controlcenter.datetime.configure;org.mate.settingsdaemon.datetimemechanism.settime
ResultActive=yes

[Adding or changing system-wide NetworkManager connections]
Identity=unix-group:admin;unix-group:sudo
Action=org.freedesktop.NetworkManager.settings.modify.system
ResultActive=yes

[Update already installed software]
Identity=unix-group:admin;unix-group:sudo
Action=org.debian.apt.upgrade-packages
ResultActive=yes

[Printer administration]
Identity=unix-group:lpadmin;unix-group:admin;unix-group:sudo
Action=org.opensuse.cupspkhelper.mechanism.*
ResultActive=yes

[Disable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=no

[Disable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
ResultActive=no

[Modify error reporting settings]
Identity=unix-group:admin;unix-group:sudo
Action=com.ubuntu.whoopsiepreferences.change
ResultActive=yes

[Allow admins to set the hostname,locale,keyboard,date/time without prompting]
Identity=unix-group:admin;unix-group:sudo
Action=org.freedesktop.locale1.set-locale;org.freedesktop.locale1.set-keyboard;org.freedesktop.hostname1.set-static-hostname;org.freedesktop.hostname1.set-hostname
ResultActive=yes
 
```

---

### Post by #&amp;thj^% on 2023-09-29
That shoots my theory down:
```
[Disable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
[COLOR="#FF0000"]ResultActive=no[/COLOR]
Driver 535 solves this though
[Disable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
[COLOR="#FF0000"]ResultActive=no[/COLOR]
```
EDIT Just a thought, this is my setting:
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen true

```
to reverse:
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen false
```

---

### Post by John Nagle on 2023-09-29
Hm. Despite that disabling, NVidia Hibernate did, apparently, try to hibernate.

---

### Post by #&amp;thj^% on 2023-09-29
Please see my edit above

---

### Post by John Nagle on 2023-09-30
Didn't happen last night. Here's the log in the attachment above, with some annotation. Note in ==> NOTE <== 

```

Sep 29 06:54:48 user-desktop systemd[1]: Starting Daily apt upgrade and clean activities...
Sep 29 06:55:08 user-desktop nvidia-persistenced: Received signal 15
Sep 29 06:55:08 user-desktop systemd[1]: Stopping NVIDIA Persistence Daemon...
==> So daily apt upgrade and clean stops the NVidia Persistence Daemon. Why? <==
Sep 29 06:55:08 user-desktop nvidia-persistenced: Socket closed.
Sep 29 06:55:08 user-desktop nvidia-persistenced: PID file unlocked.
Sep 29 06:55:08 user-desktop nvidia-persistenced: PID file closed.
Sep 29 06:55:08 user-desktop nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Sep 29 06:55:08 user-desktop nvidia-persistenced: Shutdown (883)
Sep 29 06:55:08 user-desktop systemd[1]: nvidia-persistenced.service: Deactivated successfully.
Sep 29 06:55:08 user-desktop systemd[1]: Stopped NVIDIA Persistence Daemon.
Sep 29 06:55:10 user-desktop systemd[1]: Reloading.
Sep 29 06:55:11 user-desktop systemd[1]: Reloading.
Sep 29 06:55:12 user-desktop systemd[1]: Starting NVIDIA system hibernate actions...
Sep 29 06:55:12 user-desktop hibernate: nvidia-hibernate.service
Sep 29 06:55:12 user-desktop logger[89476]: <13>Sep 29 06:55:12 hibernate: nvidia-hibernate.service
Sep 29 06:55:12 user-desktop systemd[1]: Starting NVIDIA system resume actions...
Sep 29 06:55:12 user-desktop suspend: nvidia-resume.service
Sep 29 06:55:12 user-desktop logger[89477]: <13>Sep 29 06:55:12 suspend: nvidia-resume.service
Sep 29 06:55:12 user-desktop systemd[1]: Starting NVIDIA system suspend actions...
Sep 29 06:55:12 user-desktop suspend: nvidia-suspend.service
Sep 29 06:55:12 user-desktop logger[89482]: <13>Sep 29 06:55:12 suspend: nvidia-suspend.service
Sep 29 06:55:12 user-desktop nvidia-sleep.sh[89485]: chvt: Couldn't activate vt 0: No such device or address
==> First problem. Systemd, after shutting down the NVidia hibernate daemon, tried an Nvidia suspend. This failed, probably because that needs the Hibernate daemon. <==
Sep 29 06:55:12 user-desktop systemd[1]: nvidia-resume.service: Deactivated successfully.
Sep 29 06:55:12 user-desktop systemd[1]: Finished NVIDIA system resume actions.
==> What triggered all this device removal? <==
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "40"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event1  - Power Button: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "43"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event0  - Power Button: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "44"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event4  - Logitech USB Optical Mouse: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "45"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event6  - ASRock LED Controller: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "46"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event5  - Generic USB DESKTOP MIC: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "47"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event2  - Logitech USB Keyboard: device removed
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "48"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (**) Option "fd" "48"
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) event3  - Logitech USB Keyboard: device removed
Sep 29 06:55:12 user-desktop rtkit-daemon[1251]: Supervising 3 threads of 1 processes of 1 users.
Sep 29 06:55:12 user-desktop rtkit-daemon[1251]: Successfully made thread 89496 of process 3209 owned by '1001' RT at priority 5.
Sep 29 06:55:12 user-desktop rtkit-daemon[1251]: Supervising 4 threads of 1 processes of 1 users.
Sep 29 06:55:12 user-desktop acpid: client 2964[1001:1001] has disconnected
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) systemd-logind: got pause for 13:68
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) systemd-logind: got pause for 13:64
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) systemd-logind: got pause for 13:65
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) systemd-logind: got pause for 13:69
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) systemd-logind: got pause for 13:67
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) systemd-logind: got pause for 13:70
Sep 29 06:55:12 user-desktop /usr/libexec/gdm-x-session[2964]: (II) systemd-logind: got pause for 13:66
Sep 29 06:55:12 user-desktop kernel: [243682.402870] rfkill: input handler enabled
Sep 29 06:55:12 user-desktop kernel: [243682.404413] snd_hda_codec_hdmi hdaudioC0D0: HDMI: invalid ELD data byte 89
Sep 29 06:55:12 user-desktop nvidia-sleep.sh[89478]: /usr/bin/nvidia-sleep.sh: line 20: echo: write error: Input/output error
Sep 29 06:55:12 user-desktop systemd[1]: nvidia-suspend.service: Deactivated successfully.
Sep 29 06:55:12 user-desktop systemd[1]: Finished NVIDIA system suspend actions.
Sep 29 06:55:12 user-desktop systemd[1]: nvidia-hibernate.service: Main process exited, code=exited, status=1/FAILURE
Sep 29 06:55:12 user-desktop systemd[1]: nvidia-hibernate.service: Failed with result 'exit-code'.
Sep 29 06:55:12 user-desktop systemd[1]: Failed to start NVIDIA system hibernate actions.
==> Hibernate service has failed, and there's an attempt to send a notification to the user. Of course, the graphics system is now off. <==
Sep 29 06:56:07 user-desktop update-notifier.desktop[105450]: /var/cache/apt/archives/lock:
Sep 29 06:56:33 user-desktop systemd[1]: apt-daily-upgrade.service: Deactivated successfully.
Sep 29 06:56:33 user-desktop systemd[1]: Finished Daily apt upgrade and clean activities.
Sep 29 06:56:33 user-desktop systemd[1]: apt-daily-upgrade.service: Consumed 3min 48.708s CPU time.
```

Questions:
[LIST]
[*]Is daily apt update and clean supposed to be doing all this hibernate stuff?
[*]If it is, why does it deactivate the hibernate service and then try to suspend? Can that possibly work?
[*]Whose job is it to get apt update and NVidia hibernate to play well together?
[/LIST]

---

### Post by #&amp;thj^% on 2023-09-30
> **John Nagle said:**
> Didn't happen last night. Here's the log in the attachment above, with some annotation. Note in ==> NOTE <== 
What did you do different, did you use my suggestion, or just happenstance?
> **John Nagle said:**
> 
Questions:
[LIST]
[*]Is daily apt update and clean supposed to be doing all this hibernate stuff?
[*]If it is, why does it deactivate the hibernate service and then try to suspend? Can that possibly work?
[*]Whose job is it to get apt update and NVidia hibernate to play well together?
[/LIST]

It reloads services as upgraded. for the first question.
IJDK on the second question.
nVidia is proprietary so both they and kernel devs work together.(that's is what suppose to happen)
And check:
```
systemctl status nvidia-hibernate.service
&#9675; nvidia-hibernate.service - NVIDIA system hibernate actions
     Loaded: loaded (/usr/lib/systemd/system/nvidia-hibernate.service; disabled>
     Active: inactive (dead)

```

---

### Post by John Nagle on 2023-09-30
> What did you do different, did you use my suggestion, or just happenstance?

I didn't do anything to change the system state. 

So far, this has happened twice in the last two weeks. No idea what triggers it. I've posted logs for both success and fail cases.
In the success case, there is no 
```
Sep 29 06:55:08 user-desktop systemd[1]: Stopping NVIDIA Persistence Daemon...
```

[FONT=arial]In fail cases, systemd/apt update stops the various NVidia services, which triggers the problem.
I don't understand systemd enough to look for why it did that.
[/FONT]

---

### Post by #&amp;thj^% on 2023-09-30
> **John Nagle said:**
> > What did you do different, did you use my suggestion, or just happenstance?

I didn't do anything to change the system state. 

So far, this has happened twice in the last two weeks. No idea what triggers it. I've posted logs for both success and fail cases.
In the success case, there is no 
```
Sep 29 06:55:08 user-desktop systemd[1]: Stopping NVIDIA Persistence Daemon...
```

[FONT=arial]In fail cases, systemd/apt update stops the various NVidia services, which triggers the problem.
I don't understand systemd enough to look for why it did that.
[/FONT]

Sounds more like a bug now, and would need to be filed so they can at least look at the cause.
First place is:
```
sudo nvidia-bug-report.sh
```
Report Site [https://forums.developer.nvidia.com/t/if-you-have-a-problem-please-read-this-first/27131](https://forums.developer.nvidia.com/t/if-you-have-a-problem-please-read-this-first/27131)

---

### Post by John Nagle on 2023-10-01
[FONT=arial]NVidia bug, or Ubuntu systemd configuration bug? Report to NVidia or Ubuntu? 

You just know each will blame the other.
[/FONT]

---

### Post by ranger203 on 2023-10-01
I have the same problem, except that it happens while I'm working on my laptop. The screen suddenly turns black and the fans start spinning at full power.
The system is then totally unresponsive and the only thing that works is a reset by holding the power button.
The system log shows that this happens exactly at the time the Daily apt upgrade and clean starts:

```

Oct  1 11:00:48 legion systemd[1]: Starting Daily apt upgrade and clean activities...
...
Oct  1 11:01:02 legion nvidia-persistenced: Received signal 15
Oct  1 11:01:02 legion systemd[1]: Stopping NVIDIA Persistence Daemon...
Oct  1 11:01:02 legion nvidia-persistenced: Socket closed.
Oct  1 11:01:02 legion nvidia-persistenced: PID file unlocked.
Oct  1 11:01:02 legion nvidia-persistenced: PID file closed.
Oct  1 11:01:02 legion nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Oct  1 11:01:02 legion nvidia-persistenced: Shutdown (1327)
Oct  1 11:01:03 legion systemd[1]: nvidia-persistenced.service: Deactivated successfully.
Oct  1 11:01:03 legion systemd[1]: Stopped NVIDIA Persistence Daemon.
Oct  1 11:01:04 legion systemd[1]: Reloading.
Oct  1 11:01:04 legion systemd[1]: Starting Daily apt download activities...
Oct  1 11:01:04 legion systemd[1]: Reloading.
Oct  1 11:01:05 legion systemd[1]: Starting Refresh fwupd metadata and update motd...
Oct  1 11:01:05 legion systemd[1]: Starting NVIDIA system hibernate actions...
Oct  1 11:01:05 legion hibernate: nvidia-hibernate.service
Oct  1 11:01:05 legion logger[6730]: <13>Oct  1 11:01:05 hibernate: nvidia-hibernate.service
Oct  1 11:01:05 legion systemd[1]: Starting NVIDIA system resume actions...
Oct  1 11:01:05 legion suspend: nvidia-resume.service
Oct  1 11:01:05 legion logger[6731]: <13>Oct  1 11:01:05 suspend: nvidia-resume.service
Oct  1 11:01:05 legion systemd[1]: Starting NVIDIA system suspend actions...
Oct  1 11:01:05 legion suspend: nvidia-suspend.service
Oct  1 11:01:05 legion logger[6736]: <13>Oct  1 11:01:05 suspend: nvidia-suspend.service
Oct  1 11:01:05 legion systemd[1]: nvidia-resume.service: Deactivated successfully.
Oct  1 11:01:05 legion systemd[1]: Finished NVIDIA system resume actions.
Oct  1 11:01:05 legion systemd-udevd[398]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
Oct  1 11:01:05 legion systemd[1]: fwupd-refresh.service: Deactivated successfully.
Oct  1 11:01:05 legion systemd[1]: Finished Refresh fwupd metadata and update motd.
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "40"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event2  - Power Button: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "43"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event4  - Video Bus: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "44"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event5  - Video Bus: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "45"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event0  - Power Button: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "46"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event13 - Logitech USB Optical Mouse: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "47"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "48"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event15 - ITE Tech. Inc. ITE Device(8910) Wireless Radio Control: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "49"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "50"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event12 - ITE Tech. Inc. ITE Device(8295) Keyboard: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "51"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event9  - Ideapad extra buttons: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "52"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event18 - MSFT0001:00 06CB:CE78 Mouse: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "53"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event19 - MSFT0001:00 06CB:CE78 Touchpad: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "54"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event3  - AT Translated Set 2 keyboard: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "47"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event14 - ITE Tech. Inc. ITE Device(8910) Keyboard: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (**) Option "fd" "49"
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) event8  - Logitech K270: device removed
Oct  1 11:01:05 legion /usr/libexec/gdm-x-session[1979]: (II) systemd-logind: got pause for 13:68

```

Here is someone else with the same problem: [https://askubuntu.com/questions/1487396/display-just-blanks-on-daily-apt-upgrade-and-clean-activities](https://askubuntu.com/questions/1487396/display-just-blanks-on-daily-apt-upgrade-and-clean-activities)
This one may be related as well: [https://askubuntu.com/questions/1487384/screen-goes-black-with-cursor-nvidia-problem](https://askubuntu.com/questions/1487384/screen-goes-black-with-cursor-nvidia-problem)

My configuration:
22.04 LTS, x86-64
Nvidia driver 535.113.01, the recommended driver.
Nvidia RTX 3070 Laptop GPU
Windowing System: X11[URL="https://askubuntu.com/questions/1487384/screen-goes-black-with-cursor-nvidia-problem"]
[/URL]

---

### Post by #&amp;thj^% on 2023-10-01
> **John Nagle said:**
> [FONT=arial]NVidia bug, or Ubuntu systemd configuration bug? Report to NVidia or Ubuntu? 

You just know each will blame the other.
[/FONT]

Start at nVidia then Ubuntu, and yes that's the game they both play, point fingers at each other.
I know nvidia is not fond of wayland yet.

---

