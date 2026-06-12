---
title: "ASUS W3A Can't complete the Install"
date: 2005-10-13
forum: Desktop Environments
---

### Post by dyroro on 2005-10-13
My notebook is ASUS W3A
When the first step finished, and reboot.
stop under the
Starting hotplug subsystem...

---

### Post by shenki on 2005-10-13
I own a LG LW40 Express, and spent several days trying to get horay working, having the same problem as you.

does the system have intel HD audio?

If so, you need to remove the files /lib/modules/2.6.XXXX/kernel/sound/pci/hda/*, which are the drivers for intel hd audio - this means you won't have sound, but atlest the machine will boot.

If anyone thinks they have any ideas on fixing this problem, attached is the kernel 'Opps' that trying to load the bad driver produces.

---

### Post by dyroro on 2005-10-13
thanx
and now, I can't boot the system, how to remove it?
LiveCD can't to use.

---

### Post by shunhsiung on 2005-10-13
I use Asus W6A , I have the problem ' Hotplug ' .
you can liveCD mount  ubuntu desk , found /etc/hotplug/pci.rc , 
the prc.rc shell have "pci.agent" , you can remark the line , save pci.rc script shell .
reboot again, you can boot ok.

---

### Post by dyroro on 2005-10-13
[QUOTE=shunhsiung]I use Asus W6A , I have the problem ' Hotplug ' .
you can liveCD mount  ubuntu desk , found /etc/hotplug/pci.rc , 
the prc.rc shell have "pci.agent" , you can remark the line , save pci.rc script shell .
reboot again, you can boot ok.[/QUOTE]

Thank you, I'll to try.

---

