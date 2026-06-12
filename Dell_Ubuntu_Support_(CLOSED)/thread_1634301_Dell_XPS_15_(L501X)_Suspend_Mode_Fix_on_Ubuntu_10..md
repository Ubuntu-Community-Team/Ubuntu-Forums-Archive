---
title: "Dell XPS 15 (L501X) Suspend Mode Fix on Ubuntu 10.10"
date: 2010-11-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by krunalpatel on 2010-11-30
USE THIS METHOD IF YOU ARE GETTING THIS ERROR IN SYS LOG:
> 
kernel: [ 2530.896818] pm_op(): usb_dev_suspend+0x0/0x20 returns -2
kernel: [ 2530.896821] PM: Device usb3 failed to suspend async: error -2
kernel: [ 2530.943466] PM: Some devices failed to suspend
kernel: [ 2530.943626] hub 2-1:1.0: hub_port_status failed (err = -113)
kernel: [ 2530.943631] hub 2-1:1.0: cannot disable port 5 (err = -113)
kernel: [ 2530.943637] pm_op(): usb_dev_resume+0x0/0x20 returns -113
kernel: [ 2530.943639] PM: Device 2-1.5 failed to resume async: error -113



1. Unbind xhci_hcd from kernel:

First, verify what devices you need to unload from kernel. Simple list the directory "/sys/bus/pci/drivers/xhci_hcd/" and pick all devices id that has names like "XXXX:XX:XX:X". You may have more than one device listed.

2. Create custom file /etc/pm/sleep.d/20_custom-xhci_hcd

> #!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-xhci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind xhci_hcd for first device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/xhci_hcd/unbind
              # Unbind xhci_hcd for second device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/xhci_hcd/unbind
        ;;
        resume|thaw)
              # Bind xhci_hcd for first device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/xhci_hcd/bind
              # Bind xhci_hcd for second device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/xhci_hcd/bind
        ;;
esac


3. Unload modelue xhci (usb3):

Create a file "/etc/pm/config.d/usb3-suspend-workaround", with the following content:
> #File: "/etc/pm/config.d/usb3-suspend-workaround".
SUSPEND_MODULES="xhci"

4. sudo chmod +x /etc/pm/sleep.d/20_custom-xhci_hcd

---

### Post by dann.ormond on 2010-12-16
I had problems with suspending and didn't see the same failure to suspend message in /var/log/syslog but I still followed your steps and it fixed my suspending.

I would try this solution to suspending if your XPS L501X isn't suspending.

Thanks for the solution!

Dann

---

### Post by mefesto on 2010-12-17
@krunalpatel Thanks so much for this fix. It works great as long as the dell bluetooth is disabled in the bios. But when enabled it seems that the bluetooth no longer works once resumed.

I don't suppose anyone knows of a fix for this?

> 
[   71.054985] WARNING: at /build/buildd/linux-2.6.35/fs/sysfs/dir.c:451 sysfs_add_one+0xc5/0x130()
[   71.054987] Hardware name: XPS L501X  
[   71.054988] sysfs: cannot create duplicate filename '/class/bluetooth/hci0:11'
[   71.054989] Modules linked in: cryptd aes_x86_64 aes_generic hidp hid parport_pc ppdev snd_hda_codec_nvhdmi joydev rfcomm binfmt_misc sco bnep l2cap snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec iwlagn nvidia(P) snd_hwdep snd_pcm iwlcore snd_seq_midi mac80211 snd_rawmidi uvcvideo snd_seq_midi_event videodev v4l1_compat snd_seq snd_timer snd_seq_device dell_wmi snd v4l2_compat_ioctl32 dell_laptop intel_ips dcdbas btusb bluetooth xhci_hcd psmouse i7core_edac serio_raw cfg80211 video edac_core soundcore snd_page_alloc output lp parport ahci r8169 libahci mii
[   71.055018] Pid: 2452, comm: hci0 Tainted: P      D     2.6.35-23-generic #41-Ubuntu
[   71.055020] Call Trace:
[   71.055025]  [<ffffffff8106078f>] warn_slowpath_common+0x7f/0xc0
[   71.055027]  [<ffffffff81060886>] warn_slowpath_fmt+0x46/0x50
[   71.055029]  [<ffffffff811bfa45>] sysfs_add_one+0xc5/0x130
[   71.055032]  [<ffffffff811c029b>] sysfs_do_create_link+0x13b/0x210
[   71.055034]  [<ffffffff811c03a3>] sysfs_create_link+0x13/0x20
[   71.055038]  [<ffffffff81384b7c>] device_add_class_symlinks+0x6c/0x100
[   71.055040]  [<ffffffff811be4c6>] ? sysfs_create_file+0x26/0x30
[   71.055043]  [<ffffffff81385aa8>] device_add+0x238/0x440
[   71.055045]  [<ffffffff81385461>] ? device_private_init+0x71/0x80
[   71.055051]  [<ffffffffa0c1ae0b>] add_conn+0x5b/0xe0 [bluetooth]
[   71.055055]  [<ffffffffa0c1adb0>] ? add_conn+0x0/0xe0 [bluetooth]
[   71.055059]  [<ffffffff8107a775>] run_workqueue+0xc5/0x1a0
[   71.055061]  [<ffffffff8107a8f3>] worker_thread+0xa3/0x110
[   71.055064]  [<ffffffff8107f620>] ? autoremove_wake_function+0x0/0x40
[   71.055066]  [<ffffffff8107a850>] ? worker_thread+0x0/0x110
[   71.055068]  [<ffffffff8107f0c6>] kthread+0x96/0xa0
[   71.055071]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
[   71.055073]  [<ffffffff8107f030>] ? kthread+0x0/0xa0
[   71.055075]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
[   71.055076] ---[ end trace 0cac1aa663bf114e ]---


---

### Post by dydimus on 2010-12-22
Hi,

I'm having the same suspend problem with a Dell XPS 15 but I'm relatively new to Ubuntu.

This fix seems to be what I need.

Would it be possible to give a more detailed procedure to fix this problem?

Thanks!

---

### Post by krunalpatel on 2010-12-24
> **dydimus said:**
> Hi,

I'm having the same suspend problem with a Dell XPS 15 but I'm relatively new to Ubuntu.

This fix seems to be what I need.

Would it be possible to give a more detailed procedure to fix this problem?

Thanks!

What part exactly can't you follow? Give us an idea and we can help

---

### Post by dydimus on 2010-12-24
Thank you!

I tried to create the file as indicated in point 2 but it tells me I can't save it because I don't have authorisation. Also I don't know if I have to copy all of the text in the quote into the new file (sorry I'm fairly new to this and mostly don't really understand what I'm doing).

I dindn't get to point 3 because I couldn't create that file...

Does this makes sense? I'd appreciate any help since suspending is essencial for me.

Many thanks!

---

### Post by krunalpatel on 2010-12-24
> **dydimus said:**
> Thank you!
 
I tried to create the file as indicated in point 2 but it tells me I can't save it because I don't have authorisation. Also I don't know if I have to copy all of the text in the quote into the new file (sorry I'm fairly new to this and mostly don't really understand what I'm doing).
 
I dindn't get to point 3 because I couldn't create that file...
 
Does this makes sense? I'd appreciate any help since suspending is essencial for me.
 
Many thanks!
 
use sudo
 
sudo gedit /location/filename

---

### Post by dydimus on 2010-12-25
Thanks, it worked, I created both files but when I get to point 4 and type:  sudo chmod +x /etc/pm/sleep.d/20_custom-xhci_hcd nothing seems to happen... and the suspend is still not working (I get a black screen with the prompt box to give my password but it doesn't really suspend)

Thanks again for your help!

---

### Post by dydimus on 2010-12-26
OK Solved!!! I had not changed the file's (XXXX:XX:XX.X)name. Now I did it and suspension works perfectly!
Really many thanks for your help! One learns everyday something new.
Regards

---

### Post by kongo09 on 2011-01-20
sweet

---

### Post by kongo09 on 2011-01-20
sweet!

---

### Post by kichi1983 on 2011-01-21
Great..worked without any trouble. Thank you

---

### Post by lome on 2011-01-23
Great! I can suspend now, but I can´t wake up :(
The screen stays black and like powered off.
Any idea?

Thanks :)
Edit: Nevermind, I upgraded and the suspend mode works just fine!!! thanks!!!

---

### Post by slayerdme on 2011-02-02
Thank you!

Works perfectly after a full system update. (I have bluetooth disabled in BIOS though.)

---

### Post by lagonium on 2011-02-24
Hey guys,

My XPS 15 still won't suspend, even after I have done the custom xhci_hcd file.  I chmodded it and set it up just like krunalpatel said, but my laptop still won't suspend or hibernate.  My syslog error says this:

Feb 24 05:39:22 [ 1407.313037] pm_op(): usb_dev_suspend+0x0/0x20 returns -2
Feb 24 05:39:22 [ 1407.313040] PM: Device usb3 failed to suspend async: error -2
Feb 24 05:39:22 [ 1407.358686] PM: Some devices failed to suspend

That's all the errors I get, nothing about a hub failing to suspend like krunalpatel listed.  Anyone have ideas on what I need to do to get my laptop properly suspending/hibernating?  Should I make the XHCI unbind before everything else (change the file to say '05_custom_xhci-hcd' or would that not make a difference?

Thanks in advance.

---

### Post by energyguy78 on 2011-02-26
how do you find the devices?

---

### Post by lagonium on 2011-02-28
I finally got my XPS 15 to suspend properly.  If you are getting an error message like I was (nothing about a hub, and -2 errors instead of -113) I recommend you try this. (Taken from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998))  I modified these instructions just a little bit.  You'll see that they say you should only put SUSPEND_MODULES="xhci" .  I found that this didn't work.  Ubuntu calls USB3 'xhci-hcd' so I tried that and bingo it worked.

Instead of making a file unbind and rebind the whole USB3 system, just make a file called "unload_module" in /etc/pm/config.d and into the file all you have to put is ' SUSPEND_MODULES="xhci-hcd" ' and it should work.  I no longer have problems with suspending, and my USB3 ports still work fine.  I guess I had a different problem - I hope this works for anyone else who tries it!

Good luck with your XPS 15 adventures. :)

---

### Post by iammeagain on 2011-03-14
Thanks for this, got the job done. 
I only had the usb 3.0 messing up my suspend mode. Although it does still take a while to suspend. Like 20-30 seconds. Any way to know whats making it take a while?

---

### Post by lagonium on 2011-03-14
I think that my suspend method is going to cause problems.  I can only use my USB2 port.  The USB3 ones cause kernel panics every time.  I think I need to do a method like above, and suspend the module only when the computer is going to sleep.  I think that my config file completely turned off the USB3 system, which makes sense, really.  it's in config.d and all it says is to suspend the module, so it must be across the board.

I'll switch around my config setup and see what happens.

Sorry, iammeagain, I don't know what's taking your computer so long to sleep.  It takes mine maybe 10 to 20 seconds, depending on what I'm doing.  The more you're doing, the more it will have to put into RAM and the longer it will take.

---

### Post by rodrigosprimo on 2011-03-17
Thanks!

All I had to do was create a file on /etc/pm/config.d with:

SUSPEND_MODULES="xhci-hcd"

As suggested by lagonium.

---

### Post by Darque1137 on 2011-03-18
That fixes Suspend on my new XPS 15, and increases its general usability tenfold.  Slowly but surely getting this thing together...

Thank you!

---

### Post by lagonium on 2011-03-18
Well, I guess that my suspend fix is not to blame here.  I am able to use my USB3 ports after suspending and waking up again today.  I think the problem might have been the amount of uptime last time I tried to use USB3.  I had suspended and woken up my computer a bunch of times that week instead of shutting down at the end of the day.  Maybe all that stuff made the USB3 fritz out.  I have yet to try suspending with a device attached to the USB3 ports, and I am hesitant to try it.

I'm glad that my fix worked for you rodrigosprimo!  This is my first time really diving into using Linux and it's nice to hear that I helped someone else.  

Had I been smarter about the laptop I bought, I would have gone with an Asus G53 or G73, since they seem to have better luck with Linux than anything Dell offers.  Oh well.  Lesson learned

(*Perhaps not.  Anything with Optimus will cause trouble right now, so everyone hold tight until the devs release some kind of hybrid driver.  I'm so glad I got the L501x with i7.  There's no optimus to contend with, so the GT435M works perfectly!*)

---

### Post by enigmatichus on 2011-03-22
Great work!!
It fixed my L702X without any problem! I hope I'll find such a good solution for the L502X/L702X's "lcd brightness" issue as well!
Thank you again!

---

### Post by plasm980 on 2011-04-14
OMG Thank you!

---

### Post by iammeagain on 2011-05-01
I used this before and it was a bit help, although now it appears with 11.04 this isn't necessary. Just thought I would put that out there so people don't have to deal with more problems than necessary.

Also the usb 3.0 also seems to be usable from 11.04, before it crashed my system.

---

