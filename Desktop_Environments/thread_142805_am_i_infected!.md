---
title: "am i infected?!"
date: 2006-03-11
forum: Desktop Environments
---

### Post by nerrad on 2006-03-11
Hi i have just installed firestarter and realized that it is blocking access attempts  on port 7000 to the process afs3-fileserver. 

Looking at the logs is shows attempted connections from a whole range of different IP's 

I have not installed no type of file server apart from setting up local samba shares between pcs on my network.

I have run a full system scan using fprot and no infection was found?

surely i should be concerned? or is there a legitimate reason for this service to be running. e.g. azureus uses it.

---

### Post by Zyphrexi on 2006-03-11
infected with what? a virus?
 I doubt it.

Also I have no idea.

---

### Post by az on 2006-03-11
Do you have any afs packages installed?  None are installed by default.



apt-cache search afs
john - An active password cracking tool
libkafs0-kerberos4kth - Afs Libraries for Kerberos4 From KTH
tcpdump - A powerful tool for network monitoring and data acquisition
arla - A free client for the AFS distributed network filesystem
arla-dev - Static libraries for building AFS-aware programs
arla-modules-source - Source to generate arla-modules
defrag - ext2, minix and xiafs filesystem defragmenter
kstart - Kerberos kinit variant supporting ticket refreshing
libopenafs-dev - The AFS distributed filesystem- development libraries
libpam-openafs-kaserver - The AFS distributed filesystem- kaserver PAM module
libpam-openafs-session - PAM Module to get AFS tokens and set up PAG
lojban-common - commonly used wordlists for the Lojban language
lufs-source - Linux Userland Filesystem - kernel module source
lufs-utils - Linux Userland Filesystem - utilities
multimon - Linux Radio Transmission Decoder
netdiag - Net-Diagnostics (trafshow,strobe,netwatch,statnet,tcpspray,tcpblast)
openafs-client - The AFS distributed filesystem- client support
openafs-dbserver - The AFS distributed filesystem- database server
openafs-fileserver - The AFS distributed filesystem- file server
openafs-kpasswd - The AFS distributed filesystem- old password changing
openafs-krb5 - The AFS distributed filesystem- Kerberos 5 Integration
openafs-modules-source - The AFS distributed filesystem- Module Sources
libkafs0-heimdal - Libraries for Heimdal Kerberos

---

### Post by nerrad on 2006-03-11
results of the search are as follows

apt-cache search afs
arla - A free client for the AFS distributed network filesystem
arla-dev - Static libraries for building AFS-aware programs
arla-modules-source - Source to generate arla-modules
defrag - ext2, minix and xiafs filesystem defragmenter
kstart - Kerberos kinit variant supporting ticket refreshing
libpam-openafs-session - PAM Module to get AFS tokens and set up PAG
lojban-common - commonly used wordlists for the Lojban language
lufs-source - Linux Userland Filesystem - kernel module source
lufs-utils - Linux Userland Filesystem - utilities
multimon - Linux Radio Transmission Decoder
netdiag - Net-Diagnostics (trafshow,strobe,netwatch,statnet,tcpspray,tcpblast)
openafs-krb5 - The AFS distributed filesystem- Kerberos 5 Integration
john - An active password cracking tool
libkafs0-kerberos4kth - Afs Libraries for Kerberos4 From KTH
tcpdump - A powerful tool for network monitoring and data acquisition
libkafs0-heimdal - Libraries for Heimdal Kerberos
libopenafs-dev - AFS distributed filesystem development libraries
libpam-openafs-kaserver - AFS distributed filesystem kaserver PAM module
openafs-client - AFS distributed filesystem client support
openafs-dbserver - AFS distributed filesystem database server
openafs-fileserver - AFS distributed filesystem file server
openafs-kpasswd - AFS distributed filesystem old password changing
openafs-modules-source - AFS distributed filesystem kernel module source

could any of these be running and causing the connection attempts?

if so how do i stop/remove it or do i even need to (could it affect other processes i need?)

Thanks for the help

---

### Post by az on 2006-03-11
That command just lists the available packages.

To see what you have installed, run
dpkg -l

To search through what you have installed run

dpkg -l|grep afs

But it's probably just simpler to use synaptic and search that way.  It will show you all of the packages that relate to afs and which ones of those are installed. 

If you have one installed and select it for removal, it will also tell you that it will remove the package that depends on it (it got installed somehow, right?)

---

