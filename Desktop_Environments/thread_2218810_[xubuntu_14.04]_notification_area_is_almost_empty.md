---
title: "[xubuntu 14.04] notification area is almost empty"
date: 2014-04-22
forum: Desktop Environments
---

### Post by PierU on 2014-04-22
Hi,

After upgrading to xubuntu 14.04 (from 13.10), the notification area is almost empty : it contains a single icon for the keyboard ("iBus") and nothing else. The network icon, the dropbox icon, etc... are gone.

I already had a similar problem with 13.10, but only with dropbox. Now it is more general, and the dropbox fix at that time (purging /var/lib/.dropbox*) does no longer works anyway.

Any idea ?

Thanks,

---

### Post by Jordan_Cameron on 2014-04-22
just out of interest, what happens if you run xfce4-power-manager from the command line?  From an arch perspective (I only just switched back to buntu) that would indicate nothing is running that has a system notification icon.

So try running xfce4-power-manager or nm-applet (?) from terminal, and see if they pop up.

---

### Post by PierU on 2014-04-23
If I type [COLOR=#000000]xfce4-power-manager[/COLOR] from the command line, nothing visible happens.

The services and other stuff are indeed running. For instance if I type "dropbox status" I get an answer "Up to date", and I can see the my dropbox folder is synchronised. Also, the network is OK, and so on...

It's just that no icon appears in the notification area (except the "iBus" one, as I said earlier).

---

### Post by ziegler-g on 2014-05-01
The same here for me. All this started after the update from 13.10 to 14.04. Mostly annoying, the network-manager is running:

> $ ps aux|grep applet
ziegler   1844  0.0  0.8 407176 17272 ?        Sl   12:44   0:01 nm-applet

But there is no icon in the notification area, which makes the applet useless. This more or less makes my laptop useless, because I cannot take it and go to a café or some other place with a WLAN, and that's what I have it for.

I can hardly understand that this is not one of the bugs with highest priority because it really should not appear in an LTS!

Greetings!

---

### Post by PierU on 2014-05-03
Hi,

On the launchpad ticket for this bug, a workaround has been given : installing in the panel the "indicator plugin" instead of the "notification area". All the desired icons are in the "indicator plugin" (BTW I don't understand the difference between the "indicator plugin" and the "notification area").

---

### Post by ziegler-g on 2014-05-03
Thank you, this workaround really works. That's what a workaround is for! :-)

---

