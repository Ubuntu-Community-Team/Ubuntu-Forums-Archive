---
title: "problems connecting to Windows DHCP server"
date: 2006-07-01
forum: Desktop Environments
---

### Post by poontang on 2006-07-01
Hi there, just done a clean install of 6.06 (dual boot with XP) - tried to set the network proxy settings (no luck there), checked out the "Networking" settings find that eth0 set to DHCP but no IP, subnet mask or gateway is set. I plug in the setting manually for a static IP - reboot - internet connects for a minute or two then cuts out on me. Am trying to connect to our Win 2000 server for DHCP & proxy etc. Have no problems with XP or Centos in this area. Any tips? Thanks much.

---

### Post by grooverider on 2006-07-01
after u booted into ubuntu, check the settings in /etc/network/interfaces also i had some problems with my dhcp sometimes ifdown and ifup solved the problem, try it out... good luck

---

### Post by poontang on 2006-07-02
Looks like Ubuntu dosent like my CNET PRO200 network card dang.

---

