---
title: "Kubuntu stole my startup and shutdown screens!"
date: 2008-04-26
forum: Desktop Environments
---

### Post by not_surt on 2008-04-26
Very minor problem here:

(I think) after installing the KDE package my nice, warn, golden-brown Ubuntu startup and shutdown screens (logo above progress bar) have been replaced with the cold, sterile, blue Kubuntu ones.

Any ideas where I need to go to get the Ubuntu screens back up there?

---

### Post by scragar on 2008-04-26
[http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/](http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/)

---

### Post by not_surt on 2008-04-26
Cool, thanks.

What was suggested in the blog post itself only did half the job (shutdown, but not startup), but a suggestion in the comments did the job.

What worked:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

