---
title: "Losing Notification items on my panel"
date: 2011-12-28
forum: Desktop Environments
---

### Post by rpipes on 2011-12-28
I am running both Xubuntu 11.10 as well as Ubuntu 11.10 on the same laptop.  I have them both on separate partitions, but sharing the same /home partition.  Within Ubuntu I added the xfce4 panel (sudo apt-get install xfce4-panel) and then added it as one of my startup applications.  By doing this I am able to run Unity and still have my taskbar at the bottom, and this works beautifully.

The problem is that when I log into Ubuntu, my notification item is gone from the xfce panel on the bottom, which isn't a problem since I have it on the top bar, but when I log back into Xubuntu I have to add it to the panel again.  I can only assume that even though they are on different partitions they must be sharing config or cached information that is in one of the hidden folders in my home directory which they both share.

Is there a way to enable the two systems to treat xfce4-panel separately so I don't have this problem?

Thanks in advance....

---

### Post by rpipes on 2011-12-30
Okay...well, I repartitioned the drive and completely separated Xubuntu and Ubuntu.  So, I guess this one is solved.

---

