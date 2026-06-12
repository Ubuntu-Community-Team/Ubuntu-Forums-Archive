---
title: "can't configure KPPP"
date: 2006-03-29
forum: Desktop Environments
---

### Post by walvirch on 2006-03-29
Been trying in vain to configure KPPP as a dialer for my USR5610 internal modem. The dropdown menu only goes to /dev/ttys13. My modem is installed on COM3(windows), /dev/modem (SUSE10), /dev/ttys14 (wvdial.conf on Ubuntu&KUbuntu). About the only way I can think of to solve the problem is by setting up a symbolic link to /dev/modem from /dev/ttys14. Can't find any documentation so far as to how to proceed. HELP!. Hope I posted this in the right forum list.

---

### Post by towsonu2003 on 2006-04-14
[QUOTE=walvirch]Been trying in vain to configure KPPP as a dialer for my USR5610 internal modem. The dropdown menu only goes to /dev/ttys13. My modem is installed on COM3(windows), /dev/modem (SUSE10), /dev/ttys14 (wvdial.conf on Ubuntu&KUbuntu). About the only way I can think of to solve the problem is by setting up a symbolic link to /dev/modem from /dev/ttys14. Can't find any documentation so far as to how to proceed. HELP!. Hope I posted this in the right forum list.[/QUOTE]
sudo ln -s /dev/ttys14 /dev/modem

although I would just use wvdial (I like the idea of "if it ain't broken, don't fix it).

---

