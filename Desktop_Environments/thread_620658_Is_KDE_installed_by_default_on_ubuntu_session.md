---
title: "Is KDE installed by default on ubuntu session?"
date: 2007-11-22
forum: Desktop Environments
---

### Post by genbuntu on 2007-11-22
Hi

I was just going through the session options (at login screen) and I saw 'KDE' option.  When I chose it, it successfully loaded a desktop environment different from the one that loads by default (gnome). I believe this would be equivalent of 'Kubuntu' (I've never used or installed Kubuntu before). But I always thought that in order to use Kubuntu I would have to go through the install process from the beginning. 
So where did this come from? I don't remember installing any KDE environment etc.
Thanks

---

### Post by -grubby on 2007-11-22
did you install from the Ubuntu DVD? I don't know how elsewise, never used the DVD, but I think it might (since it has all three DEs) have KDE installed along with GNOME

---

### Post by Schalken on 2007-11-22
Also, if you at one point installed the package "kubuntu-desktop" that will pull all the kubuntu stuff (i.e. KDE) along with it, and it is possible that you installed a KDE application that depended on just enough KDE components for you to be able to log into KDE.

However, the most likely cause is that you used an installation media that included KDE as **nathangrubb** said.

---

### Post by genbuntu on 2007-11-22
hmm.. interesting. I think I can safely rule out the installation cd to be the cause , because I used the same cd to install it on my laptop and desktop and the 'KDE' option is missing from my desktop session menu. Also, there is no kubuntu-desktop showing up in synaptic but there are files like 'kdebase-bin' , 'kdebase-dev' etc installed. 
However, sometime ago I did install 'Kword' and as Schalken mentioned , perhaps this could have led to the installation.
I do not intend to use KDE desktop, so how can I remove it?

---

### Post by genbuntu on 2007-11-23
I found a 'kdesktop' installed in synaptic. I think that should be it. Can anyone confirm that uninstalling it would remove the KDE environment safely ?

---

### Post by PeterJS on 2007-11-23
> **genbuntu said:**
> I found a 'kdesktop' installed in synaptic. I think that should be it. Can anyone confirm that uninstalling it would remove the KDE environment safely ?

kdestop is actually the literal kde desktop, the software that displays the wall paper, desktop icons, etc, not the desktop session itself. If it really did get installed as a result of installing Kword, you can safely assume that there is nothing you can safely uninstall. Apt is very good about installing only the bare minimum, and if the desktop session got installed as a dependency it's because something needs it. I would suggest just ignoring it.

EDIT:

The option to log in to KDE is provided by the ksmserver package which is the KDE session manager. Ksmserver isn't a direct dependency of Kword, there's at least a couple packages in the dependency chain, so I couldn't track the connection down.

On a related not does any one know of a tool to graphically represent apt dependency trees? Both for cases like this, and the oh hey isn't that cool factor.

---

### Post by genbuntu on 2007-11-23
okay. Ya, I can see ksmserver installed in synaptic. 
So probably it is best to leave it like that (or atleast until I stop using Kword). 
Thanks for the info.

---

