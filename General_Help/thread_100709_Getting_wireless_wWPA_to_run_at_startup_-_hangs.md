---
title: "Getting wireless w/WPA to run at startup - hangs"
date: 2005-12-08
forum: General Help
---

### Post by mappy24 on 2005-12-08
Hi,

I have just installed Ubuntu from DVD onto my Sony Vaio and configured WPA following the instructions on this page: [https://wiki.ubuntu.com//WPAHowto](https://wiki.ubuntu.com//WPAHowto)

All went well, I can run the wpasupplicant manually and get a wireless connection no problem.

I have an issue with the "Final Installation" section though.

The instructions state that I should modify my etc/network/interfaces file, it currently looks like this:

auto eth0
iface eth0 inet dhcp
pre-up /etc/init.d/wpasupplicant start
pre-up sleep 5

Also, I have edited my /etc/default/wpasupplicant file to look like this:

ENABLED=1
OPTIONS="-ieth0 -c/etc/wpa_supplicant.conf -Dipw"

My wpasupplicant.conf looks like this:

network={
        ssid="Maggie"
        proto=WPA
        key_mgmt=WPA-PSK
        psk="............"
}

When I restart my laptop it boots OK and gives me a login screen.  When I log in I get the mouse cursor on a blank background and then nothing else, it just stays like that and never gives me the desktop.

I commented out the two "pre-up" lines from etc/default/wpasupplicant and it loads absolutely fine.

Can anyone help?

Thanks
Ian

---

### Post by mappy24 on 2005-12-09
Got it working by re-installing, never mind!

---

