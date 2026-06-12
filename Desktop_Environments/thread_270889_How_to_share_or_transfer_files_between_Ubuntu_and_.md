---
title: "How to share or transfer files between Ubuntu and VMware Server + Windows XP?"
date: 2006-10-03
forum: Desktop Environments
---

### Post by EverySam on 2006-10-03
I have been doing a lot of Googling, and have come up with various confusing strategies (host-only networking, Samba, SWAT) and haven't been able to figure out the simplest or most straightforward way to do it.

Any help would be appreciated.

—s

---

### Post by tagra123 on 2006-10-03
I used samba. Had to allow some ports in firestarter, but it works great with vmware.

---

### Post by scxtt on 2006-10-03
i've been able to use Samba from my Kubuntu host to connect to a VMware guest Windows XP ... your 1st order of business should be to make sure you can assign a valid IP address to your guest ... i use 192.168.1.100 for Kubuntu and 192.168.1.101 for XP using "bridged" networking for the VM ...

---

