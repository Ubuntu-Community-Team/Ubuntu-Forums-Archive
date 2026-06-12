---
title: "GDM running but no GUI shown"
date: 2018-10-18
forum: Desktop Environments
---

### Post by petersanchez on 2018-10-18
I am running 18.04, Thinkpad X1C6. Things were fine and the other day my laptop wouldn't wake from sleep so I had to hard boot it. Since then the GDM login manager screen doesn't actually show. It just hangs

[ATTACH=CONFIG]281379[/ATTACH]

It boots very fast like before. I have to alt+f2, login, (had to create my .xinitrc), and issue startx to get into my WM now.

This isn't the end of the world. Really more of an annoyance, but another thing seems to happen. When the screen goes to sleep, or even just at random, it goes back to the main boot screen (shown in the screenshot). I could be in the middle of working on something and it does that. I simply hit alt+f2 again and it takes me right back to my X session.

Super weird. I did an update & dist-upgrade the day this started (Tuesday, the 16th). 

Here's some info:

```

pjs:thinkpad ~ $ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic
pjs:thinkpad ~ $ uname -a
Linux thinkpad 4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
pjs:thinkpad ~ $

```

```
6.345s NetworkManager-wait-online.service
          6.327s [EMAIL="postgresql@10-main.servic"]postgresql@10-main.servic[/EMAIL]e
          1.735s snapd.service
           655ms ufw.service
           451ms keyboard-setup.service
           383ms dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
           296ms snap-gnome\x2dsystem\x2dmonitor-57.mount
           293ms systemd-journal-flush.service
           285ms systemd-logind.service
           284ms snap-gnome\x2d3\x2d26\x2d1604-70.mount
           283ms snapd.seeded.service
           275ms snap-gnome\x2dcharacters-103.mount
           236ms NetworkManager.service
           215ms redis-server.service
           197ms snap-gtk\x2dcommon\x2dthemes-701.mount
           186ms udisks2.service
           167ms snap-gnome\x2dsystem\x2dmonitor-51.mount
           156ms snap-gnome\x2dlogs-45.mount
           155ms snap-gnome\x2dlogs-43.mount
           152ms systemd-resolved.service
           148ms systemd-timesyncd.service
           142ms snap-gnome\x2dcalculator-238.mount
           138ms snap-gnome\x2dcalculator-222.mount
           128ms accounts-daemon.service
           127ms snap-gnome\x2dcalculator-199.mount
           127ms snap-gnome\x2dlogs-40.mount
           119ms snap-core-5328.mount
           103ms networkd-dispatcher.service
            98ms ModemManager.service
            95ms grub-common.service
            93ms speech-dispatcher.service
            93ms bluetooth.service
            91ms snap-gnome\x2dsystem\x2dmonitor-54.mount
            86ms snap-gnome\x2d3\x2d26\x2d1604-59.mount
            82ms snap-gtk\x2dcommon\x2dthemes-319.mount
            80ms apparmor.service
            79ms upower.service
            79ms gpu-manager.service
            78ms alsa-restore.service
            66ms sysstat.service
            64ms pppd-dns.service
            61ms thermald.service
            59ms wpa_supplicant.service
            55ms snap-gnome\x2dcharacters-117.mount
            54ms systemd-udev-trigger.service
            51ms snap-core-5662.mount
            40ms apport.service
            36ms lvm2-monitor.service
            35ms snap-core-5548.mount
            34ms snap-gnome\x2d3\x2d26\x2d1604-74.mount
            34ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
            33ms systemd-rfkill.service
            33ms [EMAIL="user@120.servic"]user@120.servic[/EMAIL]e
            29ms systemd-tmpfiles-clean.service
            29ms systemd-journald.service
            28ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-5021822d\x2d4528\x2d44ad\x2d905d\x2d008338404291.servic"]systemd-fsck@dev-disk-by\x2duuid-5021822d\x2d4528\x2d44ad\x2d905d\x2d008338404291.servic[/EMAIL]e
            25ms snap-gnome\x2dcharacters-124.mount
            25ms systemd-udevd.service
            24ms dev-loop16.device
            23ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-4E35\x2d86E5.servic"]systemd-fsck@dev-disk-by\x2duuid-4E35\x2d86E5.servic[/EMAIL]e
            22ms dev-loop17.device
            21ms networking.service
            21ms gdm.service
            20ms rsyslog.service
            19ms colord.service
            16ms dev-loop18.device
            15ms dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.swap
            15ms systemd-modules-load.service
            14ms plymouth-read-write.service
            14ms [EMAIL="lvm2-pvscan@253:0.servic"]lvm2-pvscan@253:0.servic[/EMAIL]e
            14ms polkit.service
            13ms systemd-tmpfiles-setup-dev.service
            13ms dev-loop19.device
            11ms deluged.service
            11ms systemd-remount-fs.service
            11ms ssh.service
            10ms ureadahead-stop.service
            10ms systemd-tmpfiles-setup.service
             9ms [EMAIL="systemd-backlight@leds:tpacpi::kbd_backlight.servic"]systemd-backlight@leds:tpacpi::kbd_backlight.servic[/EMAIL]e
             9ms console-setup.service
             9ms kerneloops.service
             9ms resolvconf-pull-resolved.service
             8ms setvtrgb.service
             8ms [EMAIL="systemd-cryptsetup@nvme0n1p3_crypt.servic"]systemd-cryptsetup@nvme0n1p3_crypt.servic[/EMAIL]e
             7ms boot-efi.mount
             7ms dev-loop5.device
             6ms systemd-sysctl.service
             6ms systemd-user-sessions.service
             6ms sys-kernel-debug.mount
             6ms dev-loop15.device
             6ms dns-clean.service
             5ms kmod-static-nodes.service
             5ms dev-hugepages.mount
             5ms boot.mount
             5ms systemd-update-utmp-runlevel.service
             4ms dev-loop7.device
             4ms dev-loop8.device
             4ms systemd-random-seed.service
             4ms rtkit-daemon.service
             4ms blk-availability.service
             3ms dev-loop1.device
             3ms sys-fs-fuse-connections.mount
             3ms systemd-update-utmp.service
             3ms dev-mqueue.mount
             2ms [EMAIL="systemd-backlight@backlight:intel_backlight.servic"]systemd-backlight@backlight:intel_backlight.servic[/EMAIL]e
             2ms dev-loop3.device
             2ms sys-kernel-config.mount
             2ms plymouth-quit-wait.service
             2ms dev-loop2.device
             2ms resolvconf.service
             2ms dev-loop11.device
             1ms dev-loop13.device
             1ms dev-loop4.device
             1ms dev-loop14.device
             1ms dev-loop12.device
             1ms dev-loop6.device
             1ms snapd.socket
             1ms postgresql.service
             1ms dev-loop0.device
           988us dev-loop10.device
           731us dev-loop9.device
```

Any ideas? Thanks in advance for any help!

Peter

---

### Post by Claus7 on 2018-10-19
Hello,

since your login screen has a problem, and since gdm is not responding well all the time under 18.04, I would advice you to check lightdm instead. If you are not happy, then you can revert back to gdm (this might fix gdm also). It is advised to purge completely gdm and install lightdm and vice versa. Reboot and check if things are working normally.

Regards!

---

### Post by petersanchez on 2018-10-19
Thanks for the reply. I have a new development.. So overnight I left my screen on, locked, like always. I came in and it was all black with errors (see photo below). Also, I had about 50gb of space used overnight. It was xorg logs:

[ATTACH=CONFIG]281387[/ATTACH]

> 
pjs:thinkpad ~/.local/share/xorg $ du -sh *
32K     Xorg.0.log
49G     Xorg.0.log.old


Here are the last 200 lines of the file (in pastebin): [http://dpaste.com/29AZFV9](http://dpaste.com/29AZFV9)

---

### Post by Claus7 on 2018-10-19
Hello,

with a quick search this indeed seems to be gdm related. With that you could eliminate one possibility. You could check it out and let us know.

Regards!

---

### Post by #&amp;thj^% on 2018-10-19
Give this a try:

```
sudo apt install haveged
sudo systemctl enable haveged

```
If after a reboot dose not help try the lightdm as  Claus7 suggests .

---

### Post by petersanchez on 2018-10-19
Thanks for the replies. I will try haveged and if no luck try lightdm. On another note, this other strange behavior is happening now. Multiple times the system load is very high and the fan is on (usually when leaving the computer idle for a bit).. I have these processes hogging all CPU:

> 
$ ps auxwwww | grep apt
(... trimmed other matches to show the 3 hogging cpu...)
_apt     28010 98.8  0.0  86876  8568 ?        R    08:00  85:33 /usr/lib/apt/methods/http
_apt     28014 97.6  0.0  86876  8564 ?        R    08:00  84:32 /usr/lib/apt/methods/http
_apt     28015 95.3  0.0  86876  8664 ?        R    08:00  82:31 /usr/lib/apt/methods/http


Also this:

> 
root      7203  100  0.9 233832 160924 ?       RN   09:27   0:02 /usr/bin/python3 /usr/lib/update-notifier/apt-check --human-readable


So random how these things all started after this gdm trouble. I will try the new suggestions shortly and report back. Thanks again for all the help so far!

---

### Post by petersanchez on 2018-10-19
Update. I installed haveged, rebooted and no change. I installed lightdm and now it's even worse. Now the screen just goes black at bootup and I can't even use alt+f2 to get a shell. I don't know what to do here.

I tried editing the grub boot setup at boot up (pressing e, changing quiet to text) and it boots differently (more text) but still the same thing. When I should get a login prompt the screen goes black and I can't switch to a terminal. If I press the power button the system responds to the acpi event and powers down and shows me text.

At this point I'd love to just remove gdm and lightdm and login directly and type startx hah. Any help?

---

### Post by #&amp;thj^% on 2018-10-19
When you installed lightdm did you remove/un-install gdm3?
Also known bug: [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1779476](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1779476)
Yours seems to mimic some of the listed reply's from those users.

---

### Post by petersanchez on 2018-10-19
Hi all, I'm embarrassed to admit this was all my fault. I had a faulty udev rules file which was altering permissions on /dev/* files, creating all sorts of weird behaviors. Thank you to TJ- on #ubuntu for spending all day helping me debug and resolve this.

---

