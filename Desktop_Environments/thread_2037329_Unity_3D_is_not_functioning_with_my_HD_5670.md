---
title: "Unity 3D is not functioning with my HD 5670"
date: 2012-08-04
forum: Desktop Environments
---

### Post by MaxR84 on 2012-08-04
Dear all
I'm having some problems after installing Ubuntu LTS 12.04 32bit on my system
```
cpu Intel Pentium Dual Core E6700
motherboard Asrock 4CoreDual-Sata2 R2.0
ram Corsair XMS 2x1GB PC2-6400
vga Sapphire Radeon 5670 512MB gddr5 pci-e
audio Creative Sound Blaster Audigy 2 Zs
hdd Western Digital 160GB
wi-fi Dlink DWA-125 rev a2
```
I've installed also the last official Catalyst package by AMD and the test
```
/usr/lib/nux/unity_support_test -p
```
gave me good results
Anyway I actually can use Ubuntu 2D interface but Ubuntu (Unity 3D) is blocked
What can I do? Thanks in advance

---

### Post by MaxR84 on 2012-08-05
I've tried several times to update the os and the drivers, everytime cleaning the previous installation, without results: Unity 3D freezes. The system and the video card are in very good condition, on Windows it's all ok and also on Ubuntu 2D. I've tried Xonotic and it run fine.
Any idea? :(

Edit:

Probably I've made it all wrong.

I've retried */usr/lib/nux/unity_support_test -p *under Unity 3D and the result is
[I]
Error: unable to open display
[/I]
and after that *unity --reset *and it gave me
[I]
WARNING: no DISPLAY variable set, setting it to :0
WARNING: Unity currently default profile, so switching to metacity while resetting the value
Checking if setting need to be migrated ..no
Checking if internal files need to be migrated ..no
Backened    : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1800004

Initializing composite options...done[/I]

Also the command *compiz* says Fatal: Couldn't open display

---

### Post by MaxR84 on 2012-08-06
**cat /var/log/Xorg.0.log | grep EE**

(WW) Warning, ([COLOR=Red]EE[/COLOR]) Error, (NI) Not Implemented, (??) Unknown,
[17.641] (II) Loading Extension MIT-SCR[COLOR=Red]EE[/COLOR]N-SAVER
[18.346] (II) XKB: Reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26[COLOR=Red]EE[/COLOR]03343DB2C93394EA704B98F.xkm
[368.896] ([COLOR=Red]EE[/COLOR]) fglrx(0): PPLIB swIPPLibNotifyEventToPPLib() Failed!
[368.896] ([COLOR=Red]EE[/COLOR]) ulEventType = 00000023, ulEventData = 00000001

**/var/log/syslog**

```
*data* *ora* max-desktop kernel: [ 368.436036] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64  *data* *ora* max-desktop kernel: [ 368.446876] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64  *data* *ora* max-desktop kernel: [ 368.456581] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64  *data* *ora* max-desktop kernel: [ 368.476289] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64  *data* *ora* max-desktop kernel: [ 368.488819] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64  *data* *ora* max-desktop kernel: [ 368.531916] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64  *data* *ora* max-desktop kernel: [ 368.542465] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64  *data* *ora* max-desktop kernel: [ 368.563500] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64  *data* *ora* max-desktop kernel: [ 368.584386] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64  *data* *ora* max-desktop kernel: [ 368.594927] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64  *data* *ora* max-desktop kernel: [ 368.614507] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64  *data* *ora* max-desktop kernel: [ 368.625045] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line 64
```

---

### Post by MaxR84 on 2012-10-25
Same thing with Ubuntu 12.10 and lastest drivers :(

---

### Post by MaxR84 on 2012-11-09
Solved (apparently) with this command
```
sudo apt-get purge fglrx lightdm && sudo apt-get install lightdm ubuntu-desktop
```

---

### Post by MaxR84 on 2013-05-05
Dear all,
I've formatted and installed the last distribution: now the old problem is here again and the command is unuseful... Any ideas?

---

### Post by MaxR84 on 2013-05-09
Thanks for all the support :roll:
I'm going to use lxde

---

