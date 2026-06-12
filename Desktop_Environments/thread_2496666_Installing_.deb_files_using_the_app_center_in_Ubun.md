---
title: "Installing .deb files using the app center in Ubuntu 23.10"
date: 2024-04-07
forum: Desktop Environments
---

### Post by mike010 on 2024-04-07
Can't install .deb files using the software center is there a fix or work around for this?

Thanks

---

### Post by #&amp;thj^% on 2024-04-07
CLI method
```
dpkg -i /full/path/to/.deb
```
or Gdebi 
```
sudo apt install gdebi
```
Just right click on the downloaded .deb file and select Open with other applications. (And choose gdebi of course)

More on that: [https://itsfoss.com/gdebi-default-ubuntu-software-center/](https://itsfoss.com/gdebi-default-ubuntu-software-center/)

---

### Post by mike010 on 2024-04-07
> **1fallen said:**
> CLI method
```
dpkg -i /full/path/to/.deb
```
or Gdebi 
```
sudo apt install gdebi
```
Just right click on the downloaded .deb file and select Open with other applications. (And choose gdebi of course)

More on that: [https://itsfoss.com/gdebi-default-ubuntu-software-center/](https://itsfoss.com/gdebi-default-ubuntu-software-center/)

I had forgot about gdebi thank you still gonna upgrade to 24.04 as soon as it comes out but this will do in the mean time thank you so much.

---

### Post by ActionParsnip on 2024-04-08
Terminal will give you useful output. You can try to satisfy deps with:
```

sudo apt -f install

```

---

### Post by Dennis N on 2024-04-08
> **mike010 said:**
> Can't install .deb files using the software center is there a fix or work around for this?

Thanks
What exactly happens when you choose a .deb package in the App Center for installation? You need to explain further.

---

