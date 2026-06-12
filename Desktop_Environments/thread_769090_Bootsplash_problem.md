---
title: "Bootsplash problem"
date: 2008-04-26
forum: Desktop Environments
---

### Post by Silvestre on 2008-04-26
Hi,

i have downloaded a themes from gnome-look.org and i have installed it. After that i wanted to change the bootsplash and followed the instructions from a forum:

1) ```
sudo cp ~/Desktop/ejemplo_usplash_theme.so /usr/lib/usplash
```

2) ```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/ejemplo_usplash_theme.so 10
```

3) ```
sudo update-alternatives --config usplash-artwork.so
```

4)```
sudo update-initramfs -u
```

After this 4 steps doesn't work more the bootsplash

Do you know, how i can solve this problem?

Thanks a lot

---

