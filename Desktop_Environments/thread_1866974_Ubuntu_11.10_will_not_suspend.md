---
title: "Ubuntu 11.10 will not suspend"
date: 2011-10-22
forum: Desktop Environments
---

### Post by curts on 2011-10-22
Using a clean install of  11.04 for AMD64 and now recently upgraded to 11.10, I have not been able to suspend my desktop.  This was never a problem in my 10.04 installation.  After considerable research, I have found that I *can* suspend this PC by installing uswsusp
```
sudo apt-get install uswsusp
```
and then adding the --force parameter.
```
sudo s2ram -f
```

Additional research revealed that by creating file '/etc/pm/config.d/00sleep_module' with the following contents
```
#######################################################################
# The following options require the uswsusp package being installed
# what options should be passed to s2ram?
# see http://en.opensuse.org/S2ram for more information
# for hal 0.5.9 and up don't set this option to get the options supplied
# by HAL
SLEEP_MODULE="uswsusp"
S2RAM_OPTS="-f"
```
I could successfully suspend from the command line using the normal OS hooks.
```
sudo pm-suspend
```

What still eludes me is suspending from Unity's system pull-down menu.  Can anyone tell me what the missing piece is?

---

### Post by voltumna on 2011-10-23
Hi
i have exactly the same issue, my newly installed ubuntu 11.10 will not suspend or hibernate at all

help please

thanks in advance

---

### Post by Toz on 2011-10-23
Try updating initramfs and see if that helps (sleep hooks are stored in there). Run the following command to update your initramfs:
```
sudo update-initramfs -u
```
...reboot.

If that still doesn't work, you can try overwriting your pm-suspend command. See option C in this post: [http://ubuntuforums.org/showpost.php?p=11347202&postcount=22]("http://ubuntuforums.org/showpost.php?p=11347202&postcount=22")

---

### Post by Burfee on 2011-10-24
Hi Toz,
I am having the same problem. Suspend used to work in 11.04, but now it doesn't. I made a clean install of 11.10. I followed all the steps in your link but no success. After following the A steps the system suspends but doesn't resume. After C it just displays a window to enter password as if it just resumed from suspend, but no suspend...

Any other advices?
I have a dell studio xps 1340.

Thanks

---

### Post by Toz on 2011-10-24
@Burfee, to start with, after a failed suspend attempt, can you post the contents of the **/var/log/pm-suspend.log** file along with the results of running the following command in a terminal window?
```
cat /var/log/syslog* | grep PM:
```

EDIT: Had a look on launchpad and found these 2 related bugs: 
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754711]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754711")
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754723]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754723")

Looks like there's known problems with suspending this machine on oneiric. Do you have an nvidia card? If so, have you enabled the proprietary drivers?

---

### Post by Burfee on 2011-10-25
Hi Toz,

Yes, i have an nvidia card (GeForce 9400M G, GeForce G210M) and i had quite a few problems with the drivers. When i enabled the proprietary drivers the system wouldn't boot, so i had to download the driver from the nvidia website and install that in recovery mode. It is ok from that point of view now.

I have followed the instructions from [this site]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug") (step 2) and the system suspends now, but it doesn't recover from suspend. Is the log still relevant now?

Thanks for help

P.S.: Rhetorical question: why don't they just make it work out of the box?
P.S.2: I ran the command you suggested after i manually tried to run suspend "pm-suspend" and it failed. here are the most recent outputs
> Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fec0000 - 000000008fecf000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fecf000 - 000000008fee5000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fee5000 - 00000000a0000000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000a0000000 - 00000000e0000000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff80000
Oct 24 22:11:28 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fff80000 - 0000000100000000
Oct 24 22:11:28 burfee kernel: [    0.157163] PM: Registering ACPI NVS region at 8fecf000 (90112 bytes)
Oct 24 22:11:28 burfee kernel: [    0.864334] PM: Hibernation image not present or could not be loaded.
Oct 24 23:42:56 burfee kernel: [ 5507.948193] PM: Syncing filesystems ... 
Oct 24 23:43:07 burfee kernel: [ 5508.432024] PM: Preparing system for mem sleep
Oct 24 23:43:07 burfee kernel: [ 5508.464062] PM: Entering mem sleep
Oct 24 23:43:07 burfee kernel: [ 5508.845978] PM: suspend of drv:sd dev:0:0:0:0 complete after 380.994 msecs
Oct 24 23:43:07 burfee kernel: [ 5508.845992] PM: suspend of drv:scsi dev:target0:0:0 complete after 380.963 msecs
Oct 24 23:43:07 burfee kernel: [ 5508.846003] PM: suspend of drv:scsi dev:host0 complete after 380.883 msecs
Oct 24 23:43:07 burfee kernel: [ 5508.860023] PM: suspend of drv:ahci dev:0000:00:0b.0 complete after 340.844 msecs
Oct 24 23:43:07 burfee kernel: [ 5508.932052] PM: suspend of drv:HDA Intel dev:0000:00:08.0 complete after 412.088 msecs
Oct 24 23:43:07 burfee kernel: [ 5508.932067] PM: suspend of drv: dev:pci0000:00 complete after 411.948 msecs
Oct 24 23:43:07 burfee kernel: [ 5508.932077] PM: suspend of devices complete after 467.516 msecs
Oct 24 23:43:07 burfee kernel: [ 5508.932079] PM: suspend devices took 0.468 seconds
Oct 24 23:43:07 burfee kernel: [ 5509.012377] PM: late suspend of devices complete after 80.294 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.012824] PM: Saving platform NVS memory
Oct 24 23:43:07 burfee kernel: [ 5509.116382] PM: Restoring platform NVS memory
Oct 24 23:43:07 burfee kernel: [ 5509.215577] PM: early resume of devices complete after 2.304 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368049] PM: resume of drv:hub dev:3-4:1.0 complete after 137.087 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368059] PM: resume of drv: dev:ep_00 complete after 137.070 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368093] PM: resume of drv: dev:ep_81 complete after 137.119 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368101] PM: resume of drv:usbhid dev:3-4.1:1.0 complete after 137.083 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368110] PM: resume of drv: dev:ep_00 complete after 137.066 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368117] PM: resume of drv:usb dev:3-4.2:1.0 complete after 137.043 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368126] PM: resume of drv: dev:ep_00 complete after 137.025 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368133] PM: resume of drv:btusb dev:3-4.3:1.0 complete after 137.004 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368146] PM: resume of drv:btusb dev:3-4.3:1.1 complete after 136.962 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368157] PM: resume of drv:usb dev:3-4.3:1.2 complete after 136.931 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368168] PM: resume of drv:usb dev:3-4.3:1.3 complete after 136.900 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368176] PM: resume of drv: dev:ep_00 complete after 136.893 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368182] PM: resume of drv: dev:ep_81 complete after 137.151 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368189] PM: resume of drv: dev:ep_81 complete after 137.102 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368195] PM: resume of drv: dev:ep_81 complete after 137.052 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368202] PM: resume of drv: dev:ep_82 complete after 137.046 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368209] PM: resume of drv: dev:ep_02 complete after 137.039 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368215] PM: resume of drv: dev:ep_83 complete after 137.018 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368222] PM: resume of drv: dev:ep_03 complete after 137.010 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368228] PM: resume of drv: dev:ep_84 complete after 136.989 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.368235] PM: resume of drv: dev:ep_04 complete after 136.981 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.440069] PM: resume of drv:hub dev:4-0:1.0 complete after 209.415 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.440078] PM: resume of drv: dev:ep_00 complete after 209.374 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.440097] PM: resume of drv: dev:ep_81 complete after 209.410 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.740228] PM: resume of drv:forcedeth dev:0000:00:0a.0 complete after 524.506 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.990785] PM: resume of drv:nvidia dev:0000:03:00.0 complete after 773.946 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.994072] PM: resume of drv: dev:ep_00 complete after 763.141 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.994080] PM: resume of drv:usbhid dev:3-2:1.0 complete after 763.183 msecs
Oct 24 23:43:07 burfee kernel: [ 5509.994097] PM: resume of drv: dev:ep_81 complete after 763.184 msecs
Oct 24 23:43:07 burfee kernel: [ 5510.364066] PM: resume of drv:uvcvideo dev:4-3:1.0 complete after 1132.755 msecs
Oct 24 23:43:07 burfee kernel: [ 5510.364070] PM: resume of drv:uvcvideo dev:4-3:1.1 complete after 1132.731 msecs
Oct 24 23:43:07 burfee kernel: [ 5510.364075] PM: resume of drv: dev:ep_81 complete after 1132.752 msecs
Oct 24 23:43:07 burfee kernel: [ 5510.364079] PM: resume of drv: dev:ep_00 complete after 1132.725 msecs
Oct 24 23:43:07 burfee kernel: [ 5511.144619] PM: resume of drv:sd dev:0:0:0:0 complete after 1913.808 msecs
Oct 24 23:43:07 burfee kernel: [ 5511.144640] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1153.184 msecs
Oct 24 23:43:07 burfee kernel: [ 5511.144810] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 1913.968 msecs
Oct 24 23:43:07 burfee kernel: [ 5511.146184] PM: resume of devices complete after 1930.576 msecs
Oct 24 23:43:07 burfee kernel: [ 5511.146374] PM: resume devices took 1.932 seconds
Oct 24 23:43:07 burfee kernel: [ 5511.146398] PM: Finishing wakeup.
Oct 24 23:52:12 burfee kernel: [ 6055.621790] PM: Marking nosave pages: 000000000009d000 - 0000000000100000
Oct 24 23:52:12 burfee kernel: [ 6055.621794] PM: Marking nosave pages: 000000008fec0000 - 0000000100000000
Oct 24 23:52:12 burfee kernel: [ 6055.622980] PM: Basic memory bitmaps created
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fec0000 - 000000008fecf000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fecf000 - 000000008fee5000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fee5000 - 00000000a0000000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000a0000000 - 00000000e0000000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff80000
Oct 24 23:53:54 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fff80000 - 0000000100000000
Oct 24 23:53:54 burfee kernel: [    0.157157] PM: Registering ACPI NVS region at 8fecf000 (90112 bytes)
Oct 24 23:53:54 burfee kernel: [    0.868221] PM: Hibernation image not present or could not be loaded.
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fec0000 - 000000008fecf000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fecf000 - 000000008fee5000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fee5000 - 00000000a0000000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000a0000000 - 00000000e0000000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff80000
Oct 25 00:02:59 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fff80000 - 0000000100000000
Oct 25 00:02:59 burfee kernel: [    0.157162] PM: Registering ACPI NVS region at 8fecf000 (90112 bytes)
Oct 25 00:02:59 burfee kernel: [    0.744340] PM: Hibernation image not present or could not be loaded.
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fec0000 - 000000008fecf000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fecf000 - 000000008fee5000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 000000008fee5000 - 00000000a0000000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000a0000000 - 00000000e0000000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff80000
Oct 25 06:58:05 burfee kernel: [    0.000000] PM: Registered nosave memory: 00000000fff80000 - 0000000100000000
Oct 25 06:58:05 burfee kernel: [    0.157159] PM: Registering ACPI NVS region at 8fecf000 (90112 bytes)
Oct 25 06:58:05 burfee kernel: [    0.860394] PM: Hibernation image not present or could not be loaded.

---

### Post by dFlyer on 2011-10-25
Can you post the results of free -tom. On my first install of 11.10 it didn't create a swap file and I couldn't suspend.

---

### Post by Burfee on 2011-10-25
Swap seems to exist:
>              total       used       free     shared    buffers     cached
Mem:          3708       2770        938          0        142       1096
Swap:         4099          0       4099
Total:        7808       2770       5038


---

### Post by dFlyer on 2011-10-25
Swap wasn't the problem, so sorry I can't help ya. Hopefully someone can.

---

### Post by Toz on 2011-10-25
@Burfee, according to that log file, suspend/resume worked. What exactly is happening when you resume? Blank screen? Have you tried adjusting your screen brightness in case it's turned down really low? Or going to tty1 (Ctrl+Alt+F1) and back to tty7 (Ctrl+Alt+F7) to see if video gets re-initialized?

Are you able to ssh into the computer from another computer to confirm that it is up and running?

---

### Post by Burfee on 2011-10-25
Hi,
I followed again the first steps in your post and now it works. Previously i got black screen and nothing worked, i could only power off the laptop...

Anyway, it's ok now. :D

Thank you very much for support.

---

### Post by curts on 2011-10-29
> **Toz said:**
> If that still doesn't work, you can try overwriting your pm-suspend command. See option C in this post: [http://ubuntuforums.org/showpost.php?p=11347202&postcount=22]("http://ubuntuforums.org/showpost.php?p=11347202&postcount=22")

I tried the first two options, but had no success.  Ubuntu doesn't actually suspend and eventually returns to the session unlock dialog box.  Here is the output of cat /var/log/syslog* | grep PM: on my PC:
```
Oct 29 12:29:14 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Oct 29 12:29:14 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Oct 29 12:29:14 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Oct 29 12:29:14 Panther2 kernel: [    0.068003] PM: Registering ACPI NVS region at 3fee0000 (12288 bytes)
Oct 29 12:29:14 Panther2 kernel: [    0.390434] PM: Hibernation image not present or could not be loaded.
Oct 29 12:30:52 Panther2 kernel: [  107.676060] PM: Syncing filesystems ... done.
Oct 29 12:30:52 Panther2 kernel: [  107.725049] PM: Preparing system for mem sleep
Oct 29 12:37:32 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Oct 29 12:37:32 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Oct 29 12:37:32 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Oct 29 12:37:32 Panther2 kernel: [    0.068003] PM: Registering ACPI NVS region at 3fee0000 (12288 bytes)
Oct 29 12:37:32 Panther2 kernel: [    0.386314] PM: Hibernation image not present or could not be loaded.
Oct 29 12:39:01 Panther2 kernel: [   98.665280] PM: Syncing filesystems ... done.
Oct 29 12:39:01 Panther2 kernel: [   98.745011] PM: Preparing system for mem sleep
Oct 29 10:43:43 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Oct 29 10:43:43 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Oct 29 10:43:43 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Oct 29 10:43:43 Panther2 kernel: [    0.068003] PM: Registering ACPI NVS region at 3fee0000 (12288 bytes)
Oct 29 10:43:43 Panther2 kernel: [    0.390448] PM: Hibernation image not present or could not be loaded.

```

If I'm reading the pm-suspend.log correctly, here are the entries from the last attempt using method #2:
```
Sat Oct 29 12:38:40 BST 2011: performing suspend
s2ram_do: Device or resource busy
switching from vt7 to vt1... succeeded
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
Sat Oct 29 12:39:01 BST 2011: Awake.
Sat Oct 29 12:39:01 BST 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
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
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sat Oct 29 12:39:04 BST 2011: Finished.

```

Using the command 'sudo pm-suspend' works with the current /etc/pm/config.d/defaults settings.

Any suggestions before I try method 3?

---

### Post by Toz on 2011-10-29
@curts, this looks interesting (and by interesting, I mean not right):
> s2ram_do: Device or resource busy

After a fresh reboot/restart, can you post back the results of the last suspend attempt from /var/log/pm-suspend.log after:

1. a suspend attempt from running suspend from the Unity's system pulldown menu.

2. a suspend attempt from running **sudo pm-suspend** from the command line

Lets see what the difference is.

---

### Post by curts on 2011-10-30
Here is the requested output from the two suspend attempts: system menu pulldown (not successful) followed by 'sudo pm-suspend' (succesful).

```
Initial commandline parameters: 
Sun Oct 30 17:28:45 GMT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Panther2 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xts                    12756  0 
gf128mul               14951  1 xts
des_generic            21415  0 
md4                    12595  0 
nls_utf8               12557  3 
cifs                  273898  4 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
autofs4                37024  5 
dm_crypt               23199  0 
snd_usb_audio         118064  1 
snd_hwdep              13668  1 snd_usb_audio
snd_usbmidi_lib        25371  1 snd_usb_audio
ppdev                  17113  0 
nvidia              11713772  44 
joydev                 17693  0 
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               93004  1 gspca_main
v4l2_compat_ioctl32    17083  1 videodev
psmouse                73882  0 
snd_via82xx            29735  2 
edac_core              53746  0 
serio_raw              13166  0 
edac_mce_amd           23709  0 
snd_mpu401_uart        14169  1 snd_via82xx
k8temp                 13057  0 
i2c_viapro             13153  0 
shpchp                 37345  0 
parport_pc             36962  1 
snd_ens1371            25748  2 
gameport               19693  3 snd_via82xx,snd_ens1371
snd_ac97_codec        134826  2 snd_via82xx,snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96755  4 snd_usb_audio,snd_via82xx,snd_ens1371,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  4 snd_usbmidi_lib,snd_mpu401_uart,snd_ens1371,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  22 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_via82xx,snd_mpu401_uart,snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_via82xx,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
vesafb                 13809  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
usb_storage            57901  1 
uas                    18027  0 
firewire_ohci          40722  0 
pata_via               13623  3 
r8169                  52788  0 
sata_promise           18401  5 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
floppy                 70365  0 
             total       used       free     shared    buffers     cached
Mem:       1021328     960460      60868          0      11084      97324
-/+ buffers/cache:     852052     169276
Swap:      2096476     649640    1446836

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Oct 30 17:28:52 GMT 2011: performing suspend
s2ram_do: Device or resource busy
switching from vt7 to vt1... failed
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
Sun Oct 30 17:29:23 GMT 2011: Awake.
Sun Oct 30 17:29:23 GMT 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
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
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Oct 30 17:29:31 GMT 2011: Finished.
Initial commandline parameters: 
Sun Oct 30 17:30:11 GMT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Panther2 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xts                    12756  0 
gf128mul               14951  1 xts
des_generic            21415  0 
md4                    12595  0 
nls_utf8               12557  3 
cifs                  273898  4 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
autofs4                37024  5 
dm_crypt               23199  0 
snd_usb_audio         118064  1 
snd_hwdep              13668  1 snd_usb_audio
snd_usbmidi_lib        25371  1 snd_usb_audio
ppdev                  17113  0 
nvidia              11713772  44 
joydev                 17693  0 
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               93004  1 gspca_main
v4l2_compat_ioctl32    17083  1 videodev
psmouse                73882  0 
snd_via82xx            29735  2 
edac_core              53746  0 
serio_raw              13166  0 
edac_mce_amd           23709  0 
snd_mpu401_uart        14169  1 snd_via82xx
k8temp                 13057  0 
i2c_viapro             13153  0 
shpchp                 37345  0 
parport_pc             36962  1 
snd_ens1371            25748  2 
gameport               19693  3 snd_via82xx,snd_ens1371
snd_ac97_codec        134826  2 snd_via82xx,snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96755  4 snd_usb_audio,snd_via82xx,snd_ens1371,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  4 snd_usbmidi_lib,snd_mpu401_uart,snd_ens1371,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  22 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_via82xx,snd_mpu401_uart,snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_via82xx,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
vesafb                 13809  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
usb_storage            57901  1 
uas                    18027  0 
firewire_ohci          40722  0 
pata_via               13623  3 
r8169                  52788  0 
sata_promise           18401  5 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
floppy                 70365  0 
             total       used       free     shared    buffers     cached
Mem:       1021328     956352      64976          0      15420      71840
-/+ buffers/cache:     869092     152236
Swap:      2096476     657620    1438856

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Oct 30 17:30:22 GMT 2011: performing suspend
switching from vt7 to vt1... succeeded
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
Sun Oct 30 17:30:48 GMT 2011: Awake.
Sun Oct 30 17:30:48 GMT 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
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
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Oct 30 17:31:03 GMT 2011: Finished.
```

---

### Post by Toz on 2011-10-30
According to the logs, the suspend/resume cycle worked for both attempts. However, I'm guessing that when you tried it from the unity menu, you didn't get a screen back? This may be why:
> s2ram_do: Device or resource busy
switching from vt7 to vt1... failed
What happens if you manually switch to the first vt and back (Ctrl+Alt+F1 followed by Ctrl+Alt+F7)?
Also, maybe there's more info in your syslog. Post back the results of:
```
cat /var/log/syslog* | grep PM:
```

---

### Post by curts on 2011-10-31
> **Toz said:**
> According to the logs, the suspend/resume cycle worked for both attempts. However, I'm guessing that when you tried it from the unity menu, you didn't get a screen back?

No, the first attempt using the system menu did not actually enter the suspend state.  That is the problem I'm trying to address.  The screen came back OK on both attempts.

> Also, maybe there's more info in your syslog. Post back the results of:
```
cat /var/log/syslog* | grep PM:
```

```
Oct 30 17:28:58 Panther2 kernel: [23189.526107] PM: Syncing filesystems ... done.
Oct 30 17:28:58 Panther2 kernel: [23189.591370] PM: Preparing system for mem sleep
Oct 30 17:30:47 Panther2 kernel: [23275.777027] PM: Syncing filesystems ... done.
Oct 30 17:30:47 Panther2 kernel: [23278.287016] PM: Preparing system for mem sleep
Oct 30 17:30:47 Panther2 kernel: [23283.484043] PM: Entering mem sleep
Oct 30 17:30:47 Panther2 kernel: [23283.918439] PM: suspend of drv:nvidia dev:0000:02:00.0 complete after 432.334 msecs
Oct 30 17:30:47 Panther2 kernel: [23283.918496] PM: suspend of drv:sd dev:0:0:0:0 complete after 432.604 msecs
Oct 30 17:30:47 Panther2 kernel: [23283.918599] PM: suspend of drv:pcieport dev:0000:00:02.0 complete after 407.521 msecs
Oct 30 17:30:47 Panther2 kernel: [23283.918623] PM: suspend of drv:uhci_hcd dev:0000:00:10.0 complete after 408.082 msecs
Oct 30 17:30:47 Panther2 kernel: [23283.918630] PM: suspend of drv:scsi dev:target0:0:0 complete after 432.682 msecs
Oct 30 17:30:47 Panther2 kernel: [23283.918641] PM: suspend of drv:scsi dev:host0 complete after 432.632 msecs
Oct 30 17:30:47 Panther2 kernel: [23283.918653] PM: suspend of drv:sata_promise dev:0000:00:07.0 complete after 407.613 msecs
Oct 30 17:30:47 Panther2 kernel: [23283.918661] PM: suspend of drv: dev:pci0000:00 complete after 407.496 msecs
Oct 30 17:30:47 Panther2 kernel: [23283.918666] PM: suspend of devices complete after 434.353 msecs
Oct 30 17:30:47 Panther2 kernel: [23283.918669] PM: suspend devices took 0.432 seconds
Oct 30 17:30:47 Panther2 kernel: [23284.012369] PM: late suspend of devices complete after 93.692 msecs
Oct 30 17:30:47 Panther2 kernel: [23284.156062] PM: Saving platform NVS memory
Oct 30 17:30:47 Panther2 kernel: [23284.156098] PM: Restoring platform NVS memory
Oct 30 17:30:47 Panther2 kernel: [23284.316500] PM: early resume of devices complete after 159.991 msecs
Oct 30 17:30:47 Panther2 kernel: [23284.428338] PM: resume of drv:VIA 82xx Audio dev:0000:00:11.5 complete after 110.518 msecs
Oct 30 17:30:47 Panther2 kernel: [23284.428352] PM: resume of drv: dev:platform complete after 111.667 msecs
Oct 30 17:30:47 Panther2 kernel: [23284.471040] PM: resume of drv:firewire_ohci dev:0000:00:0c.0 complete after 153.406 msecs
Oct 30 17:30:47 Panther2 kernel: [23284.496886] PM: resume of drv:ENS1371 dev:0000:00:09.0 complete after 179.265 msecs
Oct 30 17:30:47 Panther2 kernel: [23284.950092] PM: resume of drv:nvidia dev:0000:02:00.0 complete after 629.614 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.028327] PM: resume of drv:usb-storage dev:1-5:1.0 complete after 523.984 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.028335] PM: resume of drv: dev:ep_00 complete after 523.918 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.028342] PM: resume of drv:scsi dev:host7 complete after 523.983 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.028348] PM: resume of drv: dev:ep_81 complete after 523.959 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.028353] PM: resume of drv: dev:ep_02 complete after 523.950 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.028357] PM: resume of drv:scsi_host dev:host7 complete after 523.984 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.028362] PM: resume of drv:scsi dev:target7:0:0 complete after 523.929 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.028372] PM: resume of drv:sd dev:7:0:0:0 complete after 523.924 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.028377] PM: resume of drv:scsi_device dev:7:0:0:0 complete after 523.914 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052038] PM: resume of drv:hub dev:2-0:1.0 complete after 580.988 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052044] PM: resume of drv: dev:ep_00 complete after 551.380 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052059] PM: resume of drv:hub dev:3-0:1.0 complete after 551.385 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052064] PM: resume of drv: dev:ep_00 complete after 548.323 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052074] PM: resume of drv:hub dev:4-0:1.0 complete after 548.325 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052080] PM: resume of drv: dev:ep_00 complete after 548.325 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052085] PM: resume of drv:hub dev:5-0:1.0 complete after 548.321 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052091] PM: resume of drv: dev:ep_00 complete after 548.321 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052096] PM: resume of drv: dev:ep_81 complete after 555.204 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052100] PM: resume of drv: dev:ep_81 complete after 551.424 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052105] PM: resume of drv: dev:ep_81 complete after 548.352 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.052109] PM: resume of drv: dev:ep_81 complete after 548.343 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.264014] PM: resume of drv:sd dev:3:0:0:0 complete after 760.099 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.264020] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 760.082 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.528020] PM: resume of drv:hub dev:2-1:1.0 complete after 1024.152 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.528026] PM: resume of drv: dev:ep_00 complete after 1024.128 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.528037] PM: resume of drv: dev:ep_81 complete after 1024.154 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.599972] PM: resume of drv:usb dev:3-2:1.0 complete after 1096.004 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.599979] PM: resume of drv:usb dev:3-2:1.1 complete after 1095.941 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.599984] PM: resume of drv:usb dev:3-2:1.2 complete after 1095.931 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.599989] PM: resume of drv: dev:ep_00 complete after 1095.921 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.599994] PM: resume of drv: dev:ep_81 complete after 1096.012 msecs
Oct 30 17:30:47 Panther2 kernel: [23285.599998] PM: resume of drv: dev:ep_82 complete after 1096.003 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.124421] PM: resume of drv:usbhid dev:2-1.1:1.0 complete after 1620.306 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.124427] PM: resume of drv:usbhid dev:2-1.1:1.1 complete after 1620.284 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.124433] PM: resume of drv: dev:ep_00 complete after 1620.263 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.124438] PM: resume of drv: dev:ep_81 complete after 1620.309 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.124442] PM: resume of drv: dev:ep_82 complete after 1620.286 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.671435] PM: resume of drv:usbhid dev:2-1.2:1.0 complete after 2167.235 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.671441] PM: resume of drv: dev:ep_00 complete after 2167.213 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.671446] PM: resume of drv: dev:ep_81 complete after 2167.233 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.840442] PM: resume of drv:usbhid dev:2-1.4:1.0 complete after 2336.184 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.840449] PM: resume of drv: dev:ep_00 complete after 2336.144 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.840454] PM: resume of drv: dev:ep_81 complete after 2336.180 msecs
Oct 30 17:30:47 Panther2 kernel: [23286.840459] PM: resume of drv: dev:ep_02 complete after 2336.171 msecs
Oct 30 17:30:47 Panther2 kernel: [23287.504089] PM: resume of drv:floppy dev:floppy.0 complete after 3001.862 msecs
Oct 30 17:30:47 Panther2 kernel: [23289.689225] PM: resume of drv:sd dev:0:0:0:0 complete after 5185.428 msecs
Oct 30 17:30:47 Panther2 kernel: [23289.689230] PM: Device 0:0:0:0 failed to resume async: error 134217730
Oct 30 17:30:47 Panther2 kernel: [23289.689235] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 5185.411 msecs
Oct 30 17:30:47 Panther2 kernel: [23289.689240] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2185.079 msecs
Oct 30 17:30:47 Panther2 kernel: [23289.689435] PM: resume of devices complete after 5372.828 msecs
Oct 30 17:30:47 Panther2 kernel: [23290.780098] PM: resume devices took 6.464 seconds
Oct 30 17:30:47 Panther2 kernel: [23290.780157] PM: Finishing wakeup.
```

---

### Post by regiss on 2011-10-31
Same issue for me Ubuntu upgraded from 11.04 11.10 x64 laptop Thinkpad T400
In my case I think it's related to bluetooth. Suspend from Unity usually fails after bluetooth iPhone tethering. Symptoms are same as post above. When select suspend in unity it looks like everything gonna work but then login screen comes up.

---

### Post by Toz on 2011-10-31
> **curts said:**
> No, the first attempt using the system menu did not actually enter the suspend state.  That is the problem I'm trying to address.  The screen came back OK on both attempts.

Interesting. Here is a summary of your log file.

First attempt (system pulldown menu)
```

Sun Oct 30 17:28:45 GMT 2011: Running hooks for suspend.
...
Sun Oct 30 17:28:52 GMT 2011: performing suspend
s2ram_do: Device or resource busy
switching from vt7 to vt1... failed
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
...
Sun Oct 30 17:29:23 GMT 2011: Awake.
...
Sun Oct 30 17:29:31 GMT 2011: Finished.

```
Second attempt (sudo pm-suspend)
```

Sun Oct 30 17:30:11 GMT 2011: Running hooks for suspend.
...
un Oct 30 17:30:22 GMT 2011: performing suspend
switching from vt7 to vt1... succeeded
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
...
Sun Oct 30 17:30:48 GMT 2011: Awake.
...
Sun Oct 30 17:31:03 GMT 2011: Finished.

```
So even if it looks from the log files that it is suspending and resuming, the error message is actually indicating that it never suspended. In fact, it actually goes through all of the resume processes.

Can you try suspending with the following command, and post back if it works:
```
dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

---

### Post by Toz on 2011-10-31
> **regiss said:**
> Same issue for me Ubuntu upgraded from 11.04 11.10 x64 laptop Thinkpad T400
In my case I think it's related to bluetooth. Suspend from Unity usually fails after bluetooth iPhone tethering. Symptoms are same as post above. When select suspend in unity it looks like everything gonna work but then login screen comes up.

If bluetooth is preventing suspend, try forcing an unload of the module before suspend and reload afterwards. This is done by editing (or creating if it doesn't exist) the file **/etc/pm/config.d/modules** with the following content:
```
SUSPEND_MODULES="bluetooth"
```

---

### Post by regiss on 2011-10-31
> **Toz said:**
> If bluetooth is preventing suspend, try forcing an unload of the module before suspend and reload afterwards. This is done by editing (or creating if it doesn't exist) the file **/etc/pm/config.d/modules** with the following content:
```
SUSPEND_MODULES="bluetooth"
```

Thx will let you know if that fixed my problem

---

### Post by curts on 2011-11-01
> **Toz said:**
> Can you try suspending with the following command, and post back if it works:
```
dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

No, it didn't work.
```
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

```
Initial commandline parameters: 
Tue Nov  1 20:48:02 GMT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Panther2 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xts                    12756  0 
gf128mul               14951  1 xts
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
des_generic            21415  0 
md4                    12595  0 
nls_utf8               12557  3 
cifs                  273898  4 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
autofs4                37024  5 
dm_crypt               23199  0 
snd_usb_audio         118064  1 
snd_hwdep              13668  1 snd_usb_audio
snd_usbmidi_lib        25371  1 snd_usb_audio
ppdev                  17113  0 
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               93004  1 gspca_main
nvidia              11713772  40 
v4l2_compat_ioctl32    17083  1 videodev
joydev                 17693  0 
snd_via82xx            29735  2 
psmouse                73882  0 
serio_raw              13166  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
k8temp                 13057  0 
snd_mpu401_uart        14169  1 snd_via82xx
i2c_viapro             13153  0 
parport_pc             36962  1 
shpchp                 37345  0 
snd_ens1371            25748  2 
gameport               19693  3 snd_via82xx,snd_ens1371
snd_ac97_codec        134826  2 snd_via82xx,snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96755  4 snd_usb_audio,snd_via82xx,snd_ens1371,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  4 snd_usbmidi_lib,snd_mpu401_uart,snd_ens1371,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  22 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_via82xx,snd_mpu401_uart,snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_via82xx,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
vesafb                 13809  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
sata_promise           18401  5 
pata_via               13623  3 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  52788  0 
floppy                 70365  0 
             total       used       free     shared    buffers     cached
Mem:       1021328     949416      71912          0      25672     130980
-/+ buffers/cache:     792764     228564
Swap:      2096476     557436    1539040

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Nov  1 20:48:07 GMT 2011: performing suspend
s2ram_do: Device or resource busy
switching from vt7 to vt1... succeeded
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
Tue Nov  1 20:48:30 GMT 2011: Awake.
Tue Nov  1 20:48:30 GMT 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
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
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Nov  1 20:48:34 GMT 2011: Finished.
```

---

### Post by Toz on 2011-11-02
Hmmm - that command should of worked. Can you try that one more time then post back the contents of your ~/.xsession-errors file?

And, can you try suspending one more time from the unity menu and then post back the results of:
```
cat /var/log/syslog* | grep PM:
```
and the contents of /var/log/pm-suspend.log on more time?

---

### Post by curts on 2011-11-04
Will do, Toz, but it will be more than a week before I can work on this again.

Cheers,

Curt

---

### Post by Eric12345 on 2011-11-12
Hi,
I have the same problem. My laptop can suspend but doesn't restart since I upgraded my Ubuntu to Oneiric. 

```
ed@compaq:~$ sudo s2ram
[sudo] password for ed: 
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Hewlett-Packard"
    sys_product  = "Compaq Presario CQ60 Notebook PC"
    sys_version  = "F.38"
    bios_version = "F.38"

```I have tried everything in this thread but none worked.

```

ed@compaq:~$ cat /var/log/syslog* | grep PM:
Nov 12 08:51:25 compaq kernel: [ 1750.761616] PM: Syncing filesystems ... done.
Nov 12 08:51:25 compaq kernel: [ 1750.793893] PM: Preparing system for mem sleep
Nov 12 11:02:12 compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov 12 11:02:12 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
Nov 12 11:02:12 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
Nov 12 11:02:12 compaq kernel: [    0.072003] PM: Registering ACPI NVS region at 6fee5000 (4096 bytes)
Nov 12 11:02:12 compaq kernel: [    0.927019] PM: Hibernation image not present or could not be loaded.
Nov 12 12:33:09 compaq kernel: [ 5511.583242] PM: Syncing filesystems ... done.
Nov 12 12:33:09 compaq kernel: [ 5511.721067] PM: Preparing system for mem sleep
Nov 12 12:37:05 compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov 12 12:37:05 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
Nov 12 12:37:05 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
Nov 12 12:37:05 compaq kernel: [    0.072003] PM: Registering ACPI NVS region at 6fee5000 (4096 bytes)
Nov 12 12:37:05 compaq kernel: [    0.650501] PM: Hibernation image not present or could not be loaded.
Nov 11 09:28:24 compaq kernel: [36702.398559] PM: Syncing filesystems ... done.
Nov 11 09:28:24 compaq kernel: [36702.611216] PM: Preparing system for mem sleep
Nov 11 09:45:28 compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov 11 09:45:28 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
Nov 11 09:45:28 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
Nov 11 09:45:28 compaq kernel: [    0.072003] PM: Registering ACPI NVS region at 6fee5000 (4096 bytes)
Nov 11 09:45:28 compaq kernel: [    0.650478] PM: Hibernation image not present or could not be loaded.
Nov 11 13:05:32 compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov 11 13:05:32 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
Nov 11 13:05:32 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
Nov 11 13:05:32 compaq kernel: [    0.072003] PM: Registering ACPI NVS region at 6fee5000 (4096 bytes)
Nov 11 13:05:32 compaq kernel: [    0.838310] PM: Hibernation image not present or could not be loaded.
Nov 11 15:58:51 compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov 11 15:58:51 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
Nov 11 15:58:51 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
Nov 11 15:58:51 compaq kernel: [    0.072003] PM: Registering ACPI NVS region at 6fee5000 (4096 bytes)
Nov 11 15:58:51 compaq kernel: [    0.646440] PM: Hibernation image not present or could not be loaded.
Nov 11 16:17:11 compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov 11 16:17:11 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
Nov 11 16:17:11 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
Nov 11 16:17:11 compaq kernel: [    0.072003] PM: Registering ACPI NVS region at 6fee5000 (4096 bytes)
Nov 11 16:17:11 compaq kernel: [    0.698310] PM: Hibernation image not present or could not be loaded.
Nov 12 08:23:01 compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Nov 12 08:23:01 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
Nov 12 08:23:01 compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
Nov 12 08:23:01 compaq kernel: [    0.072003] PM: Registering ACPI NVS region at 6fee5000 (4096 bytes)
Nov 12 08:23:02 compaq kernel: [    0.775005] PM: Hibernation image not present or could not be loaded.

```I have also a Compaq CQ62. I had no suspend problem with it after Oneiric upgrade.

Help !

Edit : Nvidia inside my CQ60-305EF (GeForce 8200 M G), ATI on the CQ62.

- CQ60-305EF (KO) specs [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01705413&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=3938343&query=Compaq%20Presario%20CQ60-305EF&submit=&tool=](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01705413&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=3938343&query=Compaq%20Presario%20CQ60-305EF&submit=&tool=)
- CQ62-A36SF (OK) specs [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02215924&lc=en&cc=us&destPage=document&dlc=en&jumpid=reg_r1002_frfr&product=4212496](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02215924&lc=en&cc=us&destPage=document&dlc=en&jumpid=reg_r1002_frfr&product=4212496)

---

### Post by Toz on 2011-11-12
@Eric12345,

Can you post back the contents of **/var/log/pm-suspend.log**? 

If you want to try s2ram, since its not recognized, you have to try with:
```
s2ram -f
```
(the -f to force the command)
Since its being forced, you might also need to add more parameters. See: [http://tr.opensuse.org/S2ram#My_machine_is_not_in_the_whitelist.2C_what_can_i_do.3F]("http://tr.opensuse.org/S2ram#My_machine_is_not_in_the_whitelist.2C_what_can_i_do.3F")

And also, it might be helpful if you, from a command prompt, run these commands (it will generate a more complete log file):
```
sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
sudo pm-suspend
```
...and when you recover your system (assuming suspend didn't work), post back the much bigger **/var/log/pm-suspend.log** file.

EDIT: Have you installed the proprietary video drivers?

---

### Post by Eric12345 on 2011-11-12
I've just received a nvidia upgrade : package nvidia-graphics-drivers-updates (285.05.09-0ubuntu0.1) and it seems to solve the problem (2 suspend tests were OK). I hope it will last ! :)
Otherwise, I'll publish the full-debug pm log here...

---

### Post by DMJ on 2011-11-13
I'm having suspend problems as well since I upgraded to 11.10. It worked flawlessly in 11.04, which was a surprise. The only hitch was my SSHFS mount not disconnecting, which caused Nautilus to hang when the Machine resumed. I fixed that with a script in /etc/networks/if-down.d. My NFS mount seemed to take care of itself.

 The log file shows that NetworkManager fails in bringing the IFs up or down, whether the suspend works or not. It always reconnects anyways, so that doesn't seem to be a problem. That's the only error message. 

I figured that it has something to do with my NFS and SSHFS mounts. Neither disconnect on suspend since upgrading to 11.10. I modified my script and moved it to /etc/network/if-post-down.d/, and now it works sporadically. It's clear that the mounts are causing the problem. Suspend always failed without the script, when either of the two mounts was connected, and never failed when they were disconnected.

So why would the shares failing to umount cause suspend to fail, and why did it work in Natty and not in Oneiric? The other difference is that I had Natty 32-bit installed, and changed to 64-bit with Oneiric. I also installed with the alternate CD this time on a LUKS volume. The encryption could play a role.

System:
Aspire 1410 with Intel Graphics
Ubuntu 11.10 64 bit

---

### Post by Eric12345 on 2011-11-13
> **Toz said:**
> @Eric12345,

Can you post back the contents of **/var/log/pm-suspend.log**? 

If you want to try s2ram, since its not recognized, you have to try with:
```
s2ram -f
```(the -f to force the command)
Since its being forced, you might also need to add more parameters. See: [http://tr.opensuse.org/S2ram#My_machine_is_not_in_the_whitelist.2C_what_can_i_do.3F](http://tr.opensuse.org/S2ram#My_machine_is_not_in_the_whitelist.2C_what_can_i_do.3F)

And also, it might be helpful if you, from a command prompt, run these commands (it will generate a more complete log file):
```
sudo mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
sudo pm-suspend
```...and when you recover your system (assuming suspend didn't work), post back the much bigger **/var/log/pm-suspend.log** file.

EDIT: Have you installed the proprietary video drivers?

It doesn't work anymore. Same problem occurs. :(

I tried NVidia proprietary drivers and Nouveau opensource ones, I get the same bugs...

I tried s2ram -f, without success. 

Here is my debug mode **/var/log/pm-suspend.log** : [http://pastebin.com/4rcCD141](http://pastebin.com/4rcCD141)

EDIT : It works now. I use s2ram -f -p (doesn't work with -f -p -s or with -f -p -s -v)

---

### Post by Toz on 2011-11-13
> **Eric12345 said:**
> It doesn't work anymore. Same problem occurs. :(

I tried NVidia proprietary drivers and Nouveau opensource ones, I get the same bugs...

I tried s2ram -f, without success. 

Here is my debug mode **/var/log/pm-suspend.log** : [http://pastebin.com/4rcCD141](http://pastebin.com/4rcCD141)

EDIT : It works now. I use s2ram -f -p (doesn't work with -f -p -s or with -f -p -s -v)

If s2ram -f -p works, try:
```
sudo pm-suspend --quirk-vbe-post
```

---

### Post by Toz on 2011-11-13
> **DMJ said:**
> I'm having suspend problems as well since I upgraded to 11.10. It worked flawlessly in 11.04, which was a surprise. The only hitch was my SSHFS mount not disconnecting, which caused Nautilus to hang when the Machine resumed. I fixed that with a script in /etc/networks/if-down.d. My NFS mount seemed to take care of itself.

 The log file shows that NetworkManager fails in bringing the IFs up or down, whether the suspend works or not. It always reconnects anyways, so that doesn't seem to be a problem. That's the only error message. 

I figured that it has something to do with my NFS and SSHFS mounts. Neither disconnect on suspend since upgrading to 11.10. I modified my script and moved it to /etc/network/if-post-down.d/, and now it works sporadically. It's clear that the mounts are causing the problem. Suspend always failed without the script, when either of the two mounts was connected, and never failed when they were disconnected.

So why would the shares failing to umount cause suspend to fail, and why did it work in Natty and not in Oneiric? The other difference is that I had Natty 32-bit installed, and changed to 64-bit with Oneiric. I also installed with the alternate CD this time on a LUKS volume. The encryption could play a role.

System:
Aspire 1410 with Intel Graphics
Ubuntu 11.10 64 bit

How do you mount/umount your sshfs share? 

How about putting your script in /etc/pm/sleep.d? Have a look at some of the files in /usr/lib/pm-utils/sleep.d for a template (case statement with options for suspend and thaw). Assuming your script umounts and remounts the sshfs share, it might work from there.

Have a look at: [https://bbs.archlinux.org/viewtopic.php?id=94725]("https://bbs.archlinux.org/viewtopic.php?id=94725").

---

### Post by DMJ on 2011-11-14
> **Toz said:**
> How do you mount/umount your sshfs share? 

How about putting your script in /etc/pm/sleep.d? Have a look at some of the files in /usr/lib/pm-utils/sleep.d for a template (case statement with options for suspend and thaw). Assuming your script umounts and remounts the sshfs share, it might work from there.

Have a look at: [https://bbs.archlinux.org/viewtopic.php?id=94725]("https://bbs.archlinux.org/viewtopic.php?id=94725").

Thanks for the reply. I tried putting it in /etc/pm/sleep.d. The script makes the computer hang in the process of suspending. I had a mouse cursor and blank screen. I had to use REISUB to reboot. 

The script does a lazy umount of all SSHFS and NFS shares whenever the IF goes down. This prevents the mount being stuck in limbo after reconnect. In Natty the mounts didn't effect resume/suspend, but resume/suspend did effect them. Now something has changed.

Because the script now runs after the IF goes down rather than before, I'm guessing it doesn't haven enough time to do its business before the machine suspends. Scripts in /etc/network/if-down.d no longer run. It seems like Oneiric tries to umount remote shares on resume, but is failing to do so. But there's nothing in the suspend log file. Clearly, unmounting remote shares when the network connection is lost should be built into Ubuntu. I'll post this problem on Launchpad. Here's the script:

[INDENT]#!/bin/bash

# scans /etc/mtab for sshfs and nfs mounts, and umounts them when network IF is down
# save file as /etc/network/if-post-down.d/umountnetfs
# it may also be saved as /etc/network/if-down.d/umountnetfs, but this seems to have
# stopped working in Ubuntu 11.10. It shouldn't hurt to put it in both dirs.
# Source: [http://ubuntuforums.org/archive/index.php/t-430312.html](http://ubuntuforums.org/archive/index.php/t-430312.html)

# Not for loopback!
[ "$IFACE" != "lo" ] || exit 0

# comment this for testing
exec 1>/dev/null # squelch output for non-interactive

# umount all sshfs and nfs mounts
mounted=`grep 'fuse.sshfs\|sshfs#\|nfs\|nfs4' /etc/mtab | awk '{ print $2 }'`
[ -n "$mounted" ] && { for mount in $mounted; do umount -l $mount; done; }
[/INDENT]

---

### Post by Burfee on 2011-11-16
Hi again... the things i tried in the first posts seem to have solved the problem partially. When i say partially i mean that about 40% of the times i try to suspend my laptop hangs and i have to turn it off using the power button. Nothing works, no tty switching, nothing.

```
cat /var/log/syslog* | grep PM
``` doesn't contain anything regarding the latest fail which just happened:

```
other successful things...
Nov 15 06:51:07 burfee kernel: [23451.497106] PM: resume of drv: dev:ep_04 complete after 1670.003 msecs
Nov 15 06:51:07 burfee kernel: [23451.497109] PM: resume of drv: dev:ep_82 complete after 1670.105 msecs
Nov 15 06:51:07 burfee kernel: [23451.497123] PM: resume of drv: dev:ep_03 complete after 1670.062 msecs
Nov 15 06:51:07 burfee kernel: [23451.497126] PM: resume of drv: dev:ep_02 complete after 1670.105 msecs
Nov 15 06:51:07 burfee kernel: [23451.497135] PM: resume of drv: dev:ep_83 complete after 1670.083 msecs
Nov 15 06:51:07 burfee kernel: [23451.681064] PM: resume of drv: dev:ep_00 complete after 1854.117 msecs
Nov 15 06:51:07 burfee kernel: [23451.681070] PM: resume of drv:usb dev:3-4.2:1.0 complete after 1854.155 msecs
Nov 15 06:51:07 burfee kernel: [23451.681099] PM: resume of drv: dev:ep_81 complete after 1854.168 msecs
Nov 15 06:51:07 burfee kernel: [23451.747161] PM: resume of drv:sd dev:0:0:0:0 complete after 1920.535 msecs
Nov 15 06:51:07 burfee kernel: [23451.747181] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1161.709 msecs
Nov 15 06:51:07 burfee kernel: [23451.747245] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 1920.582 msecs
Nov 15 06:51:07 burfee kernel: [23451.850075] PM: resume of drv: dev:ep_00 complete after 2023.189 msecs
Nov 15 06:51:07 burfee kernel: [23451.850082] PM: resume of drv:usbhid dev:3-4.1:1.0 complete after 2023.227 msecs
Nov 15 06:51:07 burfee kernel: [23451.850114] PM: resume of drv:generic-usb dev:0003:413C:8157.0002 complete after 102.870 msecs
Nov 15 06:51:07 burfee kernel: [23451.851671] PM: resume of drv: dev:ep_81 complete after 2024.802 msecs
Nov 15 06:51:07 burfee kernel: [23451.851684] PM: resume of devices complete after 2040.065 msecs
Nov 15 06:51:07 burfee kernel: [23451.851857] PM: resume devices took 2.040 seconds
Nov 15 06:51:07 burfee kernel: [23451.851884] PM: Finishing wakeup.


```

---

### Post by curts on 2011-12-02
OK, I'm back from my travels.  Thanks for looking at this Toz.  I installed the available updates before executing these two tests.  Hope you find something!

> **Toz said:**
> Hmmm - that command should of worked. Can you try that one more time then post back the contents of your ~/.xsession-errors file?
```
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/curts/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading modmap: /home/curts/.Xmodmap
xmodmap:  /home/curts/.Xmodmap:1:  bad keysym name 'M1' in keysym list
xmodmap:  /home/curts/.Xmodmap:2:  bad keysym name 'M2' in keysym list
xmodmap:  /home/curts/.Xmodmap:3:  bad keysym name 'M3' in keysym list
xmodmap:  /home/curts/.Xmodmap:4:  bad keysym name 'MR' in keysym list
xmodmap:  /home/curts/.Xmodmap:5:  bad keysym name 'G1' in keysym list
xmodmap:  /home/curts/.Xmodmap:6:  bad keysym name 'G2' in keysym list
xmodmap:  /home/curts/.Xmodmap:7:  bad keysym name 'G3' in keysym list
xmodmap:  /home/curts/.Xmodmap:8:  bad keysym name 'G4' in keysym list
xmodmap:  /home/curts/.Xmodmap:9:  bad keysym name 'G5' in keysym list
xmodmap:  /home/curts/.Xmodmap:10:  bad keysym name 'G6' in keysym list
xmodmap:  /home/curts/.Xmodmap:11:  bad keysym name 'G7' in keysym list
xmodmap:  /home/curts/.Xmodmap:12:  bad keysym name 'G8' in keysym list
xmodmap:  /home/curts/.Xmodmap:13:  bad keysym name 'G9' in keysym list
xmodmap:  /home/curts/.Xmodmap:14:  bad keysym name 'G10' in keysym list
xmodmap:  /home/curts/.Xmodmap:15:  bad keysym name 'G11' in keysym list
xmodmap:  /home/curts/.Xmodmap:16:  bad keysym name 'G12' in keysym list
xmodmap:  /home/curts/.Xmodmap:17:  bad keysym name 'G13' in keysym list
xmodmap:  /home/curts/.Xmodmap:18:  bad keysym name 'G14' in keysym list
xmodmap:  /home/curts/.Xmodmap:19:  bad keysym name 'G15' in keysym list
xmodmap:  /home/curts/.Xmodmap:20:  bad keysym name 'G16' in keysym list
xmodmap:  /home/curts/.Xmodmap:21:  bad keysym name 'G17' in keysym list
xmodmap:  /home/curts/.Xmodmap:22:  bad keysym name 'G18' in keysym list
xmodmap:  22 errors encountered, aborting.
Loading X session script /etc/X11/Xsession.d/00_handle_guest_session
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
gnome-session[15577]: WARNING: Could not parse desktop file /home/curts/.config/autostart/padevchooser.desktop: No such file or directory
gnome-session[15577]: WARNING: could not read /home/curts/.config/autostart/padevchooser.desktop
GNOME_KEYRING_CONTROL=/tmp/keyring-jDBS26
GNOME_KEYRING_CONTROL=/tmp/keyring-jDBS26
GPG_AGENT_INFO=/tmp/keyring-jDBS26/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-jDBS26/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-jDBS26
GPG_AGENT_INFO=/tmp/keyring-jDBS26/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-jDBS26

(gnome-settings-daemon:15651): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...yes
[LOG]: Moving Internal Files
[LOG]: Copying subdirectory from /home/curts/.compiz/session to /home/curts/.compiz-1/session
[LOG]: Copied file /home/curts/.compiz/session/10fe594f907c122cd131882477016529000000020290049 to /home/curts/.compiz-1/session/10fe594f907c122cd131882477016529000000020290049
[LOG]: Successfully moved internal files
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
xmodmap:  /home/curts/.Xmodmap:1:  bad keysym name 'M1' in keysym list
xmodmap:  /home/curts/.Xmodmap:2:  bad keysym name 'M2' in keysym list
xmodmap:  /home/curts/.Xmodmap:3:  bad keysym name 'M3' in keysym list
xmodmap:  /home/curts/.Xmodmap:4:  bad keysym name 'MR' in keysym list
xmodmap:  /home/curts/.Xmodmap:5:  bad keysym name 'G1' in keysym list
xmodmap:  /home/curts/.Xmodmap:6:  bad keysym name 'G2' in keysym list
xmodmap:  /home/curts/.Xmodmap:7:  bad keysym name 'G3' in keysym list
xmodmap:  /home/curts/.Xmodmap:8:  bad keysym name 'G4' in keysym list
xmodmap:  /home/curts/.Xmodmap:9:  bad keysym name 'G5' in keysym list
xmodmap:  /home/curts/.Xmodmap:10:  bad keysym name 'G6' in keysym list
xmodmap:  /home/curts/.Xmodmap:11:  bad keysym name 'G7' in keysym list
xmodmap:  /home/curts/.Xmodmap:12:  bad keysym name 'G8' in keysym list
xmodmap:  /home/curts/.Xmodmap:13:  bad keysym name 'G9' in keysym list
xmodmap:  /home/curts/.Xmodmap:14:  bad keysym name 'G10' in keysym list
xmodmap:  /home/curts/.Xmodmap:15:  bad keysym name 'G11' in keysym list
xmodmap:  /home/curts/.Xmodmap:16:  bad keysym name 'G12' in keysym list
xmodmap:  /home/curts/.Xmodmap:17:  bad keysym name 'G13' in keysym list
xmodmap:  /home/curts/.Xmodmap:18:  bad keysym name 'G14' in keysym list
xmodmap:  /home/curts/.Xmodmap:19:  bad keysym name 'G15' in keysym list
xmodmap:  /home/curts/.Xmodmap:20:  bad keysym name 'G16' in keysym list
xmodmap:  /home/curts/.Xmodmap:21:  bad keysym name 'G17' in keysym list
xmodmap:  /home/curts/.Xmodmap:22:  bad keysym name 'G18' in keysym list
xmodmap:  22 errors encountered, aborting.
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Starting xflux...
/usr/share/indicator-multiload/preferences.ui
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
** (gnome-fallback-mount-helper:15712): DEBUG: Starting automounting manager
** Message: applet now removed from the notification area
[2J[0;0f
--------
Welcome to xflux (f.lux for X)
This will only work if you're running X on console.

Your latitude is 52.1

Your night-time color temperature is 3400
It's night time. Your screen is changing now.
Going to background: 'kill 15731' to turn off.

Initializing nautilus-gdu extension
** Message: using fallback from indicator to GtkStatusIcon
** (gnome-fallback-mount-helper:15712): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session50
** (gnome-fallback-mount-helper:15712): DEBUG: ScreenSaver name appeared
Initializing nautilus-dropbox 0.7.1
** (gnome-fallback-mount-helper:15712): DEBUG: ScreenSaver proxy ready
** (gnome-fallback-mount-helper:15712): DEBUG: ConsoleKit session is active 1
** (gnome-fallback-mount-helper:15712): DEBUG: Screensaver GetActive() returned 0
** (nautilus:15700): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Starting Dropbox...** (process:15756): DEBUG: Telepathy Indicator started
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing place options...done
Initializing wall options...done
Initializing scale options...done
Initializing snap options...done
Initializing vpswitch options...done
compiz (core) - Error: Plugin 'text' not loaded.

Initializing thumbnail options...done
Initializing gnomecompat options...done
Initializing move options...done
Initializing animation options...done
Initializing resize options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
I/O warning : failed to load external entity "/home/curts/.compiz/session/10fe594f907c122cd131882477016529000000020290049"
Initializing session options...done
Initializing grid options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing ezoom options...done
CachingBackend: Loading instances from cacheCachingBackend: Loading instances from cache

CachingBackend: Loading <Countdown1>
opacity='0.8'
scale='0.573333333333'
is_sticky='True'
text='LEAVE FOR ATLANTA'
allow_option_override='False'
is_widget='True'
keep_above='False'
lock_position='True'
is_dragged='False'
keep_below='False'
y='199'
x='1229'
skip_taskbar='True'
to_date='2011-11-19 07:00:00'
CachingBackend: Loading instances from cache
CachingBackend: Loading <ClearWeather1>
opacity='1.0'
scale='1.6'
theme_name='default'
ZIP='OX26'
is_sticky='True'
show_error_message='0'
is_widget='True'
keep_above='True'
lock_position='True'
is_dragged='False'
keep_below='True'
y='31'
x='1189'
skip_taskbar='True'
opacity='1.0'
scale='0.4'
is_sticky='True'
is_widget='True'
keep_above='False'
lock_position='False'
color_front='0.435294117647,0.725490196078,1.0,0.899992370489'
keep_below='True'
y='26'
x='1105'
skip_taskbar='True'
color_text='0.435294117647,0.725490196078,1.0,1.0'
sensor='Core0 Temp:30.0'
is_dragged='False'
CachingBackend: Loading <RingSensors2>
scale='0.2'
is_sticky='True'
is_widget='False'
keep_above='True'
lock_position='True'
is_dragged='False'
keep_below='False'
y='38'
x='1064'
skip_taskbar='True'
color_front='0.985046158541,0.0,0.0,0.899992370489'
sensor='RAM'
show_text='False'
color_text='0.975661860075,0.04046692607,0.04046692607,1.0'
CachingBackend: Loading <RingSensors3>
scale='0.3'
theme_name='default'
is_sticky='True'
is_widget='False'
draw_buttons='True'
keep_above='True'
lock_position='True'
is_dragged='False'
keep_below='False'
y='28'
x='1053'
skip_taskbar='True'
sensor='SWAP'
lo
eth0
0
CachingBackend: Loading instances from cache
CachingBackend: Loading <Netmonitor1>
mini='True'
theme_name='Transparent'
download_total='59590'
is_widget='True'
height='60'
is_dragged='False'
scale='0.957446808511'
is_sticky='True'
keep_above='False'
lock_position='True'
draw_buttons='True'
show_frame='False'
opacity='0.8'
text_color='1.00000,1.00000,1.00000,1.00000'
keep_below='False'
dev='eth0'
upload_total='13081'
showDevice='True'
y='128'
x='989'
skip_taskbar='True'
color_text='1.0,1.0,1.0,0.6'
daemon already started
Error in screenlets.session.connect_daemon: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/share/screenlets-manager/screenlets-daemon.py exited with status 1
Error in screenlets.session.connect_daemon: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/share/screenlets-manager/screenlets-daemon.py exited with status 1
Error in screenlets.session.connect_daemon: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/share/screenlets-manager/screenlets-daemon.py exited with status 1
Error in screenlets.session.connect_daemon: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/share/screenlets-manager/screenlets-daemon.py exited with status 1
Found a running session of Countdown, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.Countdown was not provided by any .service files
Found a running session of Netmonitor, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.Netmonitor was not provided by any .service files
Found a running session of ClearWeather, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.ClearWeather was not provided by any .service files
Found a running session of RingSensors, adding new instance by service.
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.RingSensors was not provided by any .service files
Screenlet has already been added to /tmp/screenlets/screenlets.curts.running
Loading instances in: /home/curts/.config/screenlets/Netmonitor/default/
Loaded config from: Netmonitor1.ini
Screenlet has already been added to /tmp/screenlets/screenlets.curts.running
Loading instances in: /home/curts/.config/screenlets/ClearWeather/default/
Loaded config from: ClearWeather1.ini
Screenlet has already been added to /tmp/screenlets/screenlets.curts.running
Loading instances in: /home/curts/.config/screenlets/RingSensors/default/
Loaded config from: RingSensors1.ini
Screenlet has already been added to /tmp/screenlets/screenlets.curts.running
Loading instances in: /home/curts/.config/screenlets/Countdown/default/
Loaded config from: Countdown1.ini
Theme set to: 'ModernBlack'
Theme set to: 'default'
Theme set to: 'default'
theme.conf found! Loading option-overrides.
Loaded theme config from: /usr/share/screenlets/Netmonitor/themes/ModernBlack/theme.conf
	Name: ModernBlack
	Author: Jovicic Nemanja
	Version: 1.0
	Info: ModernBlack theme
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
Override: text_color
WARNING: Option 'text_color' not found or protected.
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
Set options in CountdownScreenlet
Set options in NetmonitorScreenlet
Theme set to: 'Transparent'
theme.conf found! Loading option-overrides.
Loaded theme config from: /usr/share/screenlets/Netmonitor/themes/Transparent/theme.conf
	Name: Transparent
	Author: Helder Fraga edited by Nemanja Jovicic
	Version: 1.0
	Info: Transparent theme
Restored instances from session 'default' ...

Screen geometry changed:
   0x0x1400x1050

Override: text_color
Restored instances from session 'default' ...
Can't open folder /proc/acpi/thermal_zone/
Can't open /proc/acpi/ibm/thermal
Can't open /proc/acpi/ibm/fan
reseting...
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/screenlets/__init__.py", line 2045, in expose
    self.on_draw(ctx)
  File "/usr/share/screenlets/Netmonitor/NetmonitorScreenlet.py", line 350, in on_draw
    self.get_load()
  File "/usr/share/screenlets/Netmonitor/NetmonitorScreenlet.py", line 233, in get_load
    self.reset()        
  File "/usr/share/screenlets/Netmonitor/NetmonitorScreenlet.py", line 451, in reset
    f =  open( self.mypath + "codedDay","w") #// open for for write
IOError: [Errno 13] Permission denied: '/usr/share/screenlets/Netmonitor/codedDay'
theme.conf found! Loading option-overrides.
Loaded theme config from: /usr/share/screenlets/ClearWeather/themes/default/theme.conf
	Name: Stardock weather icons
	Author: Stardock Corporation
	Version: 1.0
	Info: These weather images are (c) 2003 by Stardock Corporation.  All rights reserved.
Hddtemp not installed
['temp1:        +29.0\xc2\xb0C  (crit = +60.0\xc2\xb0C)', 'k8temp-pci-00c3', 'Core0 Temp:   +32.0\xc2\xb0C', 'nvidia GPU ambiant: 33.0 C', 'nvidia GPU core: 44.0C']
unity-panel-service: no process found
Dropbox isn't running!
Done!
Can't open folder /proc/acpi/thermal_zone/
Can't open /proc/acpi/ibm/thermal
Can't open /proc/acpi/ibm/fan
Initializing unityshell options...done
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
WARNING - add_default_menuitems and add_menuitems should be set in on_init ,menu values will be displayed incorrectly
Set options in ClearWeatherScreenlet
Theme set to: 'default'
Hddtemp not installed
theme.conf found! Loading option-overrides.
Loaded theme config from: /usr/share/screenlets/ClearWeather/themes/default/theme.conf
	Name: Stardock weather icons
	Author: Stardock Corporation
	Version: 1.0
	Info: These weather images are (c) 2003 by Stardock Corporation.  All rights reserved.
Screenlet has been initialized.
Restored instances from session 'default' ...
Starting unity-window-decorator
Can't open folder /proc/acpi/thermal_zone/
Can't open /proc/acpi/ibm/thermal
Can't open /proc/acpi/ibm/fan
Hddtemp not installed
Theme set to: 'default'
Set options in RingSensorsScreenlet
Loaded config from: RingSensors2.ini
Theme set to: 'default'
Set options in RingSensorsScreenlet
Loaded config from: RingSensors3.ini
Theme set to: 'default'
Set options in RingSensorsScreenlet
Theme set to: 'default'
DEBUG 2011-12-02 22:24:12 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1400 h=1050
Loaded config from: RingSensors1.ini~
Restored instances from session 'default' ...

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** Message: moving back from GtkStatusIcon to indicator

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
QSystemTrayIcon::setVisible: No Icon set
Setting Update "launcher_hide_mode"
Setting Update "icon_size"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2e00007


** (process:16057): WARNING **: recent-manager-provider.vala:125: Desktop file for firefox8 was not found

** (process:16057): WARNING **: recent-manager-provider.vala:125: Desktop file for firefox8 was not found

** (process:16057): WARNING **: recent-manager-provider.vala:125: Desktop file for firefox8 was not found

** (process:16057): WARNING **: recent-manager-provider.vala:125: Desktop file for firefox8 was not found

** (process:16057): WARNING **: recent-manager-provider.vala:125: Desktop file for firefox8 was not found

** (process:16057): WARNING **: recent-manager-provider.vala:125: Desktop file for firefox8 was not found

** (process:16057): WARNING **: recent-manager-provider.vala:125: Desktop file for firefox8 was not found

** (process:16057): WARNING **: recent-manager-provider.vala:125: Desktop file for firefox8 was not found

** (process:16057): WARNING **: recent-manager-provider.vala:125: Desktop file for thunderbird-bin was not found

** (process:16057): WARNING **: recent-manager-provider.vala:125: Desktop file for firefox8 was not found

** (process:16057): WARNING **: recent-manager-provider.vala:125: Desktop file for firefox8 was not found
WARN  2011-12-02 22:24:23 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-02 22:24:23 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
** (nautilus:15700): DEBUG: Got notification of SyncDaemon startup in NameOwnerChanged
WARN  2011-12-02 22:24:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-12-02 22:24:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-12-02 22:24:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-12-02 22:24:32 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-12-02 22:24:33 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-12-02 22:24:33 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-12-02 22:24:33 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-12-02 22:24:33 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-12-02 22:24:34 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-12-02 22:24:34 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
WARN  2011-12-02 22:26:20 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


WARN  2011-12-02 22:26:20 glib.glib-gobject <unknown>:0 instance with invalid (NULL) class pointer
** (nm-applet:15677): DEBUG: foo_client_state_changed_cb
** (nm-applet:15677): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (nm-applet:15677): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (gnome-fallback-mount-helper:15712): DEBUG: Screensaver active changed to 1
** (gnome-fallback-mount-helper:15712): DEBUG: ConsoleKit session is active 0
** (gnome-fallback-mount-helper:15712): DEBUG: ConsoleKit session is active 1

(gnome-settings-daemon:15651): color-plugin-WARNING **: Done switch to new account, reload devices
** (nm-applet:15677): DEBUG: old state indicates that this was not a disconnect 10
** (nm-applet:15677): DEBUG: foo_client_state_changed_cb
** (nm-applet:15677): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:15677): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:15677): DEBUG: old state indicates that this was not a disconnect 20
** (nm-applet:15677): DEBUG: foo_client_state_changed_cb
** (nm-applet:15677): DEBUG: foo_client_state_changed_cb
WARN  2011-12-02 22:27:41 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window79691780: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2011-12-02 22:27:41 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0xf760d0: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2011-12-02 22:27:41 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window79691780: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2011-12-02 22:27:41 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0xf760d0: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

** (gnome-fallback-mount-helper:15712): DEBUG: Screensaver active changed to 0
** (deja-dup-monitor:16686): DEBUG: monitor.vala:221: Automatic backups disabled.  Not scheduling a backup.

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:15700): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
```
> And, can you try suspending one more time from the unity menu and then post back the results of:
```
cat /var/log/syslog* | grep PM:
```
```
Dec  2 19:35:28 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  2 19:35:28 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec  2 19:35:28 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec  2 19:35:28 Panther2 kernel: [    0.064003] PM: Registering ACPI NVS region at 3fee0000 (12288 bytes)
Dec  2 19:35:28 Panther2 kernel: [    0.382541] PM: Hibernation image not present or could not be loaded.
Dec  2 22:15:33 Panther2 kernel: [ 9603.866602] PM: Syncing filesystems ... done.
Dec  2 22:15:33 Panther2 kernel: [ 9603.998797] PM: Preparing system for mem sleep
Dec  2 22:17:54 Panther2 kernel: [ 9745.092369] PM: Syncing filesystems ... done.
Dec  2 22:17:54 Panther2 kernel: [ 9745.429508] PM: Preparing system for mem sleep
Dec  2 22:27:30 Panther2 kernel: [10320.492431] PM: Syncing filesystems ... done.
Dec  2 22:27:30 Panther2 kernel: [10320.814207] PM: Preparing system for mem sleep
Dec  2 22:30:27 Panther2 kernel: [10498.126143] PM: Syncing filesystems ... done.
Dec  2 22:30:27 Panther2 kernel: [10498.385727] PM: Preparing system for mem sleep
Dec  1 16:22:44 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  1 16:22:44 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec  1 16:22:44 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec  1 16:22:44 Panther2 kernel: [    0.068003] PM: Registering ACPI NVS region at 3fee0000 (12288 bytes)
Dec  1 16:22:44 Panther2 kernel: [    0.390308] PM: Hibernation image not present or could not be loaded.
Dec  1 17:39:44 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  1 17:39:44 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec  1 17:39:44 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec  1 17:39:44 Panther2 kernel: [    0.068003] PM: Registering ACPI NVS region at 3fee0000 (12288 bytes)
Dec  1 17:39:44 Panther2 kernel: [    0.390319] PM: Hibernation image not present or could not be loaded.
Dec  1 20:20:27 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  1 20:20:27 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec  1 20:20:27 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec  1 20:20:27 Panther2 kernel: [    0.068003] PM: Registering ACPI NVS region at 3fee0000 (12288 bytes)
Dec  1 20:20:27 Panther2 kernel: [    0.390472] PM: Hibernation image not present or could not be loaded.
Dec  1 20:55:45 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Dec  1 20:55:45 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec  1 20:55:45 Panther2 kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec  1 20:55:45 Panther2 kernel: [    0.068003] PM: Registering ACPI NVS region at 3fee0000 (12288 bytes)
Dec  1 20:55:46 Panther2 kernel: [    0.390567] PM: Hibernation image not present or could not be loaded.
```
> and the contents of /var/log/pm-suspend.log on more time?
```
Initial commandline parameters: 
Fri Dec  2 22:15:02 GMT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Panther2 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xts                    12756  0 
gf128mul               14951  1 xts
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
des_generic            21415  0 
md4                    12595  0 
nls_utf8               12557  3 
cifs                  273898  4 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
autofs4                37024  5 
dm_crypt               23199  0 
snd_usb_audio         118064  1 
snd_hwdep              13668  1 snd_usb_audio
snd_usbmidi_lib        25371  1 snd_usb_audio
nvidia              11713772  40 
ppdev                  17113  0 
joydev                 17693  0 
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               93004  1 gspca_main
v4l2_compat_ioctl32    17083  1 videodev
snd_via82xx            29735  2 
edac_core              53746  0 
psmouse                73882  0 
edac_mce_amd           23709  0 
serio_raw              13166  0 
k8temp                 13057  0 
snd_mpu401_uart        14169  1 snd_via82xx
i2c_viapro             13153  0 
shpchp                 37345  0 
parport_pc             36962  1 
snd_ens1371            25748  2 
gameport               19693  3 snd_via82xx,snd_ens1371
snd_ac97_codec        134826  2 snd_via82xx,snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96755  4 snd_usb_audio,snd_via82xx,snd_ens1371,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  4 snd_usbmidi_lib,snd_mpu401_uart,snd_ens1371,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  22 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_via82xx,snd_mpu401_uart,snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_via82xx,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
vesafb                 13809  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
r8169                  52788  0 
sata_promise           18401  5 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_via               13670  3 
floppy                 70365  0 
             total       used       free     shared    buffers     cached
Mem:       1021324     956740      64584          0       8212     115608
-/+ buffers/cache:     832920     188404
Swap:      2096476     716056    1380420

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Dec  2 22:15:09 GMT 2011: performing suspend
s2ram_do: Device or resource busy
switching from vt7 to vt1... succeeded
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
Fri Dec  2 22:15:33 GMT 2011: Awake.
Fri Dec  2 22:15:33 GMT 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
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
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Dec  2 22:15:37 GMT 2011: Finished.
Initial commandline parameters: 
Fri Dec  2 22:17:23 GMT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Panther2 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xts                    12756  0 
gf128mul               14951  1 xts
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
des_generic            21415  0 
md4                    12595  0 
nls_utf8               12557  3 
cifs                  273898  4 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
autofs4                37024  5 
dm_crypt               23199  0 
snd_usb_audio         118064  1 
snd_hwdep              13668  1 snd_usb_audio
snd_usbmidi_lib        25371  1 snd_usb_audio
nvidia              11713772  44 
ppdev                  17113  0 
joydev                 17693  0 
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               93004  1 gspca_main
v4l2_compat_ioctl32    17083  1 videodev
snd_via82xx            29735  2 
edac_core              53746  0 
psmouse                73882  0 
edac_mce_amd           23709  0 
serio_raw              13166  0 
k8temp                 13057  0 
snd_mpu401_uart        14169  1 snd_via82xx
i2c_viapro             13153  0 
shpchp                 37345  0 
parport_pc             36962  1 
snd_ens1371            25748  2 
gameport               19693  3 snd_via82xx,snd_ens1371
snd_ac97_codec        134826  2 snd_via82xx,snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96755  4 snd_usb_audio,snd_via82xx,snd_ens1371,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  4 snd_usbmidi_lib,snd_mpu401_uart,snd_ens1371,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  22 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_via82xx,snd_mpu401_uart,snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_via82xx,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
vesafb                 13809  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
r8169                  52788  0 
sata_promise           18401  5 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_via               13670  3 
floppy                 70365  0 
             total       used       free     shared    buffers     cached
Mem:       1021324     971508      49816          0       5716     100996
-/+ buffers/cache:     864796     156528
Swap:      2096476     736784    1359692

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Dec  2 22:17:32 GMT 2011: performing suspend
s2ram_do: Device or resource busy
switching from vt7 to vt1... succeeded
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
Fri Dec  2 22:17:55 GMT 2011: Awake.
Fri Dec  2 22:17:55 GMT 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
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
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Dec  2 22:18:02 GMT 2011: Finished.
Initial commandline parameters: 
Fri Dec  2 22:27:01 GMT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Panther2 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xts                    12756  0 
gf128mul               14951  1 xts
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
des_generic            21415  0 
md4                    12595  0 
nls_utf8               12557  2 
cifs                  273898  3 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
autofs4                37024  5 
dm_crypt               23199  0 
snd_usb_audio         118064  1 
snd_hwdep              13668  1 snd_usb_audio
snd_usbmidi_lib        25371  1 snd_usb_audio
nvidia              11713772  40 
ppdev                  17113  0 
joydev                 17693  0 
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               93004  1 gspca_main
v4l2_compat_ioctl32    17083  1 videodev
snd_via82xx            29735  2 
edac_core              53746  0 
psmouse                73882  0 
edac_mce_amd           23709  0 
serio_raw              13166  0 
k8temp                 13057  0 
snd_mpu401_uart        14169  1 snd_via82xx
i2c_viapro             13153  0 
shpchp                 37345  0 
parport_pc             36962  1 
snd_ens1371            25748  2 
gameport               19693  3 snd_via82xx,snd_ens1371
snd_ac97_codec        134826  2 snd_via82xx,snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96755  4 snd_usb_audio,snd_via82xx,snd_ens1371,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  4 snd_usbmidi_lib,snd_mpu401_uart,snd_ens1371,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  22 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_via82xx,snd_mpu401_uart,snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_via82xx,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
vesafb                 13809  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
r8169                  52788  0 
sata_promise           18401  5 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_via               13670  3 
floppy                 70365  0 
             total       used       free     shared    buffers     cached
Mem:       1021324     947444      73880          0      11208     126432
-/+ buffers/cache:     809804     211520
Swap:      2096476      53284    2043192

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Dec  2 22:27:07 GMT 2011: performing suspend
s2ram_do: Device or resource busy
switching from vt7 to vt1... succeeded
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
Fri Dec  2 22:27:30 GMT 2011: Awake.
Fri Dec  2 22:27:30 GMT 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
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
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Dec  2 22:27:37 GMT 2011: Finished.
Initial commandline parameters: 
Fri Dec  2 22:30:01 GMT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Panther2 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
xts                    12756  0 
gf128mul               14951  1 xts
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
des_generic            21415  0 
md4                    12595  0 
nls_utf8               12557  2 
cifs                  273898  3 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
autofs4                37024  5 
dm_crypt               23199  0 
snd_usb_audio         118064  1 
snd_hwdep              13668  1 snd_usb_audio
snd_usbmidi_lib        25371  1 snd_usb_audio
nvidia              11713772  44 
ppdev                  17113  0 
joydev                 17693  0 
gspca_zc3xx            52562  0 
gspca_main             28314  1 gspca_zc3xx
videodev               93004  1 gspca_main
v4l2_compat_ioctl32    17083  1 videodev
snd_via82xx            29735  2 
edac_core              53746  0 
psmouse                73882  0 
edac_mce_amd           23709  0 
serio_raw              13166  0 
k8temp                 13057  0 
snd_mpu401_uart        14169  1 snd_via82xx
i2c_viapro             13153  0 
shpchp                 37345  0 
parport_pc             36962  1 
snd_ens1371            25748  2 
gameport               19693  3 snd_via82xx,snd_ens1371
snd_ac97_codec        134826  2 snd_via82xx,snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96755  4 snd_usb_audio,snd_via82xx,snd_ens1371,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  4 snd_usbmidi_lib,snd_mpu401_uart,snd_ens1371,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  22 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_via82xx,snd_mpu401_uart,snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_via82xx,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
vesafb                 13809  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
r8169                  52788  0 
sata_promise           18401  5 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_via               13670  3 
floppy                 70365  0 
             total       used       free     shared    buffers     cached
Mem:       1021324     947504      73820          0       9176     123932
-/+ buffers/cache:     814396     206928
Swap:      2096476     122692    1973784

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Dec  2 22:30:06 GMT 2011: performing suspend
s2ram_do: Device or resource busy
switching from vt7 to vt1... succeeded
fbcon fb0 state 1
fbcon fb0 state 0
switching back to vt7... succeeded
Fri Dec  2 22:30:28 GMT 2011: Awake.
Fri Dec  2 22:30:28 GMT 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
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
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Dec  2 22:30:34 GMT 2011: Finished.
```

---

### Post by Toz on 2011-12-03
@curts, welcome back.
To recap, and to make sure I have this correct, suspend works properly from the command line but not from the unity menu.

After a fresh reboot, can you re-run the following command to see if it works:
```
dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

---

### Post by curts on 2011-12-04
> **Toz said:**
> @curts, welcome back.
To recap, and to make sure I have this correct, suspend works properly from the command line but not from the unity menu.

After a fresh reboot, can you re-run the following command to see if it works:
```
dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```
After a fresh reboot, the above command does not work on my PC.

Suspend from the unity menu does not work.  The following command does work properly from the command line:
```
sudo pm-suspend
```

---

### Post by Toz on 2011-12-05
Been researching this a bit. What do the following commands return:
```
pkaction -h | grep upower
```
```
apt-cache policy upower
```
```
cat /var/log/syslog | grep dbus
```

And, do you have a live cd around? If so, try booting with it and see if the unity suspend menu item works.

---

### Post by curts on 2011-12-07
> **Toz said:**
> Been researching this a bit. What do the following commands return:
```
pkaction -h | grep upower
```
```
org.freedesktop.upower.hibernate
org.freedesktop.upower.qos.cancel-request
org.freedesktop.upower.qos.request-latency
org.freedesktop.upower.qos.request-latency-persistent
org.freedesktop.upower.qos.set-minimum-latency
org.freedesktop.upower.suspend

```
> ```
apt-cache policy upower
```
```
upower:
  Installed: 0.9.13-1
  Candidate: 0.9.13-1
  Version table:
 *** 0.9.13-1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status

```
> ```
cat /var/log/syslog | grep dbus
```
```
Dec  7 07:00:35 Panther2 dbus[1081]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec  7 07:00:36 Panther2 dbus[1081]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec  7 07:08:53 Panther2 dbus[1112]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Dec  7 07:08:53 Panther2 dbus[1112]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Dec  7 07:08:53 Panther2 dbus[1112]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Dec  7 07:08:54 Panther2 dbus[1112]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Dec  7 07:08:55 Panther2 dbus[1112]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Dec  7 07:08:55 Panther2 dbus[1112]: [system] Successfully activated service 'org.freedesktop.Accounts'
Dec  7 07:08:56 Panther2 dbus[1112]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Dec  7 07:08:56 Panther2 dbus[1112]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Dec  7 07:08:58 Panther2 dbus[1112]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Dec  7 07:08:58 Panther2 dbus[1112]: [system] Successfully activated service 'org.freedesktop.UPower'
Dec  7 07:08:59 Panther2 dbus[1112]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Dec  7 07:08:59 Panther2 dbus[1112]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Dec  7 07:09:17 Panther2 dbus[1112]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Dec  7 07:09:17 Panther2 dbus[1112]: [system] Successfully activated service 'org.freedesktop.UDisks'
Dec  7 07:10:19 Panther2 dbus[1112]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Dec  7 07:10:19 Panther2 dbus[1112]: [system] Successfully activated service 'com.ubuntu.SystemService'
Dec  7 07:10:37 Panther2 dbus[1112]: [system] Activating service name='org.debian.apt' (using servicehelper)
Dec  7 07:10:38 Panther2 dbus[1112]: [system] Successfully activated service 'org.debian.apt'
Dec  7 07:10:38 Panther2 dbus[1112]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec  7 07:10:39 Panther2 dbus[1112]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec  7 18:32:30 Panther2 dbus[1077]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Dec  7 18:32:30 Panther2 dbus[1077]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Dec  7 18:32:31 Panther2 dbus[1077]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Dec  7 18:32:31 Panther2 dbus[1077]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Dec  7 18:32:32 Panther2 dbus[1077]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Dec  7 18:32:32 Panther2 dbus[1077]: [system] Successfully activated service 'org.freedesktop.Accounts'
Dec  7 18:32:33 Panther2 dbus[1077]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Dec  7 18:32:33 Panther2 dbus[1077]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Dec  7 18:32:34 Panther2 dbus[1077]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Dec  7 18:32:34 Panther2 dbus[1077]: [system] Successfully activated service 'org.freedesktop.UPower'
Dec  7 18:32:34 Panther2 dbus[1077]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec  7 18:32:35 Panther2 dbus[1077]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec  7 18:32:35 Panther2 dbus[1077]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Dec  7 18:32:35 Panther2 dbus[1077]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Dec  7 18:39:05 Panther2 dbus[1077]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Dec  7 18:39:06 Panther2 dbus[1077]: [system] Successfully activated service 'org.freedesktop.UDisks'
Dec  7 18:40:07 Panther2 dbus[1077]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Dec  7 18:40:08 Panther2 dbus[1077]: [system] Successfully activated service 'com.ubuntu.SystemService'
Dec  7 18:40:25 Panther2 dbus[1077]: [system] Activating service name='org.debian.apt' (using servicehelper)
Dec  7 18:40:26 Panther2 dbus[1077]: [system] Successfully activated service 'org.debian.apt'
Dec  7 20:59:17 Panther2 kernel: [ 8833.517467] rhythmbox[8040] general protection ip:7fee94e8f9b1 sp:7fffebf01a80 error:0 in libdbus-media-server.so[7fee94e88000+b000]

```
> And, do you have a live cd around? If so, try booting with it and see if the unity suspend menu item works.
I have the 11.04 AMD64 live cd handy.  Will that satisfy your test or do I need to download the 11.10 AMD64 iso?

Thanks for your help,

Curt

---

### Post by IndieRockSteve on 2011-12-07
I'm interested in this too as this appears to be an issue on my mom's Lenovo Thinkpad SL400. If I try and suspend from the menu the screen turns black except for the date and logged in user name on the top bar.

when I "wake" it up I can no longer connect to the wireless network. even turning off, then on the wireless networking does nothing. as well, I'm unable to log out or reboot/poweroff. all in all, attempting to suspend makes nothing useful work...

as well, if the laptop "suspends" while in the lightdm login screen (ie closes the screen), if I "wake" it, and then try and log in, none of my users can fully log in.

---

### Post by Toz on 2011-12-07
> **curts said:**
> I have the 11.04 AMD64 live cd handy.  Will that satisfy your test or do I need to download the 11.10 AMD64 iso?
Sure, give it a try. I'm curious if it works out of the box.

---

### Post by Ghouli on 2011-12-08
I've been trying to get suspend work from time to time, but it just seems busted and determined to stay that way. Had this problem since I switched from 10.04 to 11.04, hard drives power down but fans just keep spinning and monitor doesn't switch off, just shows blank black screen. Since then I've changed motherboard and done fresh install of Ubuntu 11.10. Suspend still works fine when using 10.04 LiveCD.

---

### Post by curts on 2011-12-10
> **Toz said:**
> Sure, give it a try. I'm curious if it works out of the box.
OK, using the 11.04 live cd, my PC did enter the suspend state, but did not successfully resume.  This probably isn't a surprising result, as my PC did not even shutdown reliably with 11.04 installed.  At least with 11.10 shutdown works correctly now.  Do I need to repeat the test with the 11.10 live cd?

---

### Post by curts on 2011-12-10
@Toz

Installed today's 11.10 updates including the ACPI update.  After the restart, my PC successfully suspended from the Unity menu for the first time and successfully resumed.  Next test will be to try it again after the session has been running for part of a day.

---

### Post by Toz on 2011-12-10
> **curts said:**
> @Toz

Installed today's 11.10 updates including the ACPI update.  After the restart, my PC successfully suspended from the Unity menu for the first time and successfully resumed.  Next test will be to try it again after the session has been running for part of a day.

Thats good news. Maybe the updated fixed the problem. Its a tough one to track down.

---

### Post by curts on 2011-12-12
> **Toz said:**
> Thats good news. Maybe the updated fixed the problem. Its a tough one to track down.

It does look like the recent ACPI update has fixed my suspend problem.  It hasn't failed after several cycles of usage.

---

### Post by nirensinha on 2012-03-24
I am also having this issue. At times on suspend, the system tries to suspend and makes a switch off noise as if its suspended but the monitor shows tty login screen and the system is still on.

---

