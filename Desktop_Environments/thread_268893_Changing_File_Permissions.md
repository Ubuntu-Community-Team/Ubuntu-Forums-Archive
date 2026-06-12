---
title: "Changing File Permissions"
date: 2006-09-30
forum: Desktop Environments
---

### Post by Emasters on 2006-09-30
How do I edit my souces.list file to add repositiories.  When I use a text editor I am told I am not the owner and I can't save any changes.  How do I either become the owner or log in as root to begin with?  How do I use sudo if I am not in a terminal?  Thanks !

---

### Post by Kingsley on 2006-09-30
use nautilus.

---

### Post by Emasters on 2006-09-30
How do I use nautilus

---

### Post by kewldude606 on 2006-09-30
> **Emasters said:**
> How do I edit my souces.list file to add repositiories.  When I use a text editor I am told I am not the owner and I can't save any changes.  How do I either become the owner or log in as root to begin with?  How do I use sudo if I am not in a terminal?  Thanks !

Open the terminal (Applications-->Accessories-->Terminal).  Type in "sudo gedit /etc/apt/sources.list" (without the quotes).  Press enter, type in your  password, and hit enter again.

---

### Post by Emasters on 2006-09-30
Thanks !

---

### Post by ardchoille on 2006-10-01
> **kewldude606 said:**
> Open the terminal (Applications-->Accessories-->Terminal).  Type in "sudo gedit /etc/apt/sources.list" (without the quotes).  Press enter, type in your  password, and hit enter again.

It's better to use gksudo with gui apps. What he needs is:

```

gksudo gedit /etc/apt/sources.list

```

See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) To see why it's best to use gksudo with gui apps.

---

