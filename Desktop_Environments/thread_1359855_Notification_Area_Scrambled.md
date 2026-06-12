---
title: "Notification Area Scrambled"
date: 2009-12-20
forum: Desktop Environments
---

### Post by siabost on 2009-12-20
Hi,

Ubuntu 9.10 Desktop.

My "notification area" keeps getting scrambled between boots (pic attached).

If I remove the notification area & then add it back in it looks fine but is then scrambled again the next time the system is booted up.
The icons affected are usually the volume (sometimes I have two, or one and a half) & the wlan icon (which usually disappears).

Any ideas?

It's more of a minor nuisance than anything serious but I'd like to get it fixed.

Much ta.

---

### Post by siabost on 2009-12-23
Anybody...?

O:)

---

### Post by h0ser81 on 2010-01-07
I have the exact same problem. Anyone have any idea what causes this?

---

### Post by SecretCode on 2010-01-07
OK, I have the same problem too. I thought it was a one-off thing but it's now persisted for two boots. Only the network manager icon and the audacious (music player) icon are affected, others are fine.

As for the OP, removing the notification applet and adding it back fixes it.

These bugs may be applicable: [Bug #444333 in network-manager-applet (Ubuntu): &#8220;nm-applet shows as unresponsive black box&#8221;](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/444333) - [Bug #446093 in network-manager (Ubuntu): &#8220;nm-applet loaded, but icon not visible (karmic)&#8221;](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/446093)

---

### Post by nikkkko on 2010-02-13
I've searched a little bit because I have the same problem and we are not alone.  My network icon gets scrambled with the volume icon.  Not really a big problem but pretty annoying.

---

### Post by linux4me on 2010-02-13
Have you got "lock to panel" selected for the affected icons?

---

### Post by SecretCode on 2010-02-13
In my case the notification area applet is not locked to the panel. (It's one applet - you can't lock individual icons within it.)

---

### Post by linux4me on 2010-02-13
> **SecretCode said:**
> In my case the notification area applet is not locked to the panel. (It's one applet - you can't lock individual icons within it.)

I see. Does it happen with the default theme and with open source as well as restricted video drivers?

---

### Post by SecretCode on 2010-02-13
It's not happening **at all** for me at the moment, so I can't answer that.

---

### Post by nikkkko on 2010-02-13
> I see. Does it happen with the default theme and with open source as well as restricted video drivers?

Default theme and NVidia driver

---

### Post by siabost on 2010-02-13
Hi,

Strangely mine seems to have stopped doing it! I have made no changes other than applying the official updates as they arrive.

I also use nVidia driver & default theme.

---

### Post by Rallg on 2010-02-14
The volume-WiFi scramble has also happened here. I don't recall the phenomenon prior to 9.10 or in early 9.10, and I haven't (yet) seen it in 10.04 alpha testing. I wonder if the scramble has something to do with Network Manager (the software that manages WiFi, among other things)? I've noticed that within the last month or two, WiFi sometimes is abruptly dropped even though others in the area (not on Ubuntu) have no problem. Whether the problem still occurs as of today, I do not know.

---

### Post by siabost on 2010-02-14
Actually, Rallg, that's a point.

Shortly after the scrambling problem started I began getting regular WiFi drop-outs to the point where it could happen three or four times a session. I used a belkin PCI card with ndiswrapper & the WinXP driver. I put this down to a change from WEP security to WPA at the time as it kept "losing" the password.

Since then I've changed to a D-link card which works well without help from any Windows drivers. BTW the D-link card had "Supports Linux" stamped on the box so I can thoroughly recommend it.

As I said previously my notification icons remain unscrambled though I do get a slightly differently themed menu bar on the occasional boot for some reason - this causes no functional problems.

:)

---

### Post by Rope on 2010-03-08
I do have similar problems with the notification area. Normally it is the nm-applet which does show a white box instead of the icon. But sometimes it is the session menu wich does not appear correctly. 

I think all these problems are diplay problems.

For getting the icons back, I do hide the panel and then re-show it -> icon is back (most of the times). Or I do change the setting of the panel (auto hide, or show buttons to hide panel) and then icons are back.

Just wanted to tell you my workaround :)

---

### Post by jprupp on 2010-07-09
I have this problem,

It doesn't seem to be related to NetworkManager or any other Gnome program outside of the panel itself, and probably the combination of Compiz and the Nvidia drivers.

Since it's intermittent, it's a bitch to debug.

---

### Post by jprupp on 2010-07-09
By the way, this command kills and restarts the gnome-panel process, and normally everything returns to normal once ran:

```
ALT+F2
killall gnome-panel
ENTER
```

---

