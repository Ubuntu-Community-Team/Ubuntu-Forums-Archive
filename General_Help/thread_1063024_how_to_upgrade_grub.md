---
title: "how to upgrade grub"
date: 2009-02-07
forum: General Help
---

### Post by anand77 on 2009-02-07
I have ubuntu intrepid ibex installed in my Dell Dimension 3000. If I run the following command:

```

anand@anand-desktop:~$ cat /boot/grub/installed-version 
0.97-29ubuntu21

```

Looks like the latest version of grub for intrepid ibex is: [0.97-29ubuntu45]("https://launchpad.net/ubuntu/+source/grub/")

My question is: how to upgrade to the latest version?

Thanks in advance. :p

---

### Post by taurus on 2009-02-07
If it's in the repos, then you would upgrade it like you would with any other app.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Nero147 on 2009-02-07
I'm not saying you shouldn't update, but the different versions of grub don't really have any significant feature differences. All they really do is point at your kernel. The custom grub commands haven't really changed in the years I've been using Ubuntu. So why are you wanting to update?

---

### Post by yoman82 on 2009-02-07
grub-update is actually a command, try it.

---

### Post by anand77 on 2009-02-07
Isn't grub-update used for updating the /boot/grub/menu.lst file?

---

