---
title: "Help with my FSTAB error...."
date: 2009-05-07
forum: General Help
---

### Post by benwesting on 2009-05-07
Hi there, just wondering if anyone could help with the following error.....

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=d258cd74-9626-4871-9928-401c78186529 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=4c67effc-6a95-4a76-a2fc-5528784ca9b8 none            swap    sw              0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

On boot up it hangs abit on Configuring Network Interfaces unless i press CTRL+ALT+DEL

---

### Post by Alterax on 2009-05-07
I think I know what's going on.  The problem's in /etc/network/interfaces.
Comment out all the lines pertaining to eth0 and you should be good--if you use it, NetworkManager will handle establishing the connection once you log in.

The reason that's going on with your computer is that it's been instructed to bring up the network interface, and to get an address from the DHCP server.  It's taking so long because it tries several times before giving up.

---

### Post by benwesting on 2009-05-13
Sorry for the late reply to your message! Thanks for getting back to me. Ive tried doing what you suggested but get the following when i try to save it....

> Could not save the file /etc/network/interfaces.
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.


Any suggestions? Ive tried changing the permissions from root to my name but that hasnt helped!

---

