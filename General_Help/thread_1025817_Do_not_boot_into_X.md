---
title: "Do not boot into X"
date: 2008-12-30
forum: General Help
---

### Post by flabordec on 2008-12-30
I installed Xubuntu on a computer for my personal use. Eventually I moved on to another computer and started using the first computer as a server. 

I don't want the server to boot to X because it will spend resources which are very scarce and for some security concerns, is there a way to do this?

Thanks,
Magus

---

### Post by redilyn on 2008-12-30
```

sudo apt-get remove xfce

```

or 

```

sudo apt-get remove xfce4

```

---

### Post by pennacook on 2008-12-30
On Ubuntu Intrepid 8.10 you can use update-rc.d
```

sudo update-rc.d -f gdm remove
sudo update-rc.d gdm stop 01 0 1 6 .
sudo reboot

```
Then once the restarts you will be in console mode.

---

### Post by flabordec on 2008-12-30
Uninstalling gdm worked. Apparently the solution pennacook provided would be a bit more elegant, but I'll keep it in mind for the next time.

---

