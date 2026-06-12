---
title: "Startup failures every other attempt"
date: 2009-02-21
forum: General Help
---

### Post by dreamingdarkness on 2009-02-21
Something weird started happening with my laptop with my laptop during booting.
[Update: I'm starting to think this may be an issue with the wireless startup, considering the step at which it fails. But can anyone confirm that?]


If the laptop was fully shut down and attempt to boot Ubuntu from GRUB it freezes, blackscreen. I've tried alt-F1 but the boot text ends abruptly in a black screen. I have to reboot by holding the power button down and starting over. The reboot is successful and I can get into Ubuntu. 

The only info I've really found that indicates what ends up not starting is by checking /var/log/messages

From an aborted/failed boot:
```
Feb 21 00:47:31 ubuntu kernel: [   25.674227] Bluetooth: RFCOMM socket layer initialized
Feb 21 00:47:31 ubuntu kernel: [   25.675312] Bluetooth: RFCOMM TTY layer initialized
Feb 21 00:47:31 ubuntu kernel: [   25.675324] Bluetooth: RFCOMM ver 1.10
Feb 21 00:51:44 ubuntu syslogd 1.5.0#2ubuntu6: restart.
```


From a completed boot, immediately following the failed attempt:
```

Feb 21 00:51:50 ubuntu kernel: [   29.734162] Bluetooth: RFCOMM socket layer initialized
Feb 21 00:51:50 ubuntu kernel: [   29.734187] Bluetooth: RFCOMM TTY layer initialized
Feb 21 00:51:50 ubuntu kernel: [   29.734192] Bluetooth: RFCOMM ver 1.10
Feb 21 00:51:58 ubuntu kernel: [   34.537444] r8169: eth0: link down
Feb 21 00:51:58 ubuntu kernel: [   34.538130] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 21 00:51:58 ubuntu kernel: [   34.538673] firmware: requesting iwlwifi-5000-1.ucode
Feb 21 00:51:58 ubuntu kernel: [   37.999668] Registered led device: iwl-phy0:radio
Feb 21 00:51:58 ubuntu kernel: [   37.999685] Registered led device: iwl-phy0:assoc
Feb 21 00:51:58 ubuntu kernel: [   37.999703] Registered led device: iwl-phy0:RX
Feb 21 00:51:58 ubuntu kernel: [   37.999719] Registered led device: iwl-phy0:TX
```


And the final moments of the failed startup from /var/log/daemon.log
```
Feb 21 00:47:35 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Feb 21 00:47:35 ubuntu NetworkManager: <info>  (eth0): bringing up device. 
Feb 21 00:47:35 ubuntu NetworkManager: <info>  (eth0): preparing device. 
Feb 21 00:47:35 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Feb 21 00:47:35 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Feb 21 00:47:35 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Feb 21 00:47:35 ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Feb 21 00:47:35 ubuntu NetworkManager: <info>  (wlan0): bringing up device. 
```

On the successful boots, this goes more like: 
```
Feb 21 00:51:55 ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Feb 21 00:51:55 ubuntu NetworkManager: <info>  (wlan0): bringing up device. 
Feb 21 00:51:58 ubuntu NetworkManager: <info>  (wlan0): preparing device. 
Feb 21 00:51:58 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
```

---

