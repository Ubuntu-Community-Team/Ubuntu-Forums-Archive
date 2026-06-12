---
title: "Dell Bluetooth Headset BH200 + Hardy. How?"
date: 2008-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bengtt on 2008-06-06
Hi

I have an XPS M1330 with a Dell Bluetooth headset BH200, and just can not get it to work. Or have I missed something?

I have managed to pair it with Hardy. At least the Bluetooth preferences indicates that I have bounded with the BH200 device.

I tried to follow this link [http://wiki.ubuntuusers.de/Bluetooth_Headset](http://wiki.ubuntuusers.de/Bluetooth_Headset) but my german is not really up to speed.
Also looked at this one.[http://gentoo-wiki.com/HOWTO_use_a_bluetooth_headset](http://gentoo-wiki.com/HOWTO_use_a_bluetooth_headset)

My ~/.asoundrc contains the following
pcm.bluetooth {
   type bluetooth
   device 00:16:44:20:97:19
}

My /etc/bluetooth/audio.conf contains the following
[Bluetooth Service]
Identifier=audio
Name=Audio service
Description=Bluetooth Audio service
Autostart=true

My /etc/bluetooth/audio.service contains the following
[Bluetooth Service]
Identifier=audio
Name=Audio service
Description=Bluetooth Audio service
Autostart=true

"hcitool scan" only finds the device when I am trying to pair it, not otherwise.

Some extract from my messages log
Jun  6 14:19:18 lappis NetworkManager: <debug> [1212740358.207008] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_1644209719'). 
Jun  6 14:19:19 lappis hcid[11025]: link_key_request (sba=00:1E:4C:DC:E3:22, dba=00:16:44:20:97:19)
Jun  6 14:19:19 lappis hcid[11025]: pin_code_request (sba=00:1E:4C:DC:E3:22, dba=00:16:44:20:97:19)
Jun  6 14:19:25 lappis hcid[11025]: link_key_notify (sba=00:1E:4C:DC:E3:22, dba=00:16:44:20:97:19)
Jun  6 14:19:29 lappis NetworkManager: <debug> [1212740369.608516] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_1644209719'). 
Jun  6 14:20:33 lappis input[11033]: /org/bluez/input: org.bluez.input.Manager.CreateSecureDevice()
Jun  6 14:20:33 lappis NetworkManager: <debug> [1212740433.215111] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_1644209719'). 
Jun  6 14:20:36 lappis hcid[11025]: link_key_request (sba=00:1E:4C:DC:E3:22, dba=00:16:44:20:97:19)
Jun  6 14:20:36 lappis input[11033]: Created input device: /org/bluez/input/wearable0
Jun  6 14:20:36 lappis input[11033]: /org/bluez/input/wearable0: org.bluez.input.Device.GetAdapter()
Jun  6 14:20:36 lappis input[11033]: /org/bluez/input/wearable0: org.bluez.input.Device.GetAddress()
Jun  6 14:20:36 lappis input[11033]: /org/bluez/input/wearable0: org.bluez.input.Device.GetName()
Jun  6 14:20:36 lappis input[11033]: /org/bluez/input/wearable0: org.bluez.input.Device.GetAdapter()
Jun  6 14:20:36 lappis input[11033]: /org/bluez/input/wearable0: org.bluez.input.Device.GetAddress()
Jun  6 14:20:36 lappis input[11033]: /org/bluez/input/wearable0: org.bluez.input.Device.GetName()
Jun  6 14:20:40 lappis NetworkManager: <debug> [1212740440.507742] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_1644209719'). 
Jun  6 14:20:58 lappis input[11033]: /org/bluez/input: org.bluez.input.Manager.RemoveDevice()
Jun  6 14:21:00 lappis audio[11034]: Unregistered manager path
Jun  6 14:21:00 lappis audio[11034]: Exit
Jun  6 14:21:01 lappis audio[12271]: Bluetooth Audio daemon
Jun  6 14:21:01 lappis audio[12271]: Unix socket created: 5
Jun  6 14:21:01 lappis audio[12271]: audio.conf: Key file does not have key 'Enable'
Jun  6 14:21:01 lappis audio[12271]: audio.conf: Key file does not have key 'Disable'
Jun  6 14:21:01 lappis audio[12271]: add_service_record: got record id 0x10000
Jun  6 14:21:01 lappis audio[12271]: audio.conf: Key file does not have key 'Disable'
Jun  6 14:21:01 lappis audio[12271]: audio.conf: Key file does not have group 'A2DP'
Jun  6 14:21:01 lappis last message repeated 3 times
Jun  6 14:21:01 lappis audio[12271]: SEP 0x806d3e0 registered: type:0 codec:0 seid:1
Jun  6 14:21:01 lappis audio[12271]: add_service_record: got record id 0x10001
Jun  6 14:21:01 lappis audio[12271]: add_service_record: got record id 0x10002
Jun  6 14:21:01 lappis audio[12271]: add_service_record: got record id 0x10003
Jun  6 14:21:01 lappis audio[12271]: Registered manager path:/org/bluez/audio

---

### Post by Nergar on 2008-08-12
Having the same problem here, any help is appreciated

---

