---
title: "Need help on installing Cisco VPN on Ubuntu 9.0.4"
date: 2009-04-27
forum: General Help
---

### Post by jingpro on 2009-04-27
I ever installed successfully CISCO_VPN on 8.04 one year ago, based on instructions I found on the internet (including patching some file). Now on 9.04, I can not make it works.

Anyone can share your experience about successfully installing Cisco VPN on Ubuntu 9.0.4? Thanks a lot.

---

### Post by dro0g on 2009-04-27
Hi,

You don't need to install the Cisco VPN client - NetworkManager includes support for Cisco IPSec VPNs. You can also use vpnc from the command line if that's more your scene. 

Click on the NetworkManager icon in the system tray, VPN Connections -> Configure VPN. If you don't have VPN connections listed, you may need to install it (the package name is network-manager-vpnc)

---

### Post by jingpro on 2009-04-28
Thanks a lot. VPNC works perfectly.

---

### Post by Benic on 2009-05-05
I'm using Cisco VPN since 8.04 and it works fine with 8.10 and 9.04 also. The only thing that really bothers me is that you need to reinstall every time there is a kernel upgrade. So far, I don't have problems with jaunty.

---

