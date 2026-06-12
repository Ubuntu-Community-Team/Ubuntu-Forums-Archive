---
title: "How to know which programs are compatibile with the Xfce environment?"
date: 2010-07-22
forum: Desktop Environments
---

### Post by Xenphor on 2010-07-22
When looking for things to download off synaptic, I often see programs that have "Gnome" in the title. Since I'm using Xubuntu, is it not wise for me to use these programs? Some, like the Network Manager, seem like they would be very useful but I'm not sure if using them would harm my Xfce installation. There is also a Gnome Device Manager I would like to use but, again, I'm not sure if that would be the best idea for Xfce. Are there similar programs intended to be used for Xfce? How do I know which ones will work well and which won't?

---

### Post by mcduck on 2010-07-22
Every program you'll see in Synaptic will work.

The question is really about which toolkit the programs use (GTK for Gnome, XFCE and LXDE, and Qt for KDE). While there's no problem running a KDE app in Gnome or XFCE it will result in slightly higher resource use (as you need to load an extra toolkit in addition to what all the ther programs and the desktop environment itself are using) and everything doesn't always integrate with the rest of the desktop that well.

But in the end you really are free to run anything you'll see in Synaptic. Some apps will integrate better with the rest of your desktop, some not that well, but everything will work.

---

### Post by Xenphor on 2010-07-22
Is there a way to filter search results in Synaptic to only show programs that were made with the Xfce toolkit to insure maximum performance in Xubuntu? It just seems odd that I can use Xubuntu but end up having quite a few programs that were made for Gnome.

---

### Post by mcduck on 2010-07-22
> **Xenphor said:**
> Is there a way to filter search results in Synaptic to only show programs that were made with the Xfce toolkit to insure maximum performance in Xubuntu? It just seems odd that I can use Xubuntu but end up having quite a few programs that were made for Gnome.

XFCE, LXDE and Gnome all use the same toolkit, GTK.

---

### Post by Xenphor on 2010-07-22
Oh sorry I read your post wrong. It's the KDE programs that could pose some problems? So anything with Gnome in the title should be fine to install on Xfce?

---

### Post by mcduck on 2010-07-23
> **Xenphor said:**
> Oh sorry I read your post wrong. It's the KDE programs that could pose some problems? So anything with Gnome in the title should be fine to install on Xfce?

yep. And it's not even that you should avoid KDE apps at all costs, if there's some app you really like then use it, you will end using a bit more RAM but unless you are on a really low-end machine you probably won't notice anything else that that the app doesn't use the same theme as the rest of your desktop.

---

### Post by Dave68 on 2010-07-23
The gist of it is, that in Ubuntu, or it's derivitives, XFCE has a lot of Gnome Dependencies. KDE will work, but it is not really optimised for XFCE, if I understand correctly.
 
Dave

---

### Post by malspa on 2010-07-28
My KDE apps seem to work fine in Xfce.

---

