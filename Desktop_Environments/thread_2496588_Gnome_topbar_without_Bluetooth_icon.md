---
title: "Gnome topbar without Bluetooth icon"
date: 2024-04-04
forum: Desktop Environments
---

### Post by Freiklite on 2024-04-04
Hi,
I use Mantic Minautor on a 14s-fq hp laptop.
My Q.live 1242 wireless earphones are not detected.
No bluetooth icon in the  right topbar.

A few details;
```
$ uname -a; lspci -nnk | grep -iA3 net; lsusb; sudo dmesg | grep -i bluetooth; sudo dmesg | grep -i firmware; lsmod | grep bluetooth
Linux tinnitus-HP-Laptop-14s-fq0xxx 6.5.0-26-generic #26-Ubuntu SMP PREEMPT_DYNAMIC Tue Mar  5 21:19:28 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
    DeviceName: Realtek Wireless LAN + BT
    Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]
    Kernel driver in use: rtw_8821ce
    Kernel modules: rtw88_8821ce
02:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller 980 [144d:a809]
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b00a Realtek Semiconductor Corp. Realtek Bluetooth 4.2 Adapter
Bus 001 Device 003: ID 0408:5365 Quanta Computer, Inc. HP TrueVision HD Camera
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[sudo] Mot de passe de tinnitus : 
[ 3348.100607] rtw_8821ce 0000:01:00.0: firmware failed to leave lps state
[ 3349.992567] rtw_8821ce 0000:01:00.0: firmware failed to leave lps state
[ 3351.976447] rtw_8821ce 0000:01:00.0: firmware failed to leave lps state
[ 4340.964598] rtw_8821ce 0000:01:00.0: firmware failed to leave lps state
[ 4342.948586] rtw_8821ce 0000:01:00.0: firmware failed to leave lps state
bluetooth            1077248  44 btrtl,btmtk,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           16384  2 bluetooth

```
```
$ dpkg -l | grep blue
ii  bluez                                          5.68-0ubuntu1.1                         amd64        Bluetooth tools and daemons
ii  bluez-alsa-utils                               4.0.0-2                                 amd64        Bluetooth Audio ALSA Backend (utils)
ii  bluez-btsco                                    1:0.50-0ubuntu7                         amd64        Bluez Bluetooth SCO tool
ii  bluez-cups                                     5.68-0ubuntu1.1                         amd64        Bluetooth printer driver for CUPS
ii  bluez-firmware                                 1.2-9                                   all          Firmware for Bluetooth devices
ii  bluez-hcidump                                  5.68-0ubuntu1.1                         amd64        Analyses Bluetooth HCI packets
ii  bluez-meshd                                    5.68-0ubuntu1.1                         amd64        bluetooth mesh daemon
ii  bluez-obexd                                    5.68-0ubuntu1.1                         amd64        bluez obex daemon
ii  bluez-tests                                    5.68-0ubuntu1.1                         amd64        BlueZ test tools and scripts
ii  bluez-tools                                    2.0~20170911.0.7cb788c-4                amd64        Set of tools to manage Bluetooth devices for linux
ii  gir1.2-gnomebluetooth-3.0:amd64                42.6-1                                  amd64        Introspection data for GnomeBluetooth
ii  gnome-bluetooth-3-common                       42.6-1                                  all          GNOME Bluetooth 3 common files
ii  libasound2-plugin-bluez:amd64                  4.0.0-2                                 amd64        Bluetooth Audio ALSA Backend (plugins)
ii  libbluetooth3:amd64                            5.68-0ubuntu1.1                         amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth-3.0-13:amd64                42.6-1                                  amd64        GNOME Bluetooth 3 support library
ii  libgnome-bluetooth-ui-3.0-13:amd64             42.6-1                                  amd64        GNOME Bluetooth 3 UI support library
ii  libspa-0.2-bluetooth:amd64                     0.3.79-2                                amd64        libraries for the PipeWire multimedia server - bluetooth plugins

```
```
$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
```
$ sudo service bluetooth status | cat
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; preset: enabled)
     Active: active (running) since Thu 2024-04-04 21:45:57 CEST; 1h 18min ago
       Docs: man:bluetoothd(8)
   Main PID: 815 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 8670)
     Memory: 2.3M
        CPU: 243ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;815 /usr/lib/bluetooth/bluetoothd

avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/aptx_ll_1
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/aptx_ll_0
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/aptx_ll_duplex_1
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/aptx_ll_duplex_0
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/faststream
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/faststream_duplex
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSink/opus_05
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/opus_05
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSink/opus_05_duplex
avril 04 21:46:27 tinnitus-HP-Laptop-14s-fq0xxx bluetoothd[815]: Endpoint registered: sender=:1.95 path=/MediaEndpoint/A2DPSource/opus_05_duplex

```

Thank you for your attention and suggestions,
Ciao

---

### Post by jeremy31 on 2024-04-05
Thread closed duplicate at [https://ubuntuforums.org/showthread.php?t=2496613&p=14184607#post14184607](https://ubuntuforums.org/showthread.php?t=2496613&p=14184607#post14184607)

---

