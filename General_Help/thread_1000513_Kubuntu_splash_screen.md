---
title: "Kubuntu splash screen"
date: 2008-12-03
forum: General Help
---

### Post by malel on 2008-12-03
I have got Ubuntu 8.04 and Xfce4 on my machine now . I used to have Kubuntu on it too but I have removed everything Kubuntu except that when I now switch on, the Kubuntu splash screen and progress bar come on the screen. I have tried to locate where it is so that I can remove it manually but so far no luck.
Would appreciate any help in getting rid of this Kubuntu screen . Many thanks

---

### Post by Denestria on 2008-12-03
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure usplash

```

---

### Post by malel on 2008-12-03
Hi Denestria,

Thank you very much for your help. It is just what I wanted and all set now.

Kind regards:D

---

