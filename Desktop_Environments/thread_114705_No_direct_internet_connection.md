---
title: "No direct internet connection"
date: 2006-01-09
forum: Desktop Environments
---

### Post by Vinze on 2006-01-09
Whenever I start my PC, it always hang a bit while trying to configure network interfaces. I guess it fails or something, because when I login, I have no IP assigned. I used to think that I had to connect and disconnect a few times, and then mostly when it finally connected, the PC crashed and I had to force a shutdown. Now I didn't immediately started using the internet, and then after a while it suddenly connected. 
Before, I couldn't even connect to the internet, and I solved this by adding "acx_pci", the native driver, to /etc/hotplug/blacklist so it won't load anymore, and now I use the Windows driver with ndiswrapper. 
Does anyone know the solution? I'd be very very grateful.

---

### Post by handy on 2006-01-09
The only help I can give you is a link to a very well organised help site, go here:

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

Then scroll down to this part:

# 12 Networking

    * 12.1 How to configure Google Talk
    * 12.2 How to activate/deactivate network connections
    * 12.3 How to configure network connections
    * 12.4 How to configure dialup connections
    * 12.5 How to configure broadband connections
    * 12.6 How to change computer name
    * 12.7 How to change computer descriptions
    * 12.8 How to change computer Domain/Workgroup
    * 12.9 How to assign Hostname to local machine with dynamic IP using free DynDNS service
    * 12.10 How to share folders the easy way
    * 12.11 How to browse network computers
    * 12.12 How to access network folders without mounting
    * 12.13 How to mount/unmount network folders manually, and allow all users to read
    * 12.14 How to mount/unmount network folders manually, and allow all users to read/write
    * 12.15 How to mount network folders on boot-up, and allow all users to read
    * 12.16 How to mount network folders on boot-up, and allow all users to read/write
    * 12.17 How to get ipw2200 and wpa to work

I hope there is a solution there for you...

handy

---

### Post by Vinze on 2006-01-09
That didn't help, but thanks anyway. Any other ideas?

---

### Post by handy on 2006-01-09
If you had another network card laying around you could try it on the of chance that yours is faulty...

I make that sugestion because it is so easy.

Sorry I can't be more help.

handy

---

### Post by Vinze on 2006-01-09
Nah, I don't have other network cards. Thanks anyway, I appreciate every try to help.

---

