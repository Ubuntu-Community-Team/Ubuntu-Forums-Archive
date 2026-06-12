---
title: "MBR/GRUB messed up, help in restoring"
date: 2009-01-19
forum: General Help
---

### Post by malfist on 2009-01-19
Grub is still there and working, and I can find it with supergrub disk, however when I boot the computer I get the error:
```

L 99 99 99 99 99

```
With like 50 or 60 following '99'

How can I restore what my MBR? I formatted sda and I think I might have wiped something out there. (I boot to sdb, sdc is windows and sda is backup)

---

### Post by caljohnsmith on 2009-01-20
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by malfist on 2009-01-20
The problem is I believe I wiped the MBR that pointed to grub off of /dev/sda and my motherboard is loading lilo that's on /dev/sdb (which doesn't work because it points to the /boot on /dev/sdb which is grub)

---

