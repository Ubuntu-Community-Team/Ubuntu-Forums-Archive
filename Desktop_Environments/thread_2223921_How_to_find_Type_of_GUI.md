---
title: "How to find Type of GUI"
date: 2014-05-13
forum: Desktop Environments
---

### Post by adam57 on 2014-05-13
So I just downloaded C.A.I.N.E. on a USB drive and ran it.  The GUI on it looks AMAZNG and I want to know what it is.

Is there a command or file that I can open to see the type of GUI the mahcine is running?


Thanks!

---

### Post by su:bhatta on 2014-05-13
If [this]("http://www.caine-live.net/") is the caine you are refering to, then this is from their website: 
> CAINE offers a complete forensic  environment that is organized to integrate existing software tools as  software modules and to provide a friendly graphical interface.
CAINE Distro has been realized from Ubuntu Linux using also Remastersys  developed by Tony Brijeski and released with GNU GPL license, version  3.0.1-1.


By the looks of it, it seems to use a GTK based interface, which is customized by the team. 
By the look of it, pretty near to Mint , Ha !

---

### Post by mcduck on 2014-05-13
Based on the look of the panel and menu, it could be either old Gnome2 or Gnome3 Classic (and since they state it's based on Based on Ubuntu 12.04.3, I'd place my bets on Gnome Classic)

---

### Post by HiImTye on 2014-05-13
if it reports it, you can```
echo "$XDG_CURRENT_DESKTOP"
```

---

