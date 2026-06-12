---
title: "Need to set up network interfaces."
date: 2005-07-29
forum: Desktop Environments
---

### Post by c0rrupt on 2005-07-29
During the install, when the installer showed a list of default network interfaces and asked if I wanted to configure them I accidently skipped that step.  Is there anyway I can bring that back up so I can setup my NIC to use DHCP?

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=c0rrupt]During the install, when the installer showed a list of default network interfaces and asked if I wanted to configure them I accidently skipped that step.  Is there anyway I can bring that back up so I can setup my NIC to use DHCP?[/QUOTE]

You just need to edit /etc/network/interfaces (try "sudo gedit /etc/network/interfaces").  Assuming eth0 is your NIC, you want it to read

```

iface eth0 inet dhcp

```

If you want it configured automatically when you boot, make it

```

auto eth0
iface eth0 inet dhcp

```

Once you have done this, try "sudo /etc/init.d/networking restart".

---

