---
title: "Diagnose my Bootchart PNG -- slow boot"
date: 2009-04-26
forum: General Help
---

### Post by jondgls on 2009-04-26
After a week of research getting bootchart to actually make a bootchart...I realised I had no idea how to diagnose the darn thing. :???:

I have a very long boot process as you can see in the bootchart. Total boot time is 2m25sec.

I noticed the change when I added the following code to /etc/fstab/ to automount an internal NTFS slave HDD:
```
/media/HDD4	ntfs-3g	defaults	0	0
```

..but i'm not sure what is going on. I need the drive to mount on boot for media / network sharing.

Any help would be appreciated.

JonDgls

---

### Post by jondgls on 2009-04-27
Perhaps a point to another resource / forum that may assist with bootcharts?

Thank you,
JonDgls

---

### Post by ninjapirate89 on 2009-04-27
Was it much faster before you added the automount for the extra HD?

---

### Post by jondgls on 2009-04-27
It was considerably faster being somewhere around 35-40 seconds to idle desktop.

JonDgls

---

### Post by ninjapirate89 on 2009-04-27
Hmmmm....thats a considerable difference. I'll see if I can google up some info on this problem.

Edit -> I can't seem to find anything that may be causing this. I can only recommend that you undo whatever you did to automount that drive and try a different method.

---

### Post by jondgls on 2009-04-28
Well I removed the automount code from /etc/fstab and the boot time has not changed.

If someone could read the bootchart and give me an indication of where the fault is, I would really appreciate it.

JonDgls

---

### Post by jondgls on 2009-04-28
[Solved] While setting up a bridge between my wireless card and virtualbox I added code to my:
```
/etc/network/interfaces
```

Once I commented out these changes and left only (the default):
```
auto lo
iface lo inet loopback
```
..my bootime has returned to normal.

The problem is the /etc/init.d/networking script has the interfaces wait for a DHCP response with a timeout setting of 120 seconds!

New bootime is 40 seconds! :D

JonDgls

---

