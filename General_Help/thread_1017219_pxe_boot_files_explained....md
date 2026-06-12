---
title: "pxe boot files explained..."
date: 2008-12-20
forum: General Help
---

### Post by Mia_tech on 2008-12-20
guys I'm trying to do a pxe install of version 8.10, using a windows 2003 server as the pxe server, my problem is that I don't really understand very well what each of the files that are expected to be loaded to the client machine does, like the pxelinux.0, initrd.gz, pxelinux.cfg/default etc... my pc is booting up and getting ip's configuration from server, and I'm pointing the file to be loaded at boot is the pxelinux.0 file but for some reazon after the pc getting ip configuration is not loading anything yes I have dhcp server poiting to the correct tftp server

thanks

---

### Post by dcstar on 2008-12-20
> **Mia_tech said:**
> guys I'm trying to do a pxe install of version 8.10, using a windows 2003 server as the pxe server, my problem is that I don't really understand very well what each of the files that are expected to be loaded to the client machine does, like the pxelinux.0, initrd.gz, pxelinux.cfg/default etc... my pc is booting up and getting ip's configuration from server, and I'm pointing the file to be loaded at boot is the pxelinux.0 file but for some reazon after the pc getting ip configuration is not loading anything yes I have dhcp server poiting to the correct tftp server

thanks

This may help:

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

---

### Post by Mia_tech on 2008-12-20
thanks for the link, I finally was able to get it going, but I was disappointed when I realize that the pxe install started to pull the ubuntu install from a mirror on the internet and there's nothing to configure so I can pull it from my server instead, may be there's and I just don't know, please advise me how could I pull the install from my server and not from the internet

thanks

---

