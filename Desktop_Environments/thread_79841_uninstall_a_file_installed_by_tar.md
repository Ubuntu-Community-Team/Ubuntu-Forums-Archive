---
title: "uninstall a file installed by tar"
date: 2005-10-20
forum: Desktop Environments
---

### Post by vtec on 2005-10-20
I'm about to install a program that is in a tar. I remember a while ago i saw a command that you run when you do the make install to track what is installed so that it can be uninstalled later. It may even have made it uninstall as a deb. I can't find the thread i read it in. Can anyone refreash my memory on how to do this??

Thanks

---

### Post by RAOF on 2005-10-20
I believe what you're after is checkinstall.
```
sudo apt-get install checkinstall
```
Then, after you've done the ./configure; make, instead of running "sudo make install", you run "sudo checkinstall".  Checkinstall will run make install for you, keep track of where everything's going, build a .deb and install it.  Then you can use apt/synaptic to remove it, just like you would any other package.

---

### Post by vtec on 2005-10-21
Yes that is is. Saw that a while ago and couldn't remember of find it no matter how hard i looked. Thanks:)

---

### Post by David Marrs on 2005-10-21
ooh, that's a very handy little feature. Saves a lot of bother :)

---

