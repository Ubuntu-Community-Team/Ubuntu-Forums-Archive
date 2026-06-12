---
title: "GTK3 apps are too slow in xubuntu 13.04"
date: 2013-05-31
forum: Desktop Environments
---

### Post by horonitel on 2013-05-31
Hello everyone!

I have a Samsung N145-JP02 netbook with Kingston V300 60GB SSD and 2GB of RAM installed. It works really fast with xubuntu.
The problem is that GTK3 applications run VERY slow. For example, there is an application to change XFCE4 menu contents.
It starts for about 10-12 seconds! Same problem with Transmission. As far as I understand, they all use GTK3.

Just compare - Skype (QT4) starts in 2 seconds, Libreoffice (GTK2) in 4 seconds.
Any ideas how to speed it up? Or it is impossible and I should just replace this apps with their gtk2 alternatives?

---

### Post by dino99 on 2013-05-31
is that netbook able to run a pae kernel ? or have it to use llvm ?
glance at the System Monitor to see which process(es) is/are using too much resources; and maybe the logs could also help you with usefull warnings/errors

---

### Post by horonitel on 2013-05-31
**dino99**, thanks for the answer.
Please make yourself clear about PAE, I do not understand why you mentioned it. As far as I know PAE allows to use >4GB ram on 32-bit operating systems. As I said above, this netbook has only 2GB of RAM. Why do I need PAE kernel?

---

### Post by vasa1 on 2013-05-31
> **horonitel said:**
> .... For example, there is **an application to change XFCE4 menu contents**.
It starts for about 10-12 seconds! Same problem with Transmission. As far as I understand, they all use GTK3.
...
What is the exact name of the first one? What about Evince (Document Viewer)? Does that also take a long time?

---

### Post by horonitel on 2013-05-31
I do not know it's name. I could not find it in ps aux output :-k
Empty evince (no document opened) takes more than libreoffice writer with 1-page docx.

---

### Post by vasa1 on 2013-06-01
Can you try changing themes? What theme are you using now?

---

### Post by dentaku65 on 2013-06-01
Try to install the gtk engines:
```
sudo apt-get install gtk3-engines-xfce gtk2-engines-xfce
```
In my case the applications start instantly

---

### Post by vasa1 on 2013-06-01
> **dentaku65 said:**
> Try to install the gtk engines:
```
sudo apt-get install gtk3-engines-xfce gtk2-engines-xfce
```
In my case the applications start instantly
Xubuntu ships with the necessary engines because the default theme includes gtk2 and gtk3.

---

### Post by dentaku65 on 2013-06-01
> **vasa1 said:**
> Xubuntu ships with the necessary engines because the default theme includes gtk2 and gtk3.
Well is surely true, but on my xubuntu quantal (clean install) those engines were not installed; in any case if you execute transmission-gtk without the engines indicated the launching it takes about 15 seconds, with the engines starts instantly

---

### Post by horonitel on 2013-06-02
Well, I removed unico engines and installed xfce4 engines, which were not installed by default. Also I've changed gtk2/3 theme to zukitwo, now gtk3 apps do not display errors if started from terminal. Now It's a bit faster, but still far from being like gtk2.

---

### Post by dentaku65 on 2013-06-02
> **horonitel said:**
> Well, I removed unico engines and installed xfce4 engines, which were not installed by default. Also I've changed gtk2/3 theme to zukitwo, now gtk3 apps do not display errors if started from terminal. Now It's a bit faster, but still far from being like gtk2.

I'm using the default theme Greybird and the speed is ok, I mean no differences. But I'm using the Dev Xfce from PPA
```
sudo apt-add-repository ppa:xubuntu-dev/xfce-4.10
sudo apt-add-repository ppa:xubuntu-dev/xfce-4.12
sudo apt-get update
sudo apt-get dist-upgrade
```
I don't know if this makes some difference

---

### Post by Nutria on 2013-06-07
> **horonitel said:**
> Hello everyone!

I have a Samsung N145-JP02 netbook with Kingston V300 60GB SSD and 2GB of RAM installed. It works really fast with xubuntu.
The problem is that GTK3 applications run VERY slow. For example, there is an application to change XFCE4 menu contents.
It starts for about 10-12 seconds! Same problem with Transmission. As far as I understand, they all use GTK3.

Just compare - Skype (QT4) starts in 2 seconds, Libreoffice (GTK2) in 4 seconds.
Any ideas how to speed it up? Or it is impossible and I should just replace this apps with their gtk2 alternatives?

Is it just startup that's slow?  What about other video performance?

I'd run the program with strace (*$ strace foobar*) and see if it's hanging somewhere.

If you run the program, kill it and then run it again does it load quickly the second time?  (That would indicate that it has to load oodles of extra libraries just to run this one extra program.)

---

