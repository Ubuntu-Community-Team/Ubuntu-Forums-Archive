---
title: "Multitude of problems with Gnome3 -- Empathy, keyboard, VLC, brightness, sound, Bansh"
date: 2011-05-29
forum: Desktop Environments
---

### Post by maverick280857 on 2011-05-29
Hi,

I am (happily) running Ubuntu 11.04 64-bit on my Dell XPS 15 L501X laptop (Core i7 740 QM CPU, 6 GB DD3 SDRAM, NVIDIA GT435M graphics). I have been using Gnome3 for about 2 weeks now. But of late I have been having some problems, which I have listed below.

1. Once I exit Empathy, it doesn't log back into my google account unless I reboot the system. I use wicd to connect to my wireless (don't have network-manager, and have already configured empathy not to use network-manager to determine the network status).

2. [B]My keyboard (except the function keys) stops working randomly, requiring me to log out and log back in again. This does not happen with any specific application though.
[/B]
3. VLC always crashes the FIRST time it is started and any video is loaded in it. It works fine the second time.

4. The laptop screen brightness setting gets reset frequently and the brightness gets turned up automatically.

5. Sound sometimes doesn't work, until I reboot the system.

6. **Touchpad becomes unresponsive sometimes, but the external mouse works (this is a fairly recent occurrence).**

I'd appreciate any inputs on how to fix these problems. Personally I haven't been able to locate their sources yet.

---

### Post by rockorequin on 2011-05-29
> **maverick280857 said:**
> Hi,

I am (happily) running Ubuntu 11.04 64-bit on my Dell XPS 15 L501X laptop (Core i7 740 QM CPU, 6 GB DD3 SDRAM, NVIDIA GT435M graphics). I have been using Gnome3 for about 2 weeks now. But of late I have been having some problems, which I have listed below.

1. Once I exit Empathy, it doesn't log back into my google account unless I reboot the system. I use wicd to connect to my wireless (don't have network-manager, and have already configured empathy not to use network-manager to determine the network status).

2. My keyboard (except the function keys) stops working randomly, requiring me to log out and log back in again. This does not happen with any specific application though.

3. VLC always crashes the FIRST time it is started and any video is loaded in it. It works fine the second time.

4. The laptop screen brightness setting gets reset frequently and the brightness gets turned up automatically.

5. Banshee stops working randomly: when I click play, nothing happens.

6. Sound sometimes doesn't work, until I reboot the system.

7. Touchpad becomes unresponsive sometimes, but the external mouse works (this is a fairly recent occurrence).

I'd appreciate any inputs on how to fix these problems. Personally I haven't been able to locate their sources yet.

If sound breaks, you could try "pulseaudio -k". It kills pulseaudio which should autorestart.

Is there any chance you might be turning off the touchpad by accident? (FN-F3 on my L502x.) This caught me out for a while.

---

### Post by maverick280857 on 2011-05-29
> **rockorequin said:**
> If sound breaks, you could try "pulseaudio -k". It kills pulseaudio which should autorestart.

Will try this

[QUOTE=rockorequin]Is there any chance you might be turning off the touchpad by accident? (FN-F3 on my L502x.) This caught me out for a while.[/QUOTE]

Ah no, I checked that -- I am not pressing the Fn+F13 key (on my laptop, it is the key next to F12). If left idle, it becomes completely unresponsive and very sluggish. Could it be powering off somehow?

---

### Post by maverick280857 on 2011-05-29
> **rockorequin said:**
> If sound breaks, you could try "pulseaudio -k". It kills pulseaudio which should autorestart.

When my sound stopped working a few minutes ago, I tried this command. I got an error message saying 'main.c: ...." (unfortunately I didn't have the presence of mind then to copy past it here..argh). The daemon sure got killed, but it also muted my speaker permanently in gnome3. Then, I wasn't able to unmute the speaker from the audio notifier icon in gnome shell. Only a reboot helped.

---

### Post by maverick280857 on 2011-05-29
The touchpad is VERY sluggish of late, and quite often I have to briskly move my finger on it to make it work. It always seems to be stuck as if it has been turned off while not in use.

EDIT: Trying

```
sudo apt-get install gpointing-device-settings
```

[https://live.gnome.org/GPointingDeviceSettings](https://live.gnome.org/GPointingDeviceSettings)

---

### Post by maverick280857 on 2011-05-29
Is there any separate power setting for the touchpad?

---

### Post by maverick280857 on 2011-05-30
I've been able to re-enable the touchpad by installing the touchpad-indicator:

```

sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator

```

On starting touchpad-indicator, I found my touchpad was disabled.

References:

1. [https://help.ubuntu.com/community/SynapticsTouchpad#Using%20Touchpad-Indicator](https://help.ubuntu.com/community/SynapticsTouchpad#Using%20Touchpad-Indicator)

2. [http://www.webupd8.org/2011/02/my-weather-indicator-020-released-new.html](http://www.webupd8.org/2011/02/my-weather-indicator-020-released-new.html)

Note: The repository mentioned in link 1 did not work for me, so I used the one mentioned in link 2, which I had used for my-weather-indicator.

---

