---
title: "Lag spikes every minute while playing an fps online (quake live)"
date: 2012-12-03
forum: Gaming &amp; Leisure
---

### Post by kr0n1x on 2012-12-03
Hi, I'm having an issue with connection stability while gaming online.

My card chipset is: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)

First issue (already solved), while playing I lagged a lot, until the server disconnected me (due to inactivity).
Doing ping in terminal would give me pings of SECONDS, multiple pipes... etc.
This wasn't a new issue to me, I had it in past with debian testing.
I solved this by installing compat-wireless (the latest stable release, I only selected and compiled the ath9k driver with the script included).

Now, the only issue which is still present, is that sometimes (every X minutes, I have to time it better, it's like every minute or so) the lagometer (it's a part of fps UIs which shows the stability of the connection, [wikipedia](https://en.wikipedia.org/wiki/Lagometer)) shows red spikes (which is bad, normally it's green) and I get very bad lag. It stays like this for like 2-3 seconds then the connection returns normal and the lagometer shows only the green bar.

Wikipedia says: "Red bars mean that the frame has not arrived on time"
I would interpret this behaviour as packet loss...

The first thing to check would be to close all the applications, right? But I don't have incons in my system tray. I should check with terminal, but I don't know how.

Is there a way to check what happens to my network while I play? Like some logs... So I can analyze what happens in my pc when those red spikes happen in my lagometer... maybe there's some application using my connection in background.

Thanks

EDIT: adding screens for when it is [STABLE](http://imageshack.us/a/img803/9089/shot0004v.jpg) and when it is [LAGGING](http://imageshack.us/a/img534/1017/shot0006ay.jpg).

---

