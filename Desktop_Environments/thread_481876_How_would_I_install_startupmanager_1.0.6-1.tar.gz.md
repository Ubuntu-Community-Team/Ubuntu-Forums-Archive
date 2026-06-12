---
title: "How would I install startupmanager_1.0.6-1.tar.gz"
date: 2007-06-23
forum: Desktop Environments
---

### Post by swoll1980 on 2007-06-23
Help me out please.

---

### Post by Keisad on 2007-06-23
Yay, you get to compile!

First, move startupmanager_1.0.6-1.tar.gz to your desktop.
Than, right click and selevt "extract here". A folder with a similar name will appear on your desktop.
After that, open the command line and go to the directory that was just created on your desktop.
Execute these commands.

```
./configure && make
```

The above could take a while, so be patient.

Once finished, type in the below:

```
sudo make install
```

I believe that will help.

---

### Post by swoll1980 on 2007-06-26
thanks

---

