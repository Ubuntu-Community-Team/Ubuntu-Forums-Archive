---
title: "User Panel no worky."
date: 2009-02-10
forum: General Help
---

### Post by BrandonBan6 on 2009-02-10
Hey all,

I have Ubuntu 8.10 64 bit running with Compiz. 

I have left the theme default, but have noticed the user switcher menu has disappeared from my top panel. I tried to re-add the user switcher to the panel, and then it shows up, but acts "frozen". I can move or open the menu. I'm clueless as to where to even start troubleshooting this one. Any thoughts?? 

See attached screen shot:


thanks

---

### Post by BrandonBan6 on 2009-02-11
An additonal problem, because of the above issue, I have to shutdown from terminal. Ubuntu then appears to shut down normally as it goes to the Ubuntu Loading splash screen.........the orange bar begins to move and freezes. I have to use the main power button at that point. I think these issues are related. Searching around the internet and no luck finding the same issue... Any thoughts out there? anyone?

---

### Post by BrandonBan6 on 2009-02-12
Still no luck here, but I did discover that it happens in all user accounts. So it is a global setting...

---

### Post by BrandonBan6 on 2009-02-13
Here is the message log files, from the last shutdown, nothing strange?

```

Feb 12 16:38:22 be-ubuntu kernel: [20163.414138] device br0 left promiscuous mode
Feb 12 16:40:22 be-ubuntu bonobo-activation-server (bedmunds-10359): could not associate with desktop session: Failed to connect to socket /tmp/dbus-NMrjoPvojf: Connection refused
Feb 12 16:40:46 be-ubuntu kernel: [20307.540503] nm-system-setti[5847]: segfault at 28 ip 00007f958a9c6584 sp 00007fff967fdec0 error 4 in libnm-settings-plugin-ifupdown.so[7f958a9c0000+9000]
Feb 12 16:40:46 be-ubuntu kernel: Kernel logging (proc) stopped.
Feb 12 16:40:46 be-ubuntu kernel: Kernel log daemon terminating.
Feb 12 16:40:47 be-ubuntu exiting on signal 15

```

---

