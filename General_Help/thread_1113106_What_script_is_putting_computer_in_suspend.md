---
title: "What script is putting computer in suspend"
date: 2009-04-01
forum: General Help
---

### Post by cmaz on 2009-04-01
Hi,

i  didn't think i was a computer noob, i've always been able to work my way around a windows system, but i'm trying out ubuntu for the first time and it is really confusing me.

i'm trying to troubleshoot why my network card is being deactivated when the computer goes into suspend mode, but i can't figure out what script is responsible for this.

From a thread i read, i thought it was /etc/init.d/acpi-support, but at the same time there are acpi-support files in at least one other location (/etc/default). Why multiple?

i was also directed to some other files (pm-utils, i think? tuxonice...etc), but i have no idea what script or file is actually suspending my machine. Can anyone help me out?

By the way, i'm using version 8.10 intrepid.

Thanks!

---

### Post by jis on 2009-04-13
If I remember right, there is a bug report about network not being available after resume.

pm-utils can be used to suspend. Check [http://en.opensuse.org/Pm-utils](http://en.opensuse.org/Pm-utils)

---

