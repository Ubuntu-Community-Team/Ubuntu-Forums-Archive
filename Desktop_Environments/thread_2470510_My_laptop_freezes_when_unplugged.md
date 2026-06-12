---
title: "My laptop freezes when unplugged"
date: 2022-01-02
forum: Desktop Environments
---

### Post by Merrick28 on 2022-01-02
Helo everyone.

First of all, english is not my native language, so please forgive me if I make mistakes...

Here is my issue : my laptop (Asus NoteBook S406U) freezes when it is unplugged from AC. It boots, works for 30s/1 min, then freezes. I cannot do anything, and I have to reboot it manually, or wait a few seconds, and it will reboot. In this state, I cannot do anything, even change the retro-light of the keyboard.
It started approx. on ubuntu 20.04, but does it on 21.04, 21.10

The issue is the same on fedora, but not on Windows (I tried with a livecd)

dmesg|tail gives : 

```
steph@steph-laptop:~$ dmesg | grep -i error
[    1.107491] RAS: Correctable Errors collector initialized.
[    4.321938] EXT4-fs (dm-3): re-mounted. Opts: errors=remount-ro. Quota mode: none.
[    4.814952] Error to get sensor support bitmap
[    4.814958] hwmon-aaeon: probe of hwmon-aaeon.0 failed with error -1
[    5.338048] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    5.338059] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
[    5.338060] pcieport 0000:00:1c.0:   device [8086:9d15] error status/mask=00000001/00002000
[    5.338067] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    5.338074] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    5.338080] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    5.338087] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    5.371750] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    5.371763] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
[    5.371766] pcieport 0000:00:1c.0:   device [8086:9d15] error status/mask=00002001/00002000
[    5.371777] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    5.371786] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    5.371794] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    5.371802] pcieport 0000:00:1c.0: AER: Corrected error received: 0000:00:1c.0
[    7.876470] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    7.876527] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
[    7.876546] pcieport 0000:00:1c.0:   device [8086:9d15] error status/mask=00000081/00002000
[    7.876613] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    7.913474] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
[    7.913530] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
[    7.913547] pcieport 0000:00:1c.0:   device [8086:9d15] error status/mask=00000001/00002000
[    7.913597] pcieport 0000:00:1c.0: AER: Multiple Corrected error received: 0000:00:1c.0
```

When I disable energy management as said here : [https://askubuntu.com/questions/1154207/how-to-disable-all-power-management-in-ubuntu-18-04-lts-via-terminal](https://askubuntu.com/questions/1154207/how-to-disable-all-power-management-in-ubuntu-18-04-lts-via-terminal) I don't have the issue anymore, but I cannot hibernate... 

I tried multiple settings using tlp, but nothing works.

I'd like to find the source of the issue, can someone help me ?

---

