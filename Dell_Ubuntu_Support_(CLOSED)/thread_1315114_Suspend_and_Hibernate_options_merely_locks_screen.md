---
title: "Suspend and Hibernate options merely locks screen"
date: 2009-11-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by guitarMan666 on 2009-11-05
This duplicates a bug report ([https://bugs.launchpad.net/dell/+bug/475087](https://bugs.launchpad.net/dell/+bug/475087)) I posted but I would like advice from a wider audience:
---------------------------
When selecting the option to "Suspend" or "Hibernate" the computer (an Inspiron 1545 n-Series), the screen merely locks and asks for a password, a behavior identical to selecting the "Lock Screen" option. This occurs no matter how either the Suspend or Hibernate options are invoked I have tried the following:

* The indicator-applet-session applet on the GNOME panel
* The dialog box that pops up on pressing the power button
* Closing the lid (invokes suspend only; on battery power)
* Allowing the power to drain below 12% (invokes hibernate only; on battery power)

The last two are set in my Power Management preferences in GNOME. When I purchased the computer in July of 2009 it came with Ubuntu 8.10 Intrepid Ibex pre-installed and these options both worked flawlessly under it. The problem began upon upgrade to Ubuntu 9.04 Jaunty Jackalope and has persisted since my upgrade to Ubuntu 9.10 Karmic Koala.

I cannot find it again, however, it seemed to be related to a bug in the Intel driver for XOrg that I saw once on Launchpad. I will add the ID of that bug if I can find it again however I do remember reading that it had a "Fix Released" for Karmic.
------------------
I posted a similar thread before but this description is more refined as I have tested more thoroughly.  I would like an option that doesn't involve installing extra utilities.  I want to see the functionality restored in the OS if it is possible.

---

### Post by rockdj on 2009-11-15
No solutions here, but my problem was fixed temporarily when I upgraded to Grub 2 on my Dell M1530 XPS laptop.  Unfortunately, that was shorted lived and now my computer will not suspend, hibernate or even shut down from the normal menu.

Even doing a 'sudo shutdown now' didn't turn off the power when I tried this morning.  Further investigation is needed here for me, but it's starting to really get on my nerves since my laptop *needs* to be turned off.

---

### Post by v1nsai on 2009-12-05
Same problem here, I'm on a Dell Studio 1555 laptop.  This is a brand new out of the box jaunty install.

Is Grub somehow involved with hibernation/suspend?  I've seen it mentioned on several threads, though I haven't found any definite solutions yet, and most of them are about 7.10 for some reason, I've had this problem on every laptop I've ever put Ubuntu on, but this one is mine so I care more >:-|

Would really like to get this fixed, a laptop without hibernation is pretty weak, shutdown/startup times are way longer than hibernating.

---

### Post by rockdj on 2009-12-08
I upgraded to Grub2 and everything is now peachy.  Whether that was Grub2 itself or something else related to what I did, I'm not sure (I don't recall specifically, since it was a little while ago now).

At any rate, I'm now having the same trouble on my Ubuntu 9.10 Desktop (Dell Optiplex 755) which was working perfectly fine until yesterday.  Looks like I'll be doing the same upgrade again here and see what happens.

EDIT:  Whoops, never mind.  I just checked my /var/log/pm-suspend.log and found the reason:
Tue Dec  8 16:23:03 EST 2009: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: kernel update inhibits hibernate (/var/run/do-not-hibernate present)
Returned exit code 1.
Tue Dec  8 16:23:04 EST 2009: Inhibit found, will not perform hibernate
Yeah, okay.  It was my update from yesterday with the new kernel stopping hibernation...

---

### Post by v1nsai on 2009-12-09
I upgraded to 9.10 and all my ACPI related problems seem to be solved :-D

I don't understand the log file you posted rockdj, how did you fix your problem?  That will probably end up happening to a few of us if an update to the kernel messed up your hibernate.

---

### Post by rockdj on 2009-12-09
> **v1nsai said:**
> I upgraded to 9.10 and all my ACPI related problems seem to be solved :-D

I don't understand the log file you posted rockdj, how did you fix your problem?  That will probably end up happening to a few of us if an update to the kernel messed up your hibernate.

My previous problem was due to a kernel update -- unbeknownst to me, doing a kernel update stopped me from being able to hibernate and just locked the screen.  That should definitely be more intuitive rather than me having to delve into logs to find out why.  Restarting the computer normally solved that issue.  

Unfortunately, now that I'm on the new kernel (2.6.31-16-generic) my hibernation falls over big time, and it's worse than just simply locking the screen directly.

tail /var/log/pm-suspend.log:
```
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Wed Dec  9 17:51:09 EST 2009: performing hibernate
Wed Dec  9 17:52:34 EST 2009: Awake.
Wed Dec  9 17:52:34 EST 2009: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.
Wed Dec  9 17:53:16 EST 2009: Finished.
```

Looks like (from the log and my observations of my desktop computer), it starts to hibernate (HDD being hammered) and "succeeds" but then decides to thaw and wake up again.  Doing a 'hibernate' in the evening at work leaves me coming back to a 'locked' computer in the morning, since it thinks it should be waking itself up 90 seconds later.

This could be a whole different issue as my laptop only just locked the screen immediately on selecting hibernate.

---

### Post by Hero of Time on 2009-12-11
Now I know why I can't hibernate from time to time (I noticed it happened every time I did a kernel update). It would be a lot better if we get a message about that after the new kernel is installed, even if it's just a minor build (got one yesterday that forced me to shut down instead of using hibernate). I sometimes put my laptop to hibernate, close the lid and put it away when I think it's done. Unplugging the power cord without a battery inside is not a good idea if it doesn't hibernate ](*,).

Just checked the section of this topic, I don't have a dell.

---

### Post by guitarMan666 on 2009-12-13
You inspired me to look through that log.  I started a suspend, and then did a tail command on that log file after unlocking.  It says:
```

$ tail /var/log/pm-suspend.log
Sun Dec 13 16:22:24 EST 2009: Running hooks for resume
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Initial commandline parameters: 
Sun Dec 13 19:54:00 EST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/etc/pm/sleep.d/00_CPU suspend suspend: /etc/pm/sleep.d/00_CPU: 21: cannot create /sys/devices/system/cpu/cpu*/online: Directory nonexistent
Returned exit code 2.
Sun Dec 13 19:54:00 EST 2009: Inhibit found, will not perform suspend
Sun Dec 13 19:54:00 EST 2009: Running hooks for resume
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.

```
The important parts are the 19:54 parts.  Any idea what /sys/devices/system/cpu/cpu*/online even is?

Also, I did an in-place upgrade for both 8.10 -> 9.04 and 9.04 -> 9.10 would an upgrade to GRUB2 be recommended?  The dev's decided not to push GRUB2 with the in-place upgrades so I was avoiding it.

---

### Post by Hero of Time on 2009-12-14
It would be very strange if a bootloader does something in your power management, so I doubt it will help.

---

### Post by peak_tibor on 2010-01-10
> **guitarMan666 said:**
> You inspired me to look through that log.  I started a suspend, and then did a tail command on that log file after unlocking.  It says:
```

$ tail /var/log/pm-suspend.log
Sun Dec 13 16:22:24 EST 2009: Running hooks for resume
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Initial commandline parameters: 
Sun Dec 13 19:54:00 EST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/etc/pm/sleep.d/00_CPU suspend suspend: /etc/pm/sleep.d/00_CPU: 21: cannot create /sys/devices/system/cpu/cpu*/online: Directory nonexistent
Returned exit code 2.
Sun Dec 13 19:54:00 EST 2009: Inhibit found, will not perform suspend
Sun Dec 13 19:54:00 EST 2009: Running hooks for resume
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.

```The important parts are the 19:54 parts.  Any idea what /sys/devices/system/cpu/cpu*/online even is?

Also, I did an in-place upgrade for both 8.10 -> 9.04 and 9.04 -> 9.10 would an upgrade to GRUB2 be recommended?  The dev's decided not to push GRUB2 with the in-place upgrades so I was avoiding it.




                 I take a closer look at "00_CPU" script, that generates the error message. It states about itself:
 "Workaround for concurrency bug in xserver-xorg-video-intel 2:2.4.1-1ubuntu10"
 I checked and realized that UBUNTU 9.10 has a much newer driver, that probably does not has that bug. This means that the workorund is probably not neccessary anymore.
 I removed "00_CPU" from its directory and the problem disappeared! Suspend and hibarnation is working now.
;)

---

### Post by guitarMan666 on 2010-01-20
After removing the 00_CPU script, I still get an "inhibit found error" specifically on my most recent attempt pm-suspend.log reports:

```
Initial commandline parameters: 
Wed Jan 20 04:45:53 EST 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux avandar 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
aes_i586                8124  1 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetadp             78536  0 
vboxnetflt             85032  0 
vboxdrv               121352  1 vboxnetflt
dm_crypt               12928  0 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
joydev                 10240  0 
snd_seq                50224  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     8636  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
wl                   1272936  0 
ip_tables              11692  1 iptable_filter
snd                    59204  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
x_tables               16544  1 ip_tables
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lib80211                6432  2 lib80211_crypt_tkip,wl
dell_wmi                2564  0 
dell_laptop             8128  0 
lp                      8964  0 
dcdbas                  7292  1 dell_laptop
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usb_storage            52576  0 
sky2                   46528  0 
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
             total       used       free     shared    buffers     cached
Mem:       2024152    1463000     561152          0      43736     755152
-/+ buffers/cache:     664112    1360040
Swap:      1983988          0    1983988
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/07-stop-play.sh suspend suspend: kill: 4: Usage: kill [-s sigspec | -signum | -sigspec] [pid | job]... or
kill -l [exitstatus]
Returned exit code 2.
Wed Jan 20 04:45:54 EST 2010: Inhibit found, will not perform suspend
Wed Jan 20 04:45:54 EST 2010: Running hooks for resume
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
```

Any idea what that other script does?  The problem occurs in the /etc/pm/sleep.d/07-stop-play.sh script.  The script is as follows:
```
!/bin/sh
pid=`ps aux | awk '/PCM4\/pcm/ && !/awk/ {print $2}'`
#echo $pid
kill -14 $pid

```
Removing this script does solve the suspend problem but, it causes anything in the DVD drive to autoplay upon (which I can work around easily by making sure the drive is empty).

---

### Post by rmknightstar on 2010-10-03
> **guitarMan666 said:**
> After removing the 00_CPU script, I still get an "inhibit found error" specifically on my most recent attempt pm-suspend.log reports:


Removing this script does solve the suspend problem but, it causes anything in the DVD drive to autoplay upon (which I can work around easily by making sure the drive is empty).


Changing the script to add a check to make sure that $pid is set worked for me
```

#!/bin/sh
pid=`ps aux | awk '/PCM4\/pcm/ && !/awk/ {print $2}'`
#echo $pid
if [ $pid ]
then
kill -14 $pid
fi

```

---

