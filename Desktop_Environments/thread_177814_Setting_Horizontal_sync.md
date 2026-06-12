---
title: "Setting Horizontal sync"
date: 2006-05-16
forum: Desktop Environments
---

### Post by DumLoco on 2006-05-16
Hi guys, i installed Ubuntu 2 days ago.
I have Breezy 5.10 an Nvidia card.

My problem is the following:
When i move a window in a horizontal way, or scroll horizontally in a web browser, it looks great, very smooth. But wen it comes to vertical movement, it looks awful, not smooth at all. It's really annoying wen it comes to navigate web pages.

I came to the conclusion that the issue is due to a bad configured horizontal sync.
In my nvidia panel, and in the display settings there is no option for the horizontal sync. Btw, i really don't know what's the ideal sync for my resolution (1152*864@75hz).
In my xorg.conf i specified the adecuate range for my monitor (syncmaster 793s)
```
Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-120
EndSection

```, but that's only a range, not the setting of an adequate sync.

How in hell can i set an horizontal sync that works fine? (My other OS is XP Pro and there i get smooth vertical movements in 1152*864@75, so my computer can do it.

Thanks in advance!
Dum.

---

### Post by BobSongs on 2006-05-17
I'll take a stab at it.

> HorizSync       30-70
VertRefresh     50-120

That's what's in your xorg.conf file. Okay.

1. Are those numbers you put in? Or are they defaults? If you still have the manual for the monitor check to see what the HSync and VRefresh rates are. If they differ key in the ones from your manual. If you don't have the manual, surf to your manufacturer's site. They will likely have it in a .pdf file somewhere.

2. Are you using the correct drivers? Yeah, sorry. Had to ask. Too many troubleshooting years behind me not to ask that one. Check out the forums. There should be a posting for the latest drivers. Especially for nVidia since they have great support for their cards. If that's already done and your rates are from your owner's manual... then I'm out of ideas.

Over to you, DumLoco.

---

