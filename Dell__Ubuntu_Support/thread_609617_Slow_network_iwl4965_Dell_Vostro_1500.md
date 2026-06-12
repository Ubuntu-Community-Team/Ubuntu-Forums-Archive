---
title: "Slow network iwl4965 Dell Vostro 1500"
date: 2007-11-11
forum: Dell  Ubuntu Support
---

### Post by sjaakmans on 2007-11-11
Hello,

I installed today ubuntu gutsy on my dell vostro 1500. But my wireless network is slow.

I can't find on internet the reason, when i run windows it is fast again.

Does somebody know the reason? My max download speed is around 55 kb/s but i need over the 600 kb/s.

Greetings,

Sjaakmans

---

### Post by rocksocke on 2007-11-21
hi!

i think i have the same device in my Vostro 1400. Ubuntu Gutsy 64 bit recognized it without problems. Its working fast and reliable.

```

$ lsmod | grep iwl
iwl4965               113512  0 
iwlwifi_mac80211      200456  1 iwl4965
cfg80211                8720  1 iwlwifi_mac80211

```

what do you get?

unfortunately i still have some minor problems: the wifi-chatcher-led on the laptop's front doesn't blink at all. i'm not sure if 802.11n is working. i tried to  but...:

```

$ iwlist wlan0 bitrate
wlan0     unknown bit-rate information.
          Current Bit Rate:54 Mb/s

```

does anyone know if this is a driver-problem? should i switch to ndiswrapper?

thx for your replies

---

