---
title: "Really strange wlan0 error... please help!"
date: 2005-12-14
forum: General Help
---

### Post by tomaspineda on 2005-12-14
I can't get my wireless LAN to work after a fresh installation of Ubuntu Breezy. The connection is deactivated on startup (according to GNOME's network applet), and when I activate it, it shows signal (good signal BTW, and it's moving so it's "alive")... but wlan0 still says "Disconnected" and nothing works (not even a simple ping to my gateway).


- my WLAN device is a USB ZD1211, and its driver seems to be pre-installed and working correctly (it appears on lsmod).
- GNOME's Network Settings (network-admin) had some trouble detecting it as wlan0 on first boot, but I used ifconfig to activate it once, and then went back to network-adming to configure its parameters via GUI.
- no I didn't make mistakes with the WEP key or any other data I had to input in network-admin; I checked everything several times.
- I did a iwlist scan and it seems like wlan0 sees my Access Point correctly (with its ESSID) and everything.
- I already deactivated eth0 both in network-admin and /etc/network/interfaces.
- sometimes iwlist channel says my device is working on channel 11 (while the Access Point uses 6), but I can't change it with iwconfig (it says "Invalid argument" no matter what I do)... but eventually it auto-detects channel 6, so I guess that's not the problem.
- pretty much the same happens when I activate the device in the commandline (with ifconfig ) instead of graphically (via network-admin).

Well that's it. I really hope someone can help me, because it's the strangest error I've ever seen (everything seems to work, but it doesn't!), and I haven't read anything like this, anywhere (and believe me, I've searched more than enough).

Thanks in advance!

Tomas Pineda
[email]tomas.pineda@gmail.com[/email]

PS: sorry for the double post, but I didn't know which forum was the right one.

---

### Post by Mr. Electric Wizard on 2005-12-14
You totally need to install the new GTKwifi app.
There is a thread on the front page of the forums under "Third Party Projects".
It tells you how to download and install this app.

BTW, I could never get my wifi to work either with the built in Networking section of Ubundtu.
This app cured my problems...

---

### Post by Dr. Nick on 2005-12-14
I would think it was a /etc/network/interfaces problem, but If you set it like it should I dont know.I had a similar problem using ndiswrapper since ubuntu had a native driver for mine, I just didnt want it, I had to move the driver out of the /kernel/drivers folder to keep it from booting.

What happens when you run **sudo dhclient wlan0 **Mine used to change signal stregnth but didnt have an Ip until I ran that

---

