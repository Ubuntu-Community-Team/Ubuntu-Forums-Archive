---
title: "Ubuntu desktop 20.04 LTS screen doesn't wake after going to sleep"
date: 2021-01-02
forum: Desktop Environments
---

### Post by luke-plausin on 2021-01-02
I'm having an issue with Ubuntu desktop 20.04 where my screen won't switch on after going to sleep. When I press a key to wake the system up after the screensaver it doesn't come back for some reason. The problem seems intermittent, when I press the power button on the screen it doesn't show the OSD message (so there is a signal) but the screen is completely blank. If I leave it for a few minutes, the signal will disappear and then the OSD message comes back. If I power the screen on first and then press a key on the keyboard, the login page will show about 50% of the time. Sometimes pressing the power key will help. When the display is malfunctioning I cannot bring up the terminal with CTRL + ALT + F3.

I'm using an external monitor connected by HDMI, and an Nvidia graphics  card (the drivers all seem to be set up correctly). I actually noticed  this problem with onboard graphics (before installing the nvidia card)  so I don't think it's driver related.
I noticed that there are some apparmor denials the dmesg log  on /org/freedesktop/ paths around the same time (are these related)? I don't know very much about apparmor so would appreciate some guidance there. I'm not using any custom apparmor profiles.

Thanks :-)

```

# dmesg log
[  288.854836] audit: type=1400 audit(1609595950.565:89): apparmor="DENIED" operation="capable" profile="/snap/snapd/10492/usr/lib/snapd/snap-confine" pid=2836 comm="snap-confine" capability=4  capname="fsetid"
[  290.107404] audit: type=1326 audit(1609595951.817:90): auid=1000 uid=1000 gid=1000 ses=4 pid=2836 comm="snap-store" exe="/snap/snap-store/518/usr/bin/snap-store" sig=0 arch=c000003e syscall=314 compat=0 ip=0x7f4bff739639 code=0x50000
[  290.370340] audit: type=1107 audit(1609595952.077:91): pid=759 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/NetworkManager" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.13" pid=2836 label="snap.snap-store.ubuntu-software" peer_pid=761 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
[  290.887571] audit: type=1107 audit(1609595952.597:92): pid=759 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.11" pid=2836 label="snap.snap-store.ubuntu-software" peer_pid=782 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
[  290.887979] audit: type=1107 audit(1609595952.597:93): pid=759 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.11" pid=2836 label="snap.snap-store.ubuntu-software" peer_pid=782 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
[  290.909562] audit: type=1107 audit(1609595952.617:94): pid=759 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.11" pid=2836 label="snap.snap-store.ubuntu-software" peer_pid=782 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
[  290.909914] audit: type=1107 audit(1609595952.617:95): pid=759 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.11" pid=2836 label="snap.snap-store.ubuntu-software" peer_pid=782 peer_label="unconfined"
                exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
[  291.197614] audit: type=1400 audit(1609595952.905:96): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/etc/PackageKit/Vendor.conf" pid=2836 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  298.196733] audit: type=1400 audit(1609595959.905:97): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/gdm/greeter/applications/gnome-initial-setup.desktop" pid=2836 comm="pool-org.gnome." requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  298.219801] audit: type=1400 audit(1609595959.929:98): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/gdm/greeter/applications/gnome-initial-setup.desktop" pid=2836 comm="pool-org.gnome." requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


# Graphics driver info
$ nvidia-smi
Sat Jan  2 14:33:26 2021       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 460.27.04    Driver Version: 460.27.04    CUDA Version: 11.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  GeForce GTX 105...  On   | 00000000:10:00.0  On |                  N/A |
| 35%   32C    P5    N/A /  75W |    480MiB /  4006MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1099      G   /usr/lib/xorg/Xorg                101MiB |
|    0   N/A  N/A      2429      G   /usr/lib/xorg/Xorg                254MiB |
|    0   N/A  N/A      2564      G   /usr/bin/gnome-shell              108MiB |
|    0   N/A  N/A      3854      G   /usr/lib/firefox/firefox            1MiB |
|    0   N/A  N/A      5364      G   /usr/lib/firefox/firefox            1MiB |
+-----------------------------------------------------------------------------+

```

---

### Post by pushbike06 on 2021-01-02
Hi, You haven't stated how you enter sleep mode.
I can only say that I use a keyboard initiated sleep mode. This apparently saves my work environment, logs out and powers down.
This sleep mode is signaled by the PC power on button/lamp pulsing.
To return to use I press the PC power on button which produces, directly, the log on screen and every thing I was doing is restored. Mind I usually shut down all aps etc. before hitting sleep.
Some keyboards don't have a sleep button and there are apparently some keystrokes do put the PC to sleep. You can also use the Suspend option on Desktop power dropdown, seems to do the same as the keyboard key, for me it's easier to use the keyboard button.

---

### Post by luke-plausin on 2021-01-03
Ah I should have said - this happens either when I lock the screen with System + L, or if I allow the screen to go dim through inactivity. It's the "lock screen", not sleep mode

---

### Post by luke-plausin on 2021-01-03
I followed some advice for fixing apparmor issues on another thread. It looks like my system was somehow missing the "apparmor-profiles" apt package.
I ran these commands and didn't have the problem since (at least not yet).

```

sudo apt install apparmor-profiles
sudo apparmor_status
sudo systemctl reload apparmor.service

```

---

