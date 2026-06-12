---
title: "Strange Nautilus/Totem Freezing"
date: 2005-03-25
forum: Desktop Environments
---

### Post by Grey on 2005-03-25
Hi.  I am currently building a new computer, and trying to get AMD64 Hoary installed on it.  In the general course of things, I downloaded the Hoary preview ISO, installed all the updates via Synaptic, and have a completely up to date build as of 8:00AM MST this morning.  I installed a bunch of extras like MP3 support and XMMS.

Here's the interesting part.  When I went to right click on an MP3 file, and select "properties", in order to change the default application to XMMS, Nautilus simply froze.  Hard drive activity also ceased (I was copying files from a Samba share).  I killed the process, and tried again on a OGG file.  Same behavior.  I tried again with a simple text file, and the expected behavior of opening up a properties dialog happened.

Now here's the strange part.  In order to try to get it working and troubleshoot the problem, I uninstalled Totem.  And the problem vanished, and I was able to get to the properties dialog.

I just thought I would alert people about this, and ask if anyone else was having the same problem, or if it would be fixed by the time Hoary becomes final?

---

### Post by Mase Track on 2005-03-25
I've also had problems with totem in regards to playing a video, and then going to quit, totem freezes! When I try to kill the process or force a quit, it locks up my session. It did this no less than 4 times today as I was trying to figure out the problem.

The only solution I could manage was to uninstall via synaptic  :(

---

### Post by NiceGuyUK on 2005-06-21
More specifically, the problem is with totem-xine.  Replace it with totem-gstreamer and  restart nautilus (killall -9 nautilus does the trick for me).

Watch when you uninstall totem-xine via Synaptic though, it attempts to remove ubuntu-desktop, which is kinda important!  I simply marked it for reinstallation (it wouldn;t let me unmark it).  Apply the changes and things will sort themselves out.

Did for me anyway.

---

