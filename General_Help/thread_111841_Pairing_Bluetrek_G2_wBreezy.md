---
title: "Pairing Bluetrek G2 w/Breezy"
date: 2006-01-03
forum: General Help
---

### Post by muppetmaster on 2006-01-03
I am attempting to pair a Bluetrek G2 headset with Ubuntu/Breezy.  I have installed both Gnome-bluetooth as well as btsco following the directions here:

[http://www.ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth](http://www.ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth)

With btsco I get this error:

```
btsco -v 00:00:00:00:00:00 (replaced with actuall MAC address)
btsco v0.4
Device is 1:0
Error: Failed to connect to SDP server: Invalid exchange
Assuming channel 2

Voice setting: 0x0060
Can't connect RFCOMM channel: Invalid exchange
```

With hcitool I get this:

```
sudo hcitool cc 00:00:00:00:00:00 (replaced with actuall MAC address)
Can't create connection: Input/output error
```

As a side-note, I do not understand the utility of gnome-bluetooth, as after scanning for devices it shows them, but then does not appear to allow any action such as pairing.

Back on subject, could it be that somehow this headset is not properly compatible?  Works fine with my OSX-10.4.3 platform.

---

### Post by dave2010 on 2006-10-28
*BUMP*

I'm also having trouble with this headset.
I can't get it to pair at all. Followed instructions to the letter and nothing!
Managed to get my k750i working though.
Any ideas?
Thanks.
Update: [http://www.holtmann.org/linux/bluetooth/features.html](http://www.holtmann.org/linux/bluetooth/features.html)

There is no HCI version listed, only LMP. Does this mean it's not supported?
I'm gonna dig around and see what this "LMP" business is.

Another update: the bluetooth-also project says its compatible with the G2, unfortunately they assume that you can pair the thing.

---

