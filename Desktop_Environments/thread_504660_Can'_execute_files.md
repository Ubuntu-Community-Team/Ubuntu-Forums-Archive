---
title: "Can' execute files"
date: 2007-07-19
forum: Desktop Environments
---

### Post by pentolino on 2007-07-19
Hello everyone,
since a few days I'm unable to execute certain files which worked before.
If I run it through Nautilus I get this error:
Cannot open xxxx/programmi/eclipse/eclipse: No application suitable for automatic installation is available for handling this kind of file

If I run it through command line I get "permission denied".
I already checked permissions and they are ok, 755 and I'm the owner.
I have this problem with some other executables but not all (for example most of the application which I run through the applications menu work ok but not all of them...)
Can someone please give me a hint on where to look?
regards,
Riccardo

---

### Post by pentolino on 2007-07-20
I found out where the problem is but still can't solve it; the partition where the executable is mounted as 

rw nosuid noexec nodev

The problem is that I changed fstab to look like:

UUID=6a439866-e99f-4662-8d0d-33ebe9e28f03 /media/condivisa ext2 rw,exec,users 0 0

restarted but it still keeps mounting it as before (noexec).
Is Ubuntu ignoring fstab or what?
Thanks for any help provided :-)
Riccardo

---

### Post by pentolino on 2007-07-20
That's it!
The correct way (at least it works as I want) is to mount the partition as:

nouser,rw,exec,auto

this way it is mounted at boot time and everything goes ok.
It's a pity I almost lost a day on this...

---

