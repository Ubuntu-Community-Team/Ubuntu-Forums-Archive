---
title: "Debian based + KDE + Non- bloated + Fast Linux distro?"
date: 2006-08-02
forum: Debian
---

### Post by lzfy on 2006-08-02
Hi, I really like KDE but i haven't found a good KDE distro to use. Kubuntu is Non- bloated + Debian based, but it's slow and buggy.
Mepis is also debian based and fast, but I think it's very bloated.

So is there any other distro that I can use? Maybe I should install Debian, is it hard to install?

---

### Post by tkjacobsen on 2006-08-02
Debian is pretty easy to install. Just don't choose to install graphical desktop environment - that will give you a gnome desktop, instead do it later manually. I'll suggest using the netboot installer - else you have to install a lot of cd's. I'll also suggest installing the testing branch - 'etch'.


[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

---

### Post by RavenOfOdin on 2006-08-02
Etch is good if you want software that is lagging behind on security updates to go along with your nice bootsplash screen.  They recently formed a secure testing team for it but I think it still has a way to go.  I'd like to see it when its done however.

If you're running a server or just like stable software, use Sarge. 

For either Sarge or Etch, you can indeed choose a graphical desktop environment from the list of predefined packages, just take out "gnome" and "gdm" through Aptitude during the apt process with the '-' key.  I did that and it didn't stick me with a GNOME desktop.

---

### Post by Jucato on 2006-08-02
I guess it depends on what your priorities are. It also depends on what you mean by "bloat". I'm presuming you take "bloat" to mean as having many stuff installed or to many icons on the toolbar.

If you think that speed is more important than "bloat", go with MEPIS 6, and just remove/ignore what you don't want from the K Menu and the toolbars. It just takes a few minutes. MEPIS 6 doesn't have a sort of kubuntu-desktop metapackage that will be removed if you install some of the default applications.

However, if you prioritze non-bloat over speed, then just go with Kubuntu, and tweak it as much as you can to improve performance. Honestly, I haven't that been successful in that area. :(

I don't have any experience with Debian, much less Debian Etch. But I heard that it's quite "stable" to use as a desktop OS, but not for mission-critical systems. But still, it's not the stable release. The next Debian stable release will be in December. :p

---

### Post by RAV TUX on 2006-08-02
Knoppix 5.0

---

### Post by Iandefor on 2006-08-02
My recommendation would be to get Mepis, and manually disable the services you don't want. Or, you could install something like Debian base and then build up from that.

---

### Post by Jucato on 2006-08-02
> **yozef said:**
> Knoppix 5.0

Err... If he thinks MEPIS 6 is already bloated, how much more KNOPPIX?

I've always seen KNOPPIX **not** as a desktop distro, but more of a live/rescure/portalbe CD distro. Some swear by Kanotix, though, which is KNOPPIX based, too.

---

### Post by RAV TUX on 2006-08-02
> **Fenyx said:**
> Err... If he thinks MEPIS 6 is already bloated, how much more KNOPPIX?

I've always seen KNOPPIX **not** as a desktop distro, but more of a live/rescure/portalbe CD distro. Some swear by Kanotix, though, which is KNOPPIX based, too.

You can install Knoppix, but you may be right:

[x-evian]("http://www.x-evian.org/")is both Knoppix and debian based, very good distro overall with minor tweaking needed.

---

### Post by lzfy on 2006-08-03
Thanks for the replies :) Debian sounds very interesting to me. I will test it in VMware to see how it is. Are there any big differences between Ubuntu and Debian? Can you use Ubuntu repo's with Debian?

---

### Post by Jucato on 2006-08-03
Well, no. You can't use Ubuntu repos on Debian, and you can't use Debian repos on Ubuntu. It's going to introduce some dependency problems.

---

