---
title: "GNOME to KDE"
date: 2010-09-27
forum: Desktop Environments
---

### Post by Jonny87 on 2010-09-27
So my Dad who I've just gotten onto Ubuntu has recently installed the KDE onto his normal Ubuntu install and now prefers KDE over GNOME and he wants know if its possible to now remove the original gnome environment and still have a fully functional KDE system. He wants to do this to save him from doing a clean install with Kubuntu.

I'm guessing that it is probably possible but he would have to make sure that he has certain packages installed.

---

### Post by pmlxuser on 2010-09-27
```

sudo apt-get remove --purge ubuntu-desktop 

```

---

### Post by Jonny87 on 2010-09-27
> **pmlxuser said:**
> ```

sudo apt-get remove --purge ubuntu-desktop 

```
Thanks, I thought it would be something like that but I want to check, will this remove anything vital that could leave his system unusable as I'm in a different country and hes not that tech savvy and he really needs his comp going.

Does he need to make sure particular packages are installed for it still work would they already be there with the KDE?

---

### Post by 3Miro on 2010-09-27
Unless you are low on disk space or something like that, I recommend that you keep Gnome as a fail-safe. If you want "pure" KDE, go for clean Kubuntu install, otherwise don't remove the default desktop. It is possible that you remove something important.

---

### Post by ankspo71 on 2010-09-27
Hi,
Removing Ubuntu desktop and its applications can be done in one process (if everything goes well). [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde) .
The above link will strip your ubuntu of all of the default gnome applications then reinstall KDE (Kubuntu Desktop).

However, after using the command in the above link, you will notice that your home folder(s) will still contain all of your gnome application and desktop configurations, so it's a little untidy compaired to installing Kubuntu fresh (only in my opinion of course, others find the the remaining Gnome configurations helpful for when they need to reinstall the Gnome desktop again), but the above link has worked for me. Also keep in mind that Kubuntu doesn't have Ubuntu's gnome applications installed by default, so if if you have any favorite Ubuntu applications that were there by default, they will need to be reinstalled separately.

Whether you install Kubuntu fresh, or remove the Gnome desktop, be sure to make backups of your improtant data first.

---

