---
title: "Desktop panels not showing, Desktop/Windows fonts mixed and poor resolution"
date: 2015-07-07
forum: Desktop Environments
---

### Post by Jonners59 on 2015-07-07
OK, this seems a lot, screenshot attached.
[ATTACH=CONFIG]263076[/ATTACH]
You'll note that:
1. The image is not clear, it is rather "broken" and has a strange sheen.
2. All my panels have gone.
3. Also AbiWord opens on boot, and I have not set it to do so, nor is it in the session start up...!?!

I have tried all the settings tools I know such as NVIDIA settings, Desktop right click settings.  Not touched xConf settings as I don't understand it and I can't read it in present condition.

Tried this, but it does nothing...  ```
rm -R ~/.cache/sessions/*
```

Log File has this...?

[PHP]Jul  8 07:28:48 Baroni-PC lightdm[1822]: /etc/modprobe.d is not a file
Jul  8 07:28:48 Baroni-PC freshclam[865]: daily.cld updated (version: 20661, sigs: 1467359, f-level: 63, builder: jesler)
Jul  8 07:28:48 Baroni-PC freshclam[865]: bytecode.cld is up to date (version: 262, sigs: 49, f-level: 63, builder: anvilleg)
Jul  8 07:28:49 Baroni-PC systemd[1]: lightdm.service: main process exited, code=exited, status=1/FAILURE
Jul  8 07:28:49 Baroni-PC systemd[1]: Unit lightdm.service entered failed state.
Jul  8 07:28:49 Baroni-PC systemd[1]: lightdm.service failed.
Jul  8 07:28:49 Baroni-PC systemd[1]: lightdm.service holdoff time over, scheduling restart.
Jul  8 07:28:49 Baroni-PC systemd[1]: Starting Detect the available GPUs and deal with any system changes...
Jul  8 07:28:49 Baroni-PC gpu-manager[1896]: /etc/modprobe.d is not a file
Jul  8 07:28:49 Baroni-PC systemd[1]: Started Detect the available GPUs and deal with any system changes.
Jul  8 07:28:49 Baroni-PC systemd[1]: start request repeated too quickly for lightdm.service
Jul  8 07:28:49 Baroni-PC systemd[1]: Failed to start Light Display Manager.
Jul  8 07:28:49 Baroni-PC systemd[1]: Unit lightdm.service entered failed state.
Jul  8 07:28:49 Baroni-PC systemd[1]: lightdm.service failed.
Jul  8 07:28:51 Baroni-PC systemd[1]: Time has been changed
Jul  8 07:28:51 Baroni-PC ntpdate[1285]: step time server 87.124.126.49 offset 0.683025 sec
Jul  8 07:28:51 Baroni-PC systemd[1]: Starting LSB: Start NTP daemon...
Jul  8 07:28:51 Baroni-PC ntp[1947]: * Starting NTP server ntpd
Jul  8 07:28:51 Baroni-PC ntpd[1955]: ntpd 4.2.6p5@1.2349-o Mon Apr 13 17:00:14 UTC 2015 (1)
Jul  8 07:28:51 Baroni-PC ntpd[1956]: proto: precision = 0.183 usec
Jul  8 07:28:51 Baroni-PC ntpd[1956]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Jul  8 07:28:51 Baroni-PC ntpd[1956]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Jul  8 07:28:51 Baroni-PC ntp[1947]: ...done.
Jul  8 07:28:51 Baroni-PC systemd[1]: Started LSB: Start NTP daemon.
Jul  8 07:28:51 Baroni-PC ntpd[1956]: Listen and drop on 1 v6wildcard :: UDP 123
Jul  8 07:28:51 Baroni-PC ntpd[1956]: Listen normally on 2 lo 127.0.0.1 UDP 123[/PHP]

```
ls -l /home/baronipc/.config
```

[PHP]total 264
drwx------  3 baronipc root      4096 Jul  7 20:22 abiword
drwxrwxr-x  2 baronipc baronipc  4096 Jul  7 20:22 autostart
drwxrwxr-x  2 baronipc baronipc  4096 May 13 18:25 brasero
drwxrwxr-x  7 baronipc baronipc  4096 Jul  7 20:22 chromium
drwxr-xr-x  3 baronipc baronipc  4096 Jun 11 15:14 cinnamon-session
drwxrwxr-x  3 baronipc baronipc  4096 May 13 19:14 compiz-1
drwxrwxr-x  2 baronipc baronipc  4096 Jul  7 20:20 dconf
drwxrwxr-x  2 baronipc baronipc  4096 May 13 18:25 Empathy
drwx------  2 baronipc root      4096 Jun 26 14:43 enchant
drwxrwxr-x  9 baronipc baronipc  4096 Jun 26 14:41 evolution
drwxrwxr-x  2 baronipc baronipc  4096 May 13 20:36 Flavio Tordini
drwxrwxr-x  3 baronipc baronipc  4096 May 14 11:13 folder-color
drwxrwxr-x  2 baronipc baronipc  4096 Jul  1 16:52 FreetuxTV
drwxrwxr-x  3 baronipc baronipc  4096 May 25 08:44 gedit
drwxrwxr-x  2 baronipc baronipc  4096 Jun  8 14:31 gfax
drwx------  2 baronipc baronipc  4096 Jun 25 10:47 globaltime
drwx------  3 baronipc baronipc  4096 Jun 11 15:26 gnome-control-center
drwxr-xr-x  3 baronipc baronipc  4096 Jun 11 15:25 gnome-session
drwxr-xr-x  2 baronipc baronipc  4096 Jun  8 14:42 goa-1.0
drwxrwxr-x  8 baronipc baronipc  4096 Jul  4 11:20 google-chrome
drwxrwxr-x  2 baronipc baronipc  4096 Jun 11 13:32 google-tasks-indicator
drwxrwxr-x  2 baronipc baronipc  4096 Jul  7 20:41 gtk-2.0
drwxrwxr-x  2 baronipc baronipc  4096 Jul  7 20:01 gtk-3.0
drwxrwxr-x  3 baronipc baronipc  4096 May 14 07:03 ibus
-rw-------  1 baronipc baronipc   174 May 21 18:08 kactivitymanagerdrc
drwxrwxr-x  2 baronipc baronipc  4096 Jun 10 19:50 libaccounts-glib
drwx------  2 baronipc baronipc  4096 Jun 11 15:29 libfm
drwxrwxr-x  3 baronipc baronipc  4096 May 19 11:24 libreoffice
drwx------  3 baronipc baronipc  4096 Jun 11 15:28 lxpanel
drwxrwxr-x  3 baronipc baronipc  4096 Jun 11 15:28 lxsession
drwxrwxr-x  8 baronipc baronipc  4096 May 14 14:55 menus
-rw-rw-r--  1 baronipc baronipc  4079 Jun 29 16:10 mimeapps.list
drwxrwxr-x  2 baronipc baronipc  4096 May 13 18:24 nautilus
drwxrwxr-x  2 baronipc baronipc  4096 May 13 18:24 nautilus-actions
-rw-rw-r--  1 baronipc baronipc   126 May 14 19:39 nautilus-compare.conf
drwxr-xr-x  2 baronipc baronipc  4096 Jun 11 15:25 nemo
drwxrwxr-x  2 baronipc baronipc  4096 Jun 19 21:38 openbox
drwxrwxr-x  2 baronipc baronipc  4096 May 14 12:50 orage
-rw-rw-r--  1 baronipc baronipc    31 Jun 29 17:32 pavucontrol.ini
drwxrwxr-x  4 baronipc baronipc  4096 Jun 11 15:28 pcmanfm
drwx------  2 baronipc baronipc  4096 May 13 17:39 pulse
drwxrwxr-x  2 baronipc baronipc  4096 May 13 18:25 qBittorrent
drwxrwxr-x  3 baronipc baronipc  4096 May 13 18:24 qupzilla
drwx------  2 baronipc baronipc  4096 May 22 07:58 ristretto
drwxrwxr-x  9 baronipc baronipc  4096 May 13 18:25 screenlets
drwxrwx--x  2 baronipc baronipc  4096 Jul  5 09:53 signond
drwxrwxr-x  2 baronipc baronipc  4096 May 13 18:25 Skype
drwxrwxr-x  2 baronipc baronipc  4096 Jun 24 09:25 software-center
drwxrwxr-x  2 baronipc baronipc  4096 May 13 17:44 Thunar
drwxrwxr-x  2 baronipc baronipc  4096 May 13 18:25 totem
-rw-rw-r--  1 baronipc baronipc 13437 Jun 19 17:19 Trolltech.conf
drwxrwxr-x 10 baronipc baronipc  4096 May 13 19:16 ubuntu-tweak
drwxr-xr-x  2 baronipc root      4096 May 15 10:17 ubuntu-ui-toolkit
drwxrwxr-x  2 baronipc baronipc  4096 May 13 19:38 update-notifier
drwxrwxr-x  2 baronipc baronipc  4096 May 13 17:39 upstart
-rw-rw-r--  1 baronipc baronipc   365 May 13 19:18 user-dirs.dirs
drwxrwxr-x  2 baronipc baronipc  4096 Jun 20 11:02 VirtualBox
drwxrwxr-x  2 baronipc baronipc  4096 May 13 18:25 vlc
drwxrwxr-x  2 baronipc baronipc  4096 May 13 18:25 webbrowser-app
drwxrwxr-x  2 baronipc baronipc  4096 May 13 18:25 xfburn
drwxrwxr-x  8 baronipc baronipc  4096 Jul  7 20:38 xfce4
drwxrwxr-x  2 baronipc baronipc  4096 May 14 08:40 xfce4-session
drwxrwxr-x  2 baronipc baronipc  4096 Jun  9 11:37 yelp[/PHP]


```
sudo lspci -v -s 01:00.0
```

[HTML]01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device 362b
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at fb000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia[/HTML]

Running NVIDIA 352    [COLOR=#222222][FONT=Verdana][SIZE=2]Installed Drivers: 304.125, 331, 340.76, 346.72, 349.16, 352.21[/SIZE][/FONT][/COLOR] and X-Org X-Server


xUbuntu 15:04     3.19.0-22-generic

```
 sudo update-alternatives --config x86_64-linux-gnu_gl_conf
```
[HTML]There are 3 choices for the alternative x86_64-linux-gnu_gl_conf (providing /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf).

  Selection    Path                                       Priority   Status
------------------------------------------------------------
* 0            /usr/lib/nvidia-352/ld.so.conf              8604      auto mode
  1            /usr/lib/nvidia-352-prime/ld.so.conf        8603      manual mode
  2            /usr/lib/nvidia-352/ld.so.conf              8604      manual mode
  3            /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf   500       manual mode

Press enter to keep the current choice
[*], or type selection number: [/HTML]

 ```
head /proc/meminfo
```
[HTML]MemTotal:       16414560 kB
MemFree:        13791812 kB
MemAvailable:   15377804 kB
Buffers:          151636 kB
Cached:          1605128 kB
SwapCached:            0 kB
Active:          1280448 kB
Inactive:        1098680 kB
Active(anon):     623644 kB
Inactive(anon):    36780 kB[/HTML]

```
head /proc/cpuinfo
```
[HTML]processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
stepping    : 7
microcode    : 0x14
cpu MHz        : 1599.984
cache size    : 6144 KB
physical id    : 0[/HTML]

 ```
sudo dmidecode -t 2
```
[HTML]# dmidecode 2.12
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: P8P67-M PRO
    Version: Rev X.0X
    Serial Number: MT7014018601056
    Asset Tag: To be filled by O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To be filled by O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0[/HTML]

---

### Post by Jonners59 on 2015-07-08
OK, some progress
Fixed Windows text sizes from various standard settings tools.

The panels not showing.  I fixed that from doing the following:


Put a copy on my desktop in case all went wrong.
```
sudo cp -v ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml /home/baronipc/Desktop/
```

Then changed this:
```
gksudo leafpad /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
```
Changed this line from:
<channel name="xfce4-panel" version="1.0">
To:
```
<channel name="xfce4-panel" version="1.0" locked="*" unlocked="root">
```
which locks the panels
I then looked for all the panels and their launch monitors and noticed they still had the old DVI (value="DVI-D-0" and value="DVI-D-1") numbers so I checked my settings in NVIDIA settings and found the one in use was HDMI-0, so I changed all to the new value and rebooted after saving the file....  The panels returned.

[PHP]    <property name="panel-2" type="empty">
      <property name="position" type="string" value="p=8;x=1409;y=1009"/>
      <property name="position-locked" type="bool" value="false"/>
      <property name="plugin-ids" type="array">
        <value type="int" value="8"/>
        <value type="int" value="9"/>
        <value type="int" value="10"/>
        <value type="int" value="12"/>
        <value type="int" value="13"/>
      </property>
      <property name="size" type="uint" value="28"/>
      <property name="output-name" type="string" value="HDMI-0"/>[/PHP]

The panels reappeared after reboot, just tidying them up.

Still have problems with picture/resolution quality.  There is a lack of focus on the characters and a sort of glare that makes it unpleasant to view

I also still have AbiWord launching at boot up and only one of the apps that should launch doing so.

Any help welcome.

---

### Post by Jonners59 on 2015-07-13
As I have solved all the items here except the screen resolution, I am closing this thread as solved and opening a new one, just for the res.

---

