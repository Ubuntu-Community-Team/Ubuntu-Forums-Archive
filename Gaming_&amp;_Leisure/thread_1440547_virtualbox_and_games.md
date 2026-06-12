---
title: "virtualbox and games"
date: 2010-03-27
forum: Gaming &amp; Leisure
---

### Post by jbumgar on 2010-03-27
Can you play pc games on virualbox 3.16

---

### Post by TetonsGulf on 2010-03-27
Simply, yes.

Your experience is going to to depend though on the resources you allocate to the virtual machine. 

Response and performance are, in my experience, less impressive than they are running PC games natively.

Wine may be an option you want to look into.

---

### Post by NightwishFan on 2010-03-27
When installing guest additions in Virtualbox, you must be in safe mode. Reboot the virtual Windows and hold f8 to get the safe mode prompt. Then install the guest additions. You can get guest additions by installing the virtualbox guest additions package. While in safe mode windows, mount the guest additions iso (its located in /usr/share/virtualbox) and click the .exe inside the virtual windows. Follow the onscreen prompt and enable the direct3d support. After it is installed, unmount the guest additions iso and reboot virtual windows.

3d games should work, but it depends on your hardware how well.

---

