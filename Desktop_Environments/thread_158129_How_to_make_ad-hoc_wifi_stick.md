---
title: "How to make ad-hoc wifi stick?"
date: 2006-04-10
forum: Desktop Environments
---

### Post by jamespi on 2006-04-10
Hi, there is no GUI option to config my wifi card to ad-hoc mode, so i have to type "sudo iwconfig eth0 mode ad-hoc" every time i reboot.

How can i make this config stick so it doesnt have to be redone all the time?

---

### Post by Quirky on 2006-04-11
You will have to edit /etc/network/interfaces. While I'm not 100% sure of this, since I could never get ad-hoc working correctly with my set up, you will need an entry like this:

```

iface eth0 inet static
  pre-up iwconfig eth0 mode ad-hoc
  #other options set essid, etc...  see "man interfaces"

```

Good luck!

---

