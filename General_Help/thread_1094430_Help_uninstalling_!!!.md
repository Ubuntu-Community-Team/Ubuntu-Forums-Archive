---
title: "Help uninstalling !!!"
date: 2009-03-12
forum: General Help
---

### Post by meandshadow on 2009-03-12
Hi Everyone! I need help in uninstalling Kubuntu from my soon to be gone laptop but leave the XP Media Center Edition on it as some of the files are needed... I've tried to delete the partition containing Kubuntu and two others but now I can even log on... So I'm reinstalling Kubuntu in dual boot and hope this gets me near to where I was before... ???

---

### Post by DGortze380 on 2009-03-12
> **meandshadow said:**
> Hi Everyone! I need help in uninstalling Kubuntu from my soon to be gone laptop but leave the XP Media Center Edition on it as some of the files are needed... I've tried to delete the partition containing Kubuntu and two others but now I can even log on... So I'm reinstalling Kubuntu in dual boot and hope this gets me near to where I was before... ???

Can't log on to what??

GParted LiveCD is what you want.

Delete linux partitions, format free space to NTFS, call it a day.

Best to have a windows install disk ready incase a fixmbr is needed.

---

### Post by ajgreeny on 2009-03-12
If you have media centre (windows) still on you machine you just need to restore the windows MBR.  You can either do it with a windows install CD or if you don't have one try the following:-
You can install a Windows equivalent MBR to your sda drive by doing the following from your Live (k)ubuntu CD:
Code:

```
sudo apt-get install lilo
```then
```
sudo lilo -M  /dev/sda mbr
```

Then you should be able to boot directly into Windows again if all goes well. Let me know how it goes or if you run into problems.

If you do not still have windows on the machine a reinstall of kubuntu should get you back to where you were.

---

