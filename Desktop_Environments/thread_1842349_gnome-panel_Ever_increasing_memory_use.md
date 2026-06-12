---
title: "gnome-panel Ever increasing memory use"
date: 2011-09-11
forum: Desktop Environments
---

### Post by sleon on 2011-09-11
Is there a way to see if an applet or gnome-panel itself is leaking memory?  Virtual and writable memory for gnome-panel is increasing at a rate of 100kB/second so I have to kill+restart it every few hours to keep from exhausting all system memory.  Under memory maps for gnome-panel shows the heap increasing at that rate.

Googling has shown older threads about possible leaks with wnck-applet, and possibly the network manager applet, but nothing recently.  I've stripped almost everything from the panel to no effect.

This is 10.04 with all updates applied.  This has only started happening within the last week.  Any help/hints appreciated.

---

### Post by raja.genupula on 2011-09-11
[http://live.gnome.org/MemoryReduction](http://live.gnome.org/MemoryReduction)

i found that this is a bug 
i hope above link gonna help you to understand

---

### Post by sleon on 2011-09-12
Thanks for the reply raja.  I did a full reboot with almost all applets removed and the problem went away.  My suspicion is that it was related to the drive mounter applet but unfortunately there's no way to say definitively.  I added it back and there's no effect on memory usage now.

For the record, one other symptom was when selecting a sub-menu item (e.g. Places|Home Folder), if you hovered over it, it would close out after a couple seconds.  Never saw that behavior before.

I'll update this post if it happens again.

---

### Post by raja.genupula on 2011-09-12
i am glad to here that your issue got solved . .

---

