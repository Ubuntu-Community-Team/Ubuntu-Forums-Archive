---
title: "I can't suspend ubuntu"
date: 2012-06-01
forum: Desktop Environments
---

### Post by mp19uy on 2012-06-01
First of all, hi to everyone, this is my first post here and this week I decided to turn from Windows to Linux permanently.

I'm using ubuntu 12.04 LTS x64 and I'm having some trouble when I try to suspend.
Sometimes it just do it right, but other times when I press the suspend button, either stays awake in a black screen or goes the "blocked screen" (the one that asks you to input user password to login back to you account).

Well, and this is just one of the problems I have.

The other problem is that, when I succeed in suspend, then when I resume, I have the fan of my ATI Vga running at 100% of its speed, and that noise is really loud.

Normally I use the command: 
```
aticonfig --pplib-cmd "set fanspeed 0 50"
```
at the startup of the system to decrease the speed of it, but I can't do the same when I resume from suspend.

I've tried with a script at /etc/pm/sleep.d/atifanspeed.sh

Which is:
```

#!/bin/bash
case "$1" in       
    thaw|resume)
        aticonfig --pplib-cmd "set fanspeed 0 50"
        ;;
    *)
        ;;
esac
exit $?

```

But it didn't work. I suspect that the problem isn't the script itself, maybe there is happening something when I try to suspend that doesn't allow my script to be executed.
Of course I set chmod +x to this script.


Anyway, I will be so grateful if someone can give me a hand with this, I'm just a beginner at linux but I'm decided to learn to use it.

BTW, I apologize if you see any grammar error on my writing, English isn't my primary languange and I'm still learning it :)

---

### Post by mp19uy on 2012-06-02
Bumping this.
(I don't know if it's allowed or not to bump posts here, at least I didn't find anything related to it, in the rules)

---

### Post by Toz on 2012-06-03
Hello and welcome to the forums.

Can we get some more info about your computer? The make and model would be a good start. There might exist a known fix/workaround.

Also, there is a log file that logs all suspend attempts. It might be a good idea to have a look at this log file as well. Post back the contents of **/var/log/pm-suspend.log**

And finally, there might be some useful info in syslog. Run the following command in a terminal window and post back the results:
```
cat /var/log/syslog | grep PM:
```

---

### Post by mp19uy on 2012-06-12
Info about the computer:
CPU: Intel i7 920.
Motherboard: [URL="http://es.gigabyte.com/products/page/mb/ga-ex58-ud3r_10/"]GA-EX58-UD3R[/HTML] (Gigabyte)

Running Ubuntu 12.04 LTS x64


First I turned on the computer, then I suspended it at 19:12, and it suspended without problems, then I woke it and tried to suspended it again at 19:14 but I couldnt, it got stuck at a black screen with the prompt blinking.
Then I waited for 5 minuted and had to restart it manually by pressing the physical button.
That is all, here all the logs:


/var/log/pm-suspend.log
```

Initial commandline parameters: 
Tue Jun 12 19:12:38 UYT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux mp19uy 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
arc4                   12529  2 
psmouse                87692  0 
joydev                 17693  0 
mxm_wmi                12979  0 
snd_hda_codec_hdmi     32474  1 
rtl8187                57035  0 
mac80211              506816  1 rtl8187
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
cfg80211              205544  2 rtl8187,mac80211
snd_seq_midi           13324  0 
eeprom_93cx6           12725  1 rtl8187
snd_rawmidi            30748  1 snd_seq_midi
snd_ctxfi             111202  2 
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_ctxfi
serio_raw              13211  0 
snd_seq_midi_event     14899  1 snd_seq_midi
fglrx                3263886  81 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 47199  0 
hid                    99559  1 usbhid
i7core_edac            28102  0 
snd                    78855  18 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_ctxfi,snd_pcm,snd_seq,snd_timer,snd_seq_device
edac_core              53746  3 i7core_edac
soundcore              15091  1 snd
snd_page_alloc         18529  3 snd_hda_intel,snd_ctxfi,snd_pcm
wmi                    19256  1 mxm_wmi
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
pata_jmicron           12747  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       6112484     771128    5341356          0      46524     227956
-/+ buffers/cache:     496648    5615836
Swap:      5859324          0    5859324

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

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

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/atifanspeed.sh suspend suspend:

/etc/pm/sleep.d/atifanspeed.sh suspend suspend: not executable.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jun 12 19:12:40 UYT 2012: performing suspend
Tue Jun 12 19:12:58 UYT 2012: Awake.
Tue Jun 12 19:12:58 UYT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /etc/pm/sleep.d/atifanspeed.sh resume suspend:

/etc/pm/sleep.d/atifanspeed.sh resume suspend: not executable.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Jun 12 19:13:00 UYT 2012: Finished.
Initial commandline parameters: 
Tue Jun 12 19:14:07 UYT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux mp19uy 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
arc4                   12529  2 
psmouse                87692  0 
joydev                 17693  0 
mxm_wmi                12979  0 
snd_hda_codec_hdmi     32474  1 
rtl8187                57035  0 
mac80211              506816  1 rtl8187
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
cfg80211              205544  2 rtl8187,mac80211
snd_seq_midi           13324  0 
eeprom_93cx6           12725  1 rtl8187
snd_rawmidi            30748  1 snd_seq_midi
snd_ctxfi             111202  2 
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_ctxfi
serio_raw              13211  0 
snd_seq_midi_event     14899  1 snd_seq_midi
fglrx                3263886  93 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 47199  0 
hid                    99559  1 usbhid
i7core_edac            28102  0 
snd                    78855  18 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_ctxfi,snd_pcm,snd_seq,snd_timer,snd_seq_device
edac_core              53746  3 i7core_edac
soundcore              15091  1 snd
snd_page_alloc         18529  3 snd_hda_intel,snd_ctxfi,snd_pcm
wmi                    19256  1 mxm_wmi
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
pata_jmicron           12747  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       6112484    1252320    4860164          0      48968     400616
-/+ buffers/cache:     802736    5309748
Swap:      5859324          0    5859324

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

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

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/atifanspeed.sh suspend suspend:

/etc/pm/sleep.d/atifanspeed.sh suspend suspend: not executable.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jun 12 19:14:09 UYT 2012: performing suspend

```


and the syslog

```

Jun 12 18:47:02 mp19uy kernel: [ 1055.652689] PM: Syncing filesystems ... done.
Jun 12 18:47:02 mp19uy kernel: [ 1055.655206] PM: Preparing system for mem sleep
Jun 12 18:47:02 mp19uy kernel: [ 1055.684136] PM: Entering mem sleep
Jun 12 18:47:02 mp19uy kernel: [ 1055.804063] PM: suspend of drv:snd_hda_intel dev:0000:02:00.1 complete after 117.564 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1055.854349] PM: suspend of drv:sd dev:1:0:0:0 complete after 169.652 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1055.854429] PM: suspend of drv:scsi dev:target1:0:0 complete after 169.422 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1055.854438] PM: suspend of drv:scsi dev:host1 complete after 168.250 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1055.868012] PM: suspend of drv:ahci dev:0000:07:00.0 complete after 181.586 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1055.868058] PM: suspend of drv:pcieport dev:0000:00:1c.1 complete after 181.253 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1055.932546] PM: suspend of drv:fglrx_pci dev:0000:02:00.0 complete after 246.114 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1055.932660] PM: suspend of drv:pcieport dev:0000:00:03.0 complete after 245.793 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1056.315710] PM: suspend of drv:ehci_hcd dev:0000:00:1d.7 complete after 629.342 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1056.315740] PM: suspend of drv: dev:pci0000:00 complete after 629.133 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1056.315762] PM: suspend of devices complete after 631.946 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1056.315765] PM: suspend devices took 0.632 seconds
Jun 12 18:47:02 mp19uy kernel: [ 1056.363930] PM: late suspend of devices complete after 48.196 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1056.365216] PM: Saving platform NVS memory
Jun 12 18:47:02 mp19uy kernel: [ 1057.095667] PM: Restoring platform NVS memory
Jun 12 18:47:02 mp19uy kernel: [ 1057.495421] PM: early resume of devices complete after 1.589 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615525] PM: resume of drv:hub dev:7-0:1.0 complete after 119.367 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615529] PM: resume of drv: dev:ep_00 complete after 119.328 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615536] PM: resume of drv:hub dev:5-0:1.0 complete after 119.565 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615539] PM: resume of drv:hub dev:6-0:1.0 complete after 119.469 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615542] PM: resume of drv: dev:ep_00 complete after 119.524 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615545] PM: resume of drv: dev:ep_00 complete after 119.433 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615549] PM: resume of drv: dev:ep_81 complete after 119.369 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615553] PM: resume of drv: dev:ep_81 complete after 119.560 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615557] PM: resume of drv: dev:ep_81 complete after 119.471 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615569] PM: resume of drv:hub dev:8-0:1.0 complete after 119.330 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615574] PM: resume of drv: dev:ep_81 complete after 119.314 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615577] PM: resume of drv: dev:ep_00 complete after 119.301 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615582] PM: resume of drv:hub dev:4-0:1.0 complete after 119.730 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615587] PM: resume of drv: dev:ep_00 complete after 119.673 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.615591] PM: resume of drv: dev:ep_81 complete after 119.705 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.719474] PM: resume of drv:hub dev:3-0:1.0 complete after 223.765 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.719477] PM: resume of drv: dev:ep_00 complete after 223.754 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.719487] PM: resume of drv: dev:ep_81 complete after 223.772 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.821861] PM: resume of drv:snd_ctxfi dev:0000:09:00.0 complete after 326.413 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.985601] PM: resume of drv:usbhid dev:3-1:1.0 complete after 489.119 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.985605] PM: resume of drv:usbhid dev:3-1:1.1 complete after 489.083 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.985660] PM: resume of drv: dev:ep_81 complete after 489.158 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.985662] PM: resume of drv: dev:ep_82 complete after 489.119 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1057.985666] PM: resume of drv: dev:ep_00 complete after 489.102 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1058.336434] PM: resume of drv:fglrx_pci dev:0000:02:00.0 complete after 841.394 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1058.538283] PM: resume of drv:usbhid dev:3-2:1.0 complete after 1042.071 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1058.538292] PM: resume of drv:usbhid dev:3-2:1.1 complete after 1042.038 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1058.538350] PM: resume of drv: dev:ep_82 complete after 1042.075 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1058.538354] PM: resume of drv: dev:ep_00 complete after 1042.059 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1058.538357] PM: resume of drv: dev:ep_81 complete after 1042.124 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1061.544907] PM: resume of drv:snd_hda_intel dev:0000:02:00.1 complete after 4052.143 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1065.705890] PM: resume of drv:sd dev:1:0:0:0 complete after 8215.325 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1065.705962] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 8215.324 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1065.705979] PM: resume of drv:scsi_disk dev:1:0:0:0 complete after 8196.081 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1065.706091] PM: resume of devices complete after 8216.479 msecs
Jun 12 18:47:02 mp19uy kernel: [ 1065.988986] PM: resume devices took 8.500 seconds
Jun 12 18:47:02 mp19uy kernel: [ 1065.989051] PM: Finishing wakeup.
Jun 12 18:48:42 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 12 18:48:42 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jun 12 18:48:42 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jun 12 18:48:42 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bfee0000 - 00000000bfee2000
Jun 12 18:48:42 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bfee2000 - 00000000bfef0000
Jun 12 18:48:42 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bfef0000 - 00000000bff00000
Jun 12 18:48:42 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000e0000000
Jun 12 18:48:42 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Jun 12 18:48:42 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Jun 12 18:48:42 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Jun 12 18:48:42 mp19uy kernel: [    0.921163] PM: Registering ACPI NVS region at bfee0000 (8192 bytes)
Jun 12 18:48:42 mp19uy kernel: [    1.453042] PM: Hibernation image not present or could not be loaded.
Jun 12 19:12:01 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 12 19:12:01 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jun 12 19:12:01 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jun 12 19:12:01 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bfee0000 - 00000000bfee2000
Jun 12 19:12:01 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bfee2000 - 00000000bfef0000
Jun 12 19:12:01 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bfef0000 - 00000000bff00000
Jun 12 19:12:01 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000e0000000
Jun 12 19:12:01 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Jun 12 19:12:01 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Jun 12 19:12:01 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Jun 12 19:12:01 mp19uy kernel: [    0.924968] PM: Registering ACPI NVS region at bfee0000 (8192 bytes)
Jun 12 19:12:01 mp19uy kernel: [    1.456796] PM: Hibernation image not present or could not be loaded.
Jun 12 19:12:58 mp19uy kernel: [   51.227415] PM: Syncing filesystems ... done.
Jun 12 19:12:58 mp19uy kernel: [   51.227937] PM: Preparing system for mem sleep
Jun 12 19:12:58 mp19uy kernel: [   51.258750] PM: Entering mem sleep
Jun 12 19:12:58 mp19uy kernel: [   51.378685] PM: suspend of drv:snd_hda_intel dev:0000:02:00.1 complete after 117.847 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.504882] PM: suspend of drv:fglrx_pci dev:0000:02:00.0 complete after 244.044 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.505000] PM: suspend of drv:pcieport dev:0000:00:03.0 complete after 243.812 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.511594] PM: suspend of drv:sd dev:1:0:0:0 complete after 252.460 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.511684] PM: suspend of drv:scsi dev:target1:0:0 complete after 252.547 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.511766] PM: suspend of drv:scsi dev:host1 complete after 251.256 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.526671] PM: suspend of drv:ahci dev:0000:07:00.0 complete after 265.906 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.526686] PM: suspend of drv:pcieport dev:0000:00:1c.1 complete after 265.613 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.862590] PM: suspend of drv:ehci_hcd dev:0000:00:1d.7 complete after 601.691 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.862600] PM: suspend of drv: dev:pci0000:00 complete after 601.478 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.862627] PM: suspend of devices complete after 603.868 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.862629] PM: suspend devices took 0.604 seconds
Jun 12 19:12:58 mp19uy kernel: [   51.910808] PM: late suspend of devices complete after 48.186 msecs
Jun 12 19:12:58 mp19uy kernel: [   51.912094] PM: Saving platform NVS memory
Jun 12 19:12:58 mp19uy kernel: [   52.646922] PM: Restoring platform NVS memory
Jun 12 19:12:58 mp19uy kernel: [   53.082803] PM: early resume of devices complete after 1.590 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203061] PM: resume of drv: dev:ep_00 complete after 119.420 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203064] PM: resume of drv:hub dev:5-0:1.0 complete after 119.466 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203069] PM: resume of drv: dev:ep_00 complete after 119.187 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203073] PM: resume of drv:hub dev:8-0:1.0 complete after 119.226 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203077] PM: resume of drv: dev:ep_00 complete after 119.266 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203080] PM: resume of drv: dev:ep_81 complete after 119.451 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203085] PM: resume of drv:hub dev:7-0:1.0 complete after 119.311 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203088] PM: resume of drv: dev:ep_81 complete after 119.226 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203101] PM: resume of drv:hub dev:4-0:1.0 complete after 119.709 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203106] PM: resume of drv: dev:ep_81 complete after 119.616 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203110] PM: resume of drv: dev:ep_81 complete after 119.323 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203112] PM: resume of drv: dev:ep_00 complete after 119.581 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203116] PM: resume of drv: dev:ep_00 complete after 119.394 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203121] PM: resume of drv:hub dev:6-0:1.0 complete after 119.440 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.203127] PM: resume of drv: dev:ep_81 complete after 119.425 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.311032] PM: resume of drv:hub dev:3-0:1.0 complete after 227.846 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.311037] PM: resume of drv: dev:ep_00 complete after 227.836 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.311041] PM: resume of drv: dev:ep_81 complete after 227.849 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.409507] PM: resume of drv:snd_ctxfi dev:0000:09:00.0 complete after 326.566 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.582998] PM: resume of drv: dev:ep_00 complete after 498.705 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.583001] PM: resume of drv:usbhid dev:3-1:1.0 complete after 498.779 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.583006] PM: resume of drv:usbhid dev:3-1:1.1 complete after 498.743 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.583013] PM: resume of drv: dev:ep_81 complete after 498.776 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.583015] PM: resume of drv: dev:ep_82 complete after 498.740 msecs
Jun 12 19:12:58 mp19uy kernel: [   53.916102] PM: resume of drv:fglrx_pci dev:0000:02:00.0 complete after 833.288 msecs
Jun 12 19:12:58 mp19uy kernel: [   54.136594] PM: resume of drv:usbhid dev:3-2:1.1 complete after 1052.341 msecs
Jun 12 19:12:58 mp19uy kernel: [   54.136598] PM: resume of drv: dev:ep_00 complete after 1052.305 msecs
Jun 12 19:12:58 mp19uy kernel: [   54.136602] PM: resume of drv:usbhid dev:3-2:1.0 complete after 1052.378 msecs
Jun 12 19:12:58 mp19uy kernel: [   54.136606] PM: resume of drv: dev:ep_82 complete after 1052.340 msecs
Jun 12 19:12:58 mp19uy kernel: [   54.136613] PM: resume of drv: dev:ep_81 complete after 1052.383 msecs
Jun 12 19:12:58 mp19uy kernel: [   57.090388] PM: resume of drv:snd_hda_intel dev:0000:02:00.1 complete after 4008.237 msecs
Jun 12 19:12:58 mp19uy kernel: [   60.694454] PM: resume of drv:sd dev:1:0:0:0 complete after 7612.114 msecs
Jun 12 19:12:58 mp19uy kernel: [   60.694535] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 7612.178 msecs
Jun 12 19:12:58 mp19uy kernel: [   60.694603] PM: resume of drv:scsi_disk dev:1:0:0:0 complete after 7593.032 msecs
Jun 12 19:12:58 mp19uy kernel: [   60.694713] PM: resume of devices complete after 7613.482 msecs
Jun 12 19:12:58 mp19uy kernel: [   60.977661] PM: resume devices took 7.900 seconds
Jun 12 19:12:58 mp19uy kernel: [   60.989635] PM: Finishing wakeup.
Jun 12 19:19:41 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 12 19:19:41 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jun 12 19:19:41 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jun 12 19:19:41 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bfee0000 - 00000000bfee2000
Jun 12 19:19:41 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bfee2000 - 00000000bfef0000
Jun 12 19:19:41 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bfef0000 - 00000000bff00000
Jun 12 19:19:41 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000e0000000
Jun 12 19:19:41 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Jun 12 19:19:41 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Jun 12 19:19:41 mp19uy kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Jun 12 19:19:41 mp19uy kernel: [    0.921172] PM: Registering ACPI NVS region at bfee0000 (8192 bytes)
Jun 12 19:19:41 mp19uy kernel: [    1.457111] PM: Hibernation image not present or could not be loaded.

```

---

### Post by Toz on 2012-06-12
> Running hook /etc/pm/sleep.d/atifanspeed.sh suspend suspend:

/etc/pm/sleep.d/atifanspeed.sh suspend suspend: not executable.

Are you sure its set executable? Can you post back:
```
ls -l /etc/pm/sleep.d/atifanspeed.sh
```

Otherwise, try including a suspend hibernate case as such:
```

#!/bin/bash
case "$1" in   
    suspend|hibernate)
        #do nothing
        ;;
    thaw|resume)
        aticonfig --pplib-cmd "set fanspeed 0 50"
        ;;
    *)
        ;;
esac
exit $?
```

EDIT: You might also want to try putting the full path to the aticonfig command. It might not be finding that command.

---

### Post by mp19uy on 2012-06-27
Sorry to take so long to answer, the thing is I don't use ubuntu everyday and I stopped using this computer(the one with the problem) for the last week, so I almost forgot it. It won't happen again.

The return of
```
ls -l /etc/pm/sleep.d/atifanspeed.sh
```
is
```
-rw-r--r-- 1 root root 142 Jun  1 10:25 /etc/pm/sleep.d/atifanspeed.sh
```

Now I modified the file:
```
#!/bin/bash
case "$1" in    
    suspend|hibernate)
	#do nothing   
	;;
    thaw|resume)
        /usr/bin/aticonfig --pplib-cmd "set fanspeed 0 50"
        ;;
    *)
        ;;
esac
exit $?

```

I'm going to try it now.

EDIT:
I've just suspended it and then when I resumed, the script didn't worked because the fan reseted to his "default" speed.

BUT, fortunately at least for now, I could say that I've not more the problem with the inability to suspend, I've just tried a few times in a row to suspend it, and all the times it did correctly without any stuck and above of all, very fast, that's great!


And editing again, indeed, I've just saw that it haven't the right permissions, now I set chmod 755 permissions to the script.


Now I see that the problem is here, this is what return pm-suspend.log when I try to execute the script:

```

Running hook /etc/pm/sleep.d/atifanspeed.sh resume suspend:
ati_pplib_cmd: Unable to open display `'.
aticonfig: parsing the command-line failed.

/etc/pm/sleep.d/atifanspeed.sh resume suspend: Returned exit code 1.

```

---

### Post by Toz on 2012-07-01
> **mp19uy said:**
> 
```

Running hook /etc/pm/sleep.d/atifanspeed.sh resume suspend:
ati_pplib_cmd: Unable to open display `'.
aticonfig: parsing the command-line failed.

/etc/pm/sleep.d/atifanspeed.sh resume suspend: Returned exit code 1.

```

Try this script. It should make your display accessible:
```
#!/bin/bash

case "$1" in    
    suspend|hibernate)
	#do nothing   
	;;
    thaw|resume)
        USER=<username>
        USERHOME=/home/$USER
        export XAUTHORITY="$USERHOME/.Xauthority"
        export DISPLAY=":0"
        su $USER -c "/usr/bin/aticonfig --pplib-cmd \"set fanspeed 0 50\""
        ;;
    *)
        ;;
esac
exit $?

```
...make sure to replace <username> with your username

---

