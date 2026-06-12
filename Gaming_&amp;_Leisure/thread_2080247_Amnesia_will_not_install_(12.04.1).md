---
title: "Amnesia will not install (12.04.1)"
date: 2012-11-03
forum: Gaming &amp; Leisure
---

### Post by FinalSlam on 2012-11-03
Hey, I am trying to install Amnesia from the Ubuntu Software Center, and it finishes the download, but it does not install. Any help would be appreciated. :)

---

### Post by Carborundum on 2012-11-03
> **FinalSlam said:**
> Hey, I am trying to install Amnesia from the Ubuntu Software Center, and it finishes the download, but it does not install. Any help would be appreciated. :)
If the purchase completed, Amnesia should be in your software sources. Try running ```
sudo apt-get install amnesia
```
It should give you some details on what is happening. Post the terminal output here.

---

### Post by FinalSlam on 2012-11-03
> **Carborundum said:**
> If the purchase completed, Amnesia should be in your software sources. Try running ```
sudo apt-get install amnesia
```It should give you some details on what is happening. Post the terminal output here.
That command worked. Thank you very much, sir.
Also, I was trying out other ubuntu-based distros, like Kubuntu and Xubuntu. I'm sticking with Ubuntu 12.04. Best FPS by far.

---

### Post by Zeven on 2012-11-03
> **FinalSlam said:**
> That command worked. Thank you very much, sir.
Also, I was trying out other ubuntu-based distros, like Kubuntu and Xubuntu. I'm sticking with Ubuntu 12.04. Best FPS by far.

FPS meaning frames per second in this case, correct? Xubuntu is known to be a low requirements operating system, and yet you get better frames per second in Amnesia: The Dark Descent with Ubuntu?

---

### Post by holastickboy on 2012-11-03
Window managers can definitely effect your Frames Per Second when gaming in OpenGL.  Weird that you have better FPS with Unity though, all conventional benchmarks put that on the very worst performance, with KDE 4.9 winning all benchmarks with XFCE closely behind.  Have you tried turning off desktop effects before launching your games?

Check out these Phoronix benchmarks to see what I mean

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210beta_desktops&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210beta_desktops&num=1)

---

