---
title: "Print to Windows server using samba?"
date: 2006-07-11
forum: Desktop Environments
---

### Post by devnulljp on 2006-07-11
Trying to print from Ubuntu boxes to a Laser printer attached to a WinXP server.
Using samba and the correct PPD file for the printer installed locally in /etc/cups/ppd/, it works fine from boxes on the same subnet but not identically configured boxes on a different subnet.
I seem to remember something about netbios not being routable across subnets, so is that the problem? Any secret to allow me to print from all nix boxes to the printer on the windows server?

ubuntu_box_1<ip: xxx.xxx.175.xxx> prints OK to windows_box<ip: xxx.xxx.175.xxx>

ubuntu_box_2<ip: xxx.xxx.10.xxx> doesn't print to windows_box<ip: xxx.xxx.175.xxx>

Any ideas?

---

### Post by T313C0mun1s7 on 2006-07-11
Sorry I can not give you a more exact answer, but at least it is a place to start.

SMB does not cross subnets, this is what WINS is for. You may need a WINS server on the subnet with the printer. Maybe you can set this up on the Windows box serving the printer, or on whatever is providing DHCP (if you are using it) to the subnet with the printer. Then somewhere in the samba configuration file on your workstation you need to enable WINS and point it to the server.

Again I wish I could be more exact, but I have not done this myself and I am just pulling this from the networking theory I remember.



[IMG]http://folding.extremeoverclocking.com/sigs/sigimage.php?u=188072[/IMG]

---

