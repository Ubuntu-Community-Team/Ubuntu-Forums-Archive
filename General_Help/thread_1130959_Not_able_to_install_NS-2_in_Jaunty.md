---
title: "Not able to install NS-2 in Jaunty"
date: 2009-04-20
forum: General Help
---

### Post by rrajath on 2009-04-20
Hi.. I installed NS-2 in Hardy Heron with this tutorial [http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04]("http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04") and it worked.

Now I'm using Jaunty and I tried to install NS-2 and I followed the same steps as in the link pasted above. After all the installation process is done, when I type ns, it says ns is not installed.

Plz help.. Its urgent..

---

### Post by wirelessmonkey on 2009-04-20
From the bottom of your install document:
```

It probably means the environment variables haven't been set correctly. Make sure the ~/.bashrc file has been edited correctly and that it has either been source'd as described above or that the system has been rebooted.

---

This error also occurs when you are still working in the same Terminal. Open a new Terminal and type 'ns' 

```



I went ahead and installed this just to see, and the only thing I had to change besides the bashrc paths was this: ```

cd ns-allinone-2.31/ns-2.31
./validate

```
to do the validation test.

Make sure you open a new terminal after saving your bashrc stuff.

---

### Post by rrajath on 2009-04-20
Thanx a lot. Its working now. I don't know how I overlooked that part.

---

