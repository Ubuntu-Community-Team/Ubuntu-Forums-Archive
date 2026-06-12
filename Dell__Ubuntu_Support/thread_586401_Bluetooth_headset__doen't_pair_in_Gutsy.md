---
title: "Bluetooth headset  doen't pair in Gutsy"
date: 2007-10-22
forum: Dell  Ubuntu Support
---

### Post by black_eye on 2007-10-22
I've installed 7.10 on my new Dell D830. Now I want to pair my headset  It is a Sony DR-BT10CX.

The headsset is found :

sudo hcitool scan:

00:13:A9:5C:xx:xx       DR-BT10CX

then there is an error:

sudo hidd --connect 00:13:A9:5C:xx:xx
Can't get device information: Success

then I tried something else:

btsco -v MAC

btsco v0.42
Error: control open (hw:1): No such device
Error: Can't find device. Bail

running sudo modprobe snd-bt-sco results in:
FATAL: Error inserting snd_bt_sco (/lib/modules/2.6.22-14-generic/ubuntu/snd-bt-sco.ko): Unknown symbol in module, or unknown parameter (see dmesg)

after this, dmesg | tail shows:
[ 8797.280000] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[ 8797.280000] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[ 8797.280000] snd_bt_sco: disagrees about version of symbol snd_hwdep_new
[ 8797.280000] snd_bt_sco: Unknown symbol snd_hwdep_new
[ 8797.280000] snd_bt_sco: disagrees about version of symbol snd_ctl_notify
[ 8797.280000] snd_bt_sco: Unknown symbol snd_ctl_notify
[ 8797.280000] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[ 8797.280000] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[ 8797.280000] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[ 8797.280000] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed

Pairing with my mobile (N95) workes, also sending pictures to and from.
Any ideas?

---

### Post by Blackie_Chan on 2007-10-25
Use the following [http://www.stgraber.org/2007/05/18/bluetooth-headset-manager/](http://www.stgraber.org/2007/05/18/bluetooth-headset-manager/) 

For me it worked like a charm.

---

### Post by plasticM on 2007-11-06
It doesn't work for me either.  :(

Seems like the same problem and I've tried to use Stéphane Graber's gbtsco (as per the link above) but it seemed to have the same problem.

I've posted here to no avail...
[http://ubuntuforums.org/showthread.php?t=602956](http://ubuntuforums.org/showthread.php?t=602956)

---

### Post by nab on 2007-11-06
Hi,

I had the same problem.

Running "sudo hciconfig hci0 reset" after plugging the bluetooth adapter (cc3023) in worked for me.

Nikolaus

---

### Post by Dougle on 2008-02-05
I went straight to blueZ for an answer found it here:
[HOWTO - AudioDevices]("http://wiki.bluez.org/wiki/HOWTO/AudioDevices")

Would love to know if anyone has a quick way to switch a system from speakers to bluetooth via command line, this will be useful for some people to use with bluemon.

Also why do i itch whenever i listen to my headphones? :confused:

---

