---
title: "[xubuntu] Troubleshooting failure to suspend 14.04"
date: 2014-07-30
forum: Desktop Environments
---

### Post by nick.spacek on 2014-07-30
I have been having intermittent problems suspending lately, I'm not sure what is causing it.

There seems to be some process interrupting the suspend, or that is not responding and the suspend gives up. The screen turns black, but not off, then after some time I get to the lightlocker login.

I can tell within a couple of second whether the suspend will work because during a successful suspend the screen turns black and then off.

Once this happens I have to shutdown in a terminal. When the shutdown begins to look processes it must kill the process blocking the suspend because the suspend completes in the middle of the shutdown. Then I have to start the computer again so that the shutdown will complete.

My attempts to investigate logs have not proved useful. It seems like it should be logged somewhere the state of the suspend and what process is blocking it. Where should I look? Thanks.

---

### Post by Toz on 2014-07-30
Hello and welcome to the forums.

The log files that would yield the most information would be /var/log/pm-suspend.log and a part of /var/log/syslog. Feel free to post back the contents of /var/log/pm-suspend.log (within **[noparse]```
 
```[/noparse]** tags)and the results of:
```
cat /var/log/syslog | grep PM:
```

Also useful would be some more detailed information about your computer. Make, model and video card information would be helpful.

More information about troubleshooting can be found at the link in my signature in this post.

---

### Post by nick.spacek on 2014-07-31
Here is the filtered output from syslog:
```
Jul 30 17:09:48 titan kernel: [31434.797191] PM: Syncing filesystems ... done.
Jul 30 17:09:48 titan kernel: [31434.821966] PM: Preparing system for mem sleep
Jul 30 21:49:58 titan kernel: [31434.944400] PM: Entering mem sleep
Jul 30 21:49:58 titan kernel: [31441.036298] PM: suspend of devices complete after 6087.905 msecs
Jul 30 21:49:58 titan kernel: [31441.036532] PM: late suspend of devices complete after 0.230 msecs
Jul 30 21:49:58 titan kernel: [31441.116114] PM: noirq suspend of devices complete after 79.531 msecs
Jul 30 21:49:58 titan kernel: [31441.119898] PM: Saving platform NVS memory
Jul 30 21:49:58 titan kernel: [31441.433573] PM: Restoring platform NVS memory
Jul 30 21:49:58 titan kernel: [31441.778086] PM: noirq resume of devices complete after 190.739 msecs
Jul 30 21:49:58 titan kernel: [31441.778250] PM: early resume of devices complete after 0.136 msecs
Jul 30 21:49:58 titan kernel: [31442.478869] PM: resume of devices complete after 700.184 msecs
Jul 30 21:49:58 titan kernel: [31442.479107] PM: Finishing wakeup.
Jul 30 22:54:52 titan kernel: [35338.710436] PM: Syncing filesystems ... done.
Jul 30 22:54:52 titan kernel: [35338.738775] PM: Preparing system for mem sleep
```

I removed logs that were from the previous resume from pm-suspend.log:
```
Initial commandline parameters: 
Wed Jul 30 22:54:52 ADT 2014: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.


Running hook /etc/pm/sleep.d/00_check_touchpad_status suspend suspend:
/etc/pm/sleep.d/00_check_touchpad_status suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux titan 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ctr                    13049  0 
ccm                    17773  0 
nfnetlink_queue        22329  0 
nfnetlink_log          17926  0 
nfnetlink              14606  2 nfnetlink_log,nfnetlink_queue
veth                   13331  0 
xt_addrtype            12635  2 
xt_conntrack           12760  1 
ipt_MASQUERADE         12880  1 
iptable_nat            13011  1 
nf_conntrack_ipv4      15012  2 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
nf_nat_ipv4            13263  1 iptable_nat
nf_nat                 21841  3 ipt_MASQUERADE,nf_nat_ipv4,iptable_nat
nf_conntrack           96976  6 ipt_MASQUERADE,nf_nat,nf_nat_ipv4,xt_conntrack,iptable_nat,nf_conntrack_ipv4
bridge                110793  0 
stp                    12976  1 bridge
llc                    14552  2 stp,bridge
aufs                  202783  79 
iptable_filter         12810  1 
ip_tables              27239  2 iptable_filter,iptable_nat
x_tables               34059  5 ip_tables,ipt_MASQUERADE,xt_conntrack,iptable_filter,xt_addrtype
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
snd_hda_codec_hdmi     46254  4 
bnep                   19624  2 
rfcomm                 69160  4 
bluetooth             391196  10 bnep,rfcomm
binfmt_misc            17468  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
snd_hda_codec_conexant    57441  1 
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17381  0 
arc4                   12608  2 
serio_raw              13462  0 
iwldvm                232285  0 
mac80211              630653  1 iwldvm
intel_ips              18664  0 
thinkpad_acpi          81013  1 
nvram                  14411  1 thinkpad_acpi
snd_seq_midi           13324  0 
iwlwifi               169932  1 iwldvm
lpc_ich                21080  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          52355  10 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
nouveau              1097199  5 
snd_hwdep              13602  1 snd_hda_codec
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_rawmidi            30144  1 snd_seq_midi
ttm                    85115  1 nouveau
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
drm_kms_helper         53081  1 nouveau
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
drm                   303102  7 ttm,drm_kms_helper,nouveau
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mei_me                 18627  0 
snd_timer              29482  2 snd_pcm,snd_seq
mei                    82276  1 mei_me
snd                    69238  32 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
i2c_algo_bit           13413  1 nouveau
soundcore              12680  1 snd
parport_pc             32701  0 
mxm_wmi                13021  1 nouveau
video                  19476  1 nouveau
ppdev                  17671  0 
mac_hid                13205  0 
lp                     17759  0 
wmi                    19177  2 mxm_wmi,nouveau
parport                42348  3 lp,ppdev,parport_pc
psmouse               106678  0 
firewire_ohci          40409  0 
e1000e                254433  0 
ahci                   25819  4 
firewire_core          68769  1 firewire_ohci
sdhci_pci              23172  0 
libahci                32560  1 ahci
sdhci                  43015  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
ptp                    18933  1 e1000e
pps_core               19382  1 ptp
             total       used       free     shared    buffers     cached
Mem:       8033536    5685728    2347808      59384     677740    1560676
-/+ buffers/cache:    3447312    4586224
Swap:     19827704          0   19827704
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.


Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.


Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.


Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.


Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.


Wed Jul 30 22:54:52 ADT 2014: performing suspend

```

---

### Post by Toz on 2014-07-31
Unfortunately, there is nothing obviously glaring to point out what the problem may be. 

A few more questions:

1. You have created a /etc/pm/sleep.d/00_check_touchpad_status hook. What is that for? Can you post back the code?

2. Can you post back the full /var/log/pm-suspend.log file? I would like to see if there is something in one if the previous failures.

3. I see your using the opensource nouveau driver for your video card. Have you tried with the proprietary nvidia driver?

Intermittent issues like this are the most difficult to troubleshoot.

---

### Post by nick.spacek on 2014-08-01
> **Toz said:**
> Unfortunately, there is nothing obviously glaring to point out what the problem may be.

This has been a source of frustration to me as well, I'm not sure where the problem is. I do sometimes get a message about a DBUS timeout so it could be a DBUS signal that is timing out, I don't know where the logs for that would be though. The message is something like "org.freedesktop.dbus.error.noreply". If I see it again I will add.

> **Toz said:**
> 1. You have created a /etc/pm/sleep.d/00_check_touchpad_status hook. What is that for? Can you post back the code?
```
#!/bin/sh#copy to /etc/pm/sleep.d
LOGFILE="/var/log/sleep.log"


case "$1" in
        resume|thaw)
                echo "Resumed from suspend at `date`" >> "$LOGFILE"
                /usr/bin/python3 /opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/check_touchpad_status.py
                echo "Touchpad enabled"
                ;;
esac
```

It is for disabling my touchpad and was added by touchpad-indicator.

> **Toz said:**
> 2. Can you post back the full /var/log/pm-suspend.log file? I would like to see if there is something in one if the previous failures.

This looks to be about a month's worth: [ATTACH]255187[/ATTACH]

> **Toz said:**
> 3. I see your using the opensource nouveau driver for your video card. Have you tried with the proprietary nvidia driver?

I have not, I have used it in the past and it always seems to cause additional trouble. I just left the open source one because it was working well until the standby issues started.

I forgot to mention my machine specs, it's a Thinkpad T510 with NVIDIA Corporation GT218M [NVS 3100M] (rev a2) (reported by lspci).

Thanks for looking into this.

---

### Post by Toz on 2014-08-01
I see you've run a debug suspend session. 

I also see this:
> Running hook /etc/pm/sleep.d/00_check_touchpad_status resume suspend:
Unable to connect to X server
'NoneType' object has no attribute 'lower'
org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Touchpad-Indicator is not working
Touchpad is disabled
Touchpad enabled
/etc/pm/sleep.d/00_check_touchpad_status resume suspend: success.

Does the touchpad-indicator work after suspend? Does it restore the touchpad's state? I'm not sure if this is the cause (you always get the message even if the suspend was successful or not), but it might be worth it to try deleting that file (you can always re-create it if you need it). See if it makes a difference.

---

### Post by nick.spacek on 2014-08-01
That's a great idea, I hadn't noticed "org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11" when I was looking at those logs.

I will try removing it and see if I encounter the problem over the next few days. When I resume successfully the touchpad is disabled as it always is and I've never noticed an instance where it has been re-enabled, but I will keep a watch for that behavior.

---

### Post by nick.spacek on 2014-08-07
Well, I was very hopeful as I hadn't encountered the problem until last night. Then, just as in the past, the suspend failed.

I have seen a scattering of similar sounding suspend problems:

[http://ubuntuforums.org/showthread.php?t=2223084&p=13018695#post13018695](http://ubuntuforums.org/showthread.php?t=2223084&p=13018695#post13018695)

[http://askubuntu.com/questions/489912/thinkpad-does-not-wake-from-sleep-14-04](http://askubuntu.com/questions/489912/thinkpad-does-not-wake-from-sleep-14-04)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1292627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1292627)

I don't know if they are all encountering the exact same issue, but it sounds similar. How do we go about diagnosing where the problem is (e.g. if it is a kernel issue)? Is there another source for debugging this that can be enabled?

---

### Post by Toz on 2014-08-07
There is information about running a Resume Trace debug of the suspend process [here]("https://wiki.ubuntu.com/DebuggingKernelSuspend#A.22resume-trace.22_debugging_procedure_for_finding_buggy_drivers"). Given that the problem is intermittent, the issue that you will face is trying to get the suspend to fail while running a resume trace. The other option is to create a bug report of your own and start the process of testing different kernels.

---

