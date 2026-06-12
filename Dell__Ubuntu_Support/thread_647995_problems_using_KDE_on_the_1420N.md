---
title: "problems using KDE on the 1420N?"
date: 2007-12-23
forum: Dell  Ubuntu Support
---

### Post by gamelord12 on 2007-12-23
I vaguely remember seeing on a Digg.com comment that it was a bad idea to use KDE on the 1420N with Ubuntu, but I don't remember why.  I'm ordering this laptop shortly after Christmas (with nVidia graphics, finally!) and I was just curious whether or not I could use KDE without any problems.  I prefer it over GNOME quite a bit.

---

### Post by neptho on 2007-12-23
I *just* bought the Vostro 1400, which shares most of the hardware in common with the 1420.  It installed without a hitch - I cheaped out and kept the onboard Intel video, but did purchase the Intel 3945 wireless, and the Dell 355 Bluetooth.  It just worked with Kubuntu 7.10/Gutsy.

All I had to do was add the following to /etc/modprobe.d/alsa-base to make audio work:
options snd-hda-intel probe_mask=1 model=3stack

There's absolutely nothing 'wrong' or broken with KDE.  I do recall in Feisty when 3.5.6 was standard, and there was an unofficial 3.5.7 package - that broke several things, but it, itself was broken; it had nothing to do with the machine.

---

### Post by dnvikram on 2007-12-23
I have been using KDE in Gutsy Gibbon on 1420N since many weeks and it absolutely has no problems.Its really smooth and more appealing than Gnome.Go ahead use KDE.I am sure ur gonna love it.

---

### Post by Orion2000za on 2008-01-14
> **neptho said:**
> I *just* bought the Vostro 1400, which shares most of the hardware in common with the 1420.  It installed without a hitch - I cheaped out and kept the onboard Intel video, but did purchase the Intel 3945 wireless, and the Dell 355 Bluetooth.  It just worked with Kubuntu 7.10/Gutsy.

All I had to do was add the following to /etc/modprobe.d/alsa-base to make audio work:
options snd-hda-intel probe_mask=1 model=3stack

There's absolutely nothing 'wrong' or broken with KDE.  I do recall in Feisty when 3.5.6 was standard, and there was an unofficial 3.5.7 package - that broke several things, but it, itself was broken; it had nothing to do with the machine.

I am using Kubuntu 7.10 on a Vostro 1400 with same config and I have two annoying problems and some minor ones:
1. The kernel does not see the modem as it should so can not use it. Booting with a Knoppix liveCD and an earlier kernel can "see" the  modem codec
2. The intel wireless likes to play yo-yo with the connections, going on and off - ipw3945 driver

minor issues: the mute and light up/down buttons don't work

any suggestions will be appreciated

Sinclair

---

### Post by jetpeach on 2008-01-19
i have a 1420n with bluetooth running kubuntu. i find everything works great, except i'm currently trying to get the bluetooth option i chose to work with a bluetooth mouse i bought.
kbluetoothd doesn't recognize the bluetooth adapter by default...

EDIT: turned out this was because the bluetooth option wasn't installed the way Dell said it would be... i called them and they refunded my credit card $100, so i was happy. i bought the internal bluetooth module on ebay for $15 and installed it myself, now my bluetooth mouse works great.

---

### Post by neptho on 2008-01-19
> **Orion2000za said:**
> I am using Kubuntu 7.10 on a Vostro 1400 with same config and I have two annoying problems and some minor ones:
1. The kernel does not see the modem as it should so can not use it. Booting with a Knoppix liveCD and an earlier kernel can "see" the  modem codec
2. The intel wireless likes to play yo-yo with the connections, going on and off - ipw3945 driver

minor issues: the mute and light up/down buttons don't work

any suggestions will be appreciated

Sinclair

#1: I have disabled the software modem driver, because it breaks my audio; the two are mutually exclusive for me; my HDA Intel codec does not work with the modified driver that works with the modem

#2: I had this problem early-on, so I stopped using KNetworkmanager/networkmanager, and launch wpa_supplicant myself for the wireless interface:

/etc/network/interfaces:
auto wlan0
iface wlan0 inet dhcp
pre-up          /etc/init.d/wifi_wpa.sh start
pre-down        /etc/init.d/wifi_wpa.sh stop

/etc/init.d/wifi_wpa.sh:
#!/bin/sh
PATH=/bin:/usr/bin:/sbin:/usr/sbin
BIN=/sbin/wpa_supplicant
PIDFILE=/var/run/wpa_supplicant.pid
. /lib/lsb/init-functions

case "$1" in
  start)
if [ -x /sbin/wpa_supplicant ]; then
 # ifdown wlan0_rename
  killall wpa_supplicant 1&>2 > /dev/null
  sleep 2s
  $BIN -iwlan0 -c /etc/wpa_supplicant.conf -Dwext -w -P $PIDFILE 2>&1 &
fi
    ;;
  stop)
    killall wpa_supplicant 1&>2 > /dev/null
#    ifdown wlan0_rename
    ;;
  *)
    ;;
esac
exit 0

/etc/wpa_supplicant.conf:
network={
        ssid="MY_SSID"
        scan_ssid=1
        psk=(use wpa_passphrase SSID then type code to get psk)
}

I have a much better, 'auto scanning' system on my 6400, but I don't have access to that, now, and this little hack ensures it works whenever I go to sleep.

As far as the buttons, you need to install an updated kmilo - however, the one in Gutsy always toggles index 0 which is PCM, it won't work for the onboard audio.  I had to do some nasty patching to some Hardy sources to some diffs I found on the kde list.  I can't even begin to say how I got it working, but in the end, I removed/turned it off because it was becoming obnoxious with how I had to workaround to make it go.

I've created a thread on how I made the up/down buttons work for the backlight; I'm afraid I don't recall what I named it, however.

---

