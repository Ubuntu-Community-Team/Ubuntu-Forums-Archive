---
title: "can't change login screen"
date: 2006-11-07
forum: Desktop Environments
---

### Post by xor.be on 2006-11-07
Hi,

I have remove the kde environment,but i am still stuck with the blue kubuntu login screen.
For some reason the login screen menu,under administration won't open.(it goes starting,then nothing)
Is there maybe a command i can use ? 

Thank you:-k

---

### Post by jd65pl on 2006-11-07
Try

```
gksu gdmsetup
```

Does it return any errors in the terminal?

---

### Post by BitTorrentBuddha on 2006-11-07
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure gdm
```

---

