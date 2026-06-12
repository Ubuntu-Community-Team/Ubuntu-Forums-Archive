---
title: "No gui to scan for wireless cells in 8.10?"
date: 2009-01-01
forum: Desktop Environments
---

### Post by dr. mario on 2009-01-01
Something is weird because as soon as I upgraded to 8.10, I lost my ability to scan wlan0 for wireless cells within the gui. I used to be able to press the gnome-netstatus applet and it would show which network I am connected to and let me scan for more. I know that Ubuntu updated the network configuration because it now connects on startup automatically. (which I like) I also looked within the system preferences for network. iwlist still works in cli.

---

### Post by stderr on 2009-01-01
TBH, I've always had trouble with wireless networking on Ubuntu. I never take the time to figure it out, and most of my boxes are on ethernet connections anyway, and I've only got the one laptop.

It seems that every copy of Ubuntu I install for other people has pretty nice GUIs for that sort of thing by default; mine never has though ;) From your post, I reckon I must have been missing gnome-netstatus.

However, wifi-radar tends to work OK for me. It's not a default GNOME utility, but it works pretty well.

```
sudo apt-get install wifi-radar
```

---

### Post by zingbats on 2009-01-07
The trouble with wifi-radar, is it doesn't connect on an N channel, if there's b or g avaliable. My router broadcasts B,G and N and it always connects via B.

Alas, as a wireless scanner it doesn't act too badly.

Lord only knows why Ubuntu dropped the wifi-scanning function in Network Connections.

---

