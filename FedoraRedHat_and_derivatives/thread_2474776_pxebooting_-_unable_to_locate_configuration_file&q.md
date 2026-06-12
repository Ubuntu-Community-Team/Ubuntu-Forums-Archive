---
title: "pxebooting - :unable to locate configuration file&quot;"
date: 2022-05-07
forum: Fedora/RedHat and derivatives
---

### Post by jencdi on 2022-05-07
OS- Rocky Linux 8.5 with Warewulf V4

I can boot one of the node and it will acquire a IP address but can not find the configuration file.

Copy of DHCPD.conf file

subnet 10.0.1.0 netmask 255.255.255.0 {
    # specify the range of lease IP address
    range dynamic-bootp 10.0.1.100 10.0.1.160;
    # specify broadcast address
    option broadcast-address 10.0.1.255;
    # specify gateway
#    option routers 10.0.1.1;
#    option domain-name-server 10.0.1.11;
#    option doamin-name "my-machine";
#    option ip-forwarding off;


filename "pxelinux.0";
}

pxelinux.0 is located in var/lib/tftpboot

When I start Warewulf the following line appears.  "Writing PXE files to: /var/lib/tftpboot/warewulf" When I check there the directory contains; arm64.efi,  i386.efi,  i386.kpxe,  ipxe, and  x86.efi

Any help would be appreciated.

---

### Post by DuckHook on 2022-05-07
*Thread moved to **Fedora/RedHat and derivatives** as the more appropriate forum.*

---

