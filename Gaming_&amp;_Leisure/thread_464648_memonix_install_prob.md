---
title: "memonix install prob"
date: 2007-06-04
forum: Gaming &amp; Leisure
---

### Post by silent1643 on 2007-06-04
er i downloaded the tar, unziped to my desktop, and then tried to run the program and bla nothing..

```
./Memonix: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

```

---

### Post by hikaricore on 2007-06-05
I recommend the following method for install:

```
sudo aptitude install libsdl-image1.2
```

```
wget http://www.viewizard.com/linux/debian/memx_1.6-build70327_all.deb
wget http://www.viewizard.com/linux/debian/memx-data_1.6-build70327_all.deb
sudo dpkg -i memx*.deb
```

^_^

---

### Post by silent1643 on 2007-06-05
thanks, that seemed to work

---

