---
title: "Ubuntu becomes Kubuntu"
date: 2008-08-21
forum: Desktop Environments
---

### Post by jvincent08 on 2008-08-21
I've been using Ubuntu for a while and I was curious to try out KDE 4 (the last time I tried it, it was 3.x), so instead of installing Kubuntu, I simply installed the KDE packages with Synaptic. After deciding I still liked Gnome better, I removed every KDE package I could find, with the exception of some libraries that were needed for a few KDE apps I use. Now while the computer is booting, I get a blue "Kubuntu" loading screen, instead of the Ubuntu one. I didn't know installing KDE packages would affect the boot screen. How can I get it back? TIA

---

### Post by tuxxy on 2008-08-21
[Heres a guide]("http://technofreakatchennai.wordpress.com/2006/12/22/switching-between-ubuntukubuntuxubuntu-uspalsh/") to selecting which splash you want,

---

### Post by tangibleorange on 2008-08-21
> **jvincent08 said:**
> I've been using Ubuntu for a while and I was curious to try out KDE 4 (the last time I tried it, it was 3.x), so instead of installing Kubuntu, I simply installed the KDE packages with Synaptic. After deciding I still liked Gnome better, I removed every KDE package I could find, with the exception of some libraries that were needed for a few KDE apps I use. Now while the computer is booting, I get a blue "Kubuntu" loading screen, instead of the Ubuntu one. I didn't know installing KDE packages would affect the boot screen. How can I get it back? TIA

i can suggest only these three commands:

```
sudo apt-get purge kubuntu-artwork-usplash
sudo apt-get install usplash-theme-ubuntu
sudo update-initramfs -u
```

---

### Post by jvincent08 on 2008-08-21
Thanks guys! The commands tangibleorange provided did the trick.

---

### Post by oni5115 on 2008-08-22
Is there a guide to making your own splash theme?

---

### Post by 73ckn797 on 2008-09-14
Thanks for the information on usplash.

I had the very same issue and though it was not something that was of a critical nature, it was a minor irritant. 

I have been exploring the Xfce and KDE environments and really prefer Gnome. With the exception of the Thunar File Manager, Gnome has all that I need.

Thunar does what I need for multiple file renaming and archiving (zip) in a simple and all-in-one environment. I upload over 25,000 photos a year and with Thunar I do not have to switch between several applications to accomplish all that I need to do.

Again, thanks for the information.

A little searching will usually find the answers to questions about the Ubuntu experience.

---

