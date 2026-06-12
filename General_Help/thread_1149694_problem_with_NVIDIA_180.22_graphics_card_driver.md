---
title: "problem with NVIDIA 180.22 graphics card driver"
date: 2009-05-05
forum: General Help
---

### Post by pgngp on 2009-05-05
I have an NVIDIA GeForce 9800 GT graphics card installed on my Dell Optiplex 755. To use this graphics card, I have an NVIDIA 180.22 driver running on my Ubuntu 8.04. Until yesterday the graphics card driver was working fine. But today when I started my computer, I was getting a very low resolution. (Maybe something happened yesterday when I installed the Ubuntu updates.) So after a little searching on the forums, I decided to reinstall the driver NVIDIA-Linux-x86-180.22-pkg1.run. 

Here are the steps I took to reinstall the NVIDIA 180.22 driver:
1) I first stopped the X server:
```
$sudo /etc/init.d/gdm stop
```
2) Then I switched to command-line mode by pressing CTRL+ALT+F1.
3) I logged in using my user name and password
4) I executed the NVIDIA 180.22 driver package for installation and followed the prompts:
```
$sudo sh NVIDIA-Linux-x86-180.22-pkg1.run
```
5) When the driver was reinstalled successfully, I restarted my computer

It then worked just fine like before. 

I hope this post helps those having a similar problem.

---

