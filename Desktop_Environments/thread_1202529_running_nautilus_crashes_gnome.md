---
title: "running nautilus crashes gnome"
date: 2009-07-02
forum: Desktop Environments
---

### Post by ezacon on 2009-07-02
I have an ubuntu server 9.04 with gnome desktop installed. The system is runing fine except for nautilus. When i run it, from menu or console, the destop hangs forever. I can still log in via ssh and the server processes are runing fine.
In syslog, i get this when i run nautilius:

Jul  2 16:26:43 coll kernel: [  266.028035] NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 000008dc 00000000 00000100
Jul  2 16:26:43 coll kernel: [  266.058515] NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 00000104 00000000 00000100
Jul  2 16:26:43 coll kernel: [  266.099661] NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 000008dc 00000000 00000100
Jul  2 16:26:43 coll kernel: [  266.165594] NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 00000104 00000000 00000100
Jul  2 16:26:43 coll kernel: [  266.200799] NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 000008dc 00000000 00000100
Jul  2 16:26:43 coll kernel: [  266.238466] NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 000008dc 00000000 00000100
Jul  2 16:26:43 coll kernel: [  266.285256] NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 000008dc 00000047 00000100
Jul  2 16:26:43 coll kernel: [  266.330223] NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 000008dc 00000000 00000100

/etc/init.d/gdm restart does not work. Only a full reboot does.

This was running in the past. I think it is failing after an update.
Any idea?

---

### Post by ezacon on 2009-07-04
I have found that i am using 2.6.28.11 kernel. It should be 2.6.28.13. The .13 kernel files are present in /boot directory, but not present in grub config.
I will try to add a grub config for .13.

---

### Post by ezacon on 2009-07-05
moore on this.
i have added 2.6.28.13 to grub, but the nvidia driver does not work with this kernel. The destop runs in low resolution mode but nautilus works.
it looks like a nvidia driver issue.

---

### Post by raidoz on 2009-07-06
Having a similar problem, though crashes seem random. Had a similar issue when I installed the OS, but adding Option "RenderAccel" "False" solved it(it's still in xorg.conf). The new problems seem to have started after the updates on 2 or 3 of July, when the -13 kernel was installed, -11 is still installed, but manually choosing it does not help. Rest of the updates were lsb- and perl stuff ... nothing that particularly stands out for me.

---

### Post by ezacon on 2009-07-07
In wich section did you add this option?
Thanks for your answere.

---

### Post by ezacon on 2009-07-08
The issue was solved installing nvidia-glx-190 from repositories.
Now i con run nautilus without problem.

---

