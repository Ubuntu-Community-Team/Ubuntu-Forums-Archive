---
title: "gnomenu 1.9.9 tar.gz"
date: 2009-07-04
forum: Desktop Environments
---

### Post by jayanramesh on 2009-07-04
Dear pals
Could anyone direct me how to intall gnomenu 1.9.9 tar.gz.Help will be very much appreciated.

---

### Post by Kvothe on 2009-07-04
First you need to find the .tar.gz and unzip it. For example, if you downloaded it to your home directory, open up a terminal and type:
```
tar -zxvf filename.tar.gz
```Or just find it and use the GUI. Now you can navigate to the folder you created by typing:
```
cd gnomen*
```While in the program directory, run these three commands:
```
sudo ./configure
sudo make
sudo make install
```And that should take care of it.

---

### Post by jayanramesh on 2009-07-05
Dear Kvothe,
Thank you so much for your invaluable help.I have succeeded installing it with your appropriate direction.

---

