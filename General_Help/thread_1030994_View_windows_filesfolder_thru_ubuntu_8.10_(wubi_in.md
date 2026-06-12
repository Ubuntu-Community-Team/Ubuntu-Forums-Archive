---
title: "View windows files/folder thru ubuntu 8.10 (wubi installation)"
date: 2009-01-04
forum: General Help
---

### Post by Schok on 2009-01-04
i installed ubuntu 8.10 in windows using wubi, then wanted to view the windows files/folder (installed the NTFS tools from add/remove) but i still cant view them. any help?

---

### Post by Schok on 2009-01-05
Update: i tried [LIST]
[*]Ext3 IFs      - It asks if i want to reformat the drive
                   and mountdiag.exe doesnt work, it just appears 
                   a couple of secs then disappears
[*]Linux Reader  - Doesnt do anything when i want to open the 
                   partition..it just stays on the same page but
                   the address bar says im inside the partition
[/LIST]


Sorry, this are the programs i tried to read linux's partition thru windows [on a normal install of ubuntu]

---

### Post by blazemore on 2009-01-05
Open a terminal and type
```
sudo fdisk -l
```

One of the lines will have NTFS somewhere, look at the device name, let's called it /dev/sda1, but remember to change it for what yours actually is.

```
sudo mkdir /windows
```
Makes a directory called /windows

```
sudo mount -t ntfs /dev/**sda1** /windows
```
Remember to change the bold text to what is relevant to you.

And if you ever have problems with mounting, add the code ```
-o force
``` to the end of any mount command.

---

