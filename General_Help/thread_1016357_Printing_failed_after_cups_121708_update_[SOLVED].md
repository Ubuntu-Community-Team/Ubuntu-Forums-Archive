---
title: "Printing failed after cups 12/17/08 update [SOLVED]"
date: 2008-12-19
forum: General Help
---

### Post by mia1dolfan on 2008-12-19
The cups 12/17/08 updates broke printing for me.  This affects two network printers, both connected via Directjet tcp 9100. I tested printing in Evince, Okular, Acrobat Reader, Firefox, Gimp, gedit. The only thing that would print is the test page sent to it from 'system-config-printer' applet. I sniffed the traffic and saw that a complete postscript document from header to footer was being successfully sent to the printers (by rebuilding TCP conversation in Wireshark), however no job was processed by the printer. Creating a new printer did not help. I downgraded the *cups* packages to the ones installed on 11/28/08 and then I was able to print again.

These are the commands I ran to downgrade.  I used the archived packages on my machine from 11/28/08.

```
cd /var/cache/apt/archives
sudo apt-get remove cups-bsd # Dependency problem if not removed first
find -name '*cups*\.deb' -printf '%AD %f\n' | grep "11/28/08" | \
 cut -d\ -f2 | sudo xargs -i{} dpkg -i "{}"
sudo /etc/init.d/cups restart
# Place cups packages on hold so not auto upgraded by package manager
find -name '*cups*\.deb' -printf '%f %AD\n' | grep "11/28/08" | \
 awk -F_ '{print $1 " hold"}' | sudo xargs -i{} sh -c 'echo "{}" | \
 dpkg --set-selections'


```

---

