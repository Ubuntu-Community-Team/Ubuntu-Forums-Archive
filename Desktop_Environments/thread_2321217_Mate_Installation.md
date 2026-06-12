---
title: "Mate Installation"
date: 2016-04-21
forum: Desktop Environments
---

### Post by feartheterrapin on 2016-04-21
I am still on Ubuntu 12.04 with Gnome Classic as my Desktop Environment.  I am looking forward to moving on to 16.04, but not Unity or Gnome.  I know I have two options:
 
 1)  Install Ubuntu-Mate, or
 2)  Install Ubuntu, then Mate, and possibly remove Unity.
 
 I guess I fear missing out on something by not installing the original Ubuntu as I do want a LTS.  Is there some sort of chart comparing what is included in the various flavors of Ubuntu besides the DE?
 
 Any recommendations to my 16.04 installation are appreciated.

---

### Post by vasa1 on 2016-04-21
Ubuntu Mate 16.04 is LTS. It will be supported for *three* years. Regular Ubuntu, the one with Unity, is also LTS but supported for *five* years.

I'm not sure it's a trivial task to "remove" Unity.

---

### Post by feartheterrapin on 2016-04-21
> **vasa1 said:**
> Ubuntu Mate 16.04 is LTS. It will be supported for *three* years. Regular Ubuntu, the one with Unity, is also LTS but supported for *five* years.

I'm not sure it's a trivial task to "remove" Unity.

Thank you for the quick reply.  Knowing the length of LTS for each option is a significant factor.  Thanks.

---

### Post by vasa1 on 2016-04-21
> **feartheterrapin said:**
> ... Is there some sort of chart comparing what is included in the various flavors of Ubuntu besides the DE? ...
AFAIK, there isn't any such chart.

From what I understand, all official flavors share a common core. The differentiation is in the components of the DE.

You can look at
[http://packages.ubuntu.com/xenial/ubuntu-desktop](http://packages.ubuntu.com/xenial/ubuntu-desktop)
[http://packages.ubuntu.com/xenial/xubuntu-desktop](http://packages.ubuntu.com/xenial/xubuntu-desktop)
[http://packages.ubuntu.com/xenial/kubuntu-desktop](http://packages.ubuntu.com/xenial/kubuntu-desktop)
[http://packages.ubuntu.com/xenial/lubuntu-desktop](http://packages.ubuntu.com/xenial/lubuntu-desktop)
[http://packages.ubuntu.com/xenial/ubuntu-mate-desktop](http://packages.ubuntu.com/xenial/ubuntu-mate-desktop)
[http://packages.ubuntu.com/xenial/ubuntu-gnome-desktop](http://packages.ubuntu.com/xenial/ubuntu-gnome-desktop)
to get an idea of how the DEs differ.

I left out kylin because I couldn't find a link for that.

At one time, I had made my own chart to compare a few flavors. Now that I've settled down, I don't bother ;)

---

### Post by feartheterrapin on 2016-04-21
@vasa1

These are useful.  Thanks.

---

### Post by pfeiffep on 2016-04-21
> **feartheterrapin said:**
> I am still on Ubuntu 12.04 with Gnome Classic as my Desktop Environment.  I am looking forward to moving on to 16.04, but not Unity or Gnome.  I know I have two options:
 
 1)  Install Ubuntu-Mate, or
 2)  Install Ubuntu, then Mate, and possibly remove Unity.
 
 I guess I fear missing out on something by not installing the original Ubuntu as I do want a LTS.  Is there some sort of chart comparing what is included in the various flavors of Ubuntu besides the DE?
 
 Any recommendations to my 16.04 installation are appreciated.I've been testing [in separate partitions] both 1 & 2. IMHO you'll be best served by #1. I've had some small annoyances using #2 [although I didn't attempt Unity removal]

Ubuntu Mate will enjoy 3 yrs LTS + 2 years security updates only [there's a slim possibility that some of the MATE bits might have issues in the last 2 years]

---

### Post by vasa1 on 2016-04-21
> **pfeiffep said:**
> ...
Ubuntu Mate will enjoy 3 yrs LTS + **2 years security updates only** [there's a slim possibility that some of the MATE bits might have issues in the last 2 years]
I tried to find some authoritative link on the part in bold but haven't yet. In other words, it seems logical that the security updates should still come through but I'm not sure if there's some sort of blanket action such that once the three years is up, there'll be _no_ updates at all.

Maybe some Xubuntu LTS user can clarify.

---

### Post by Dennis N on 2016-04-21
> **pfeiffep said:**
> Ubuntu Mate will enjoy 3 yrs LTS + 2 years security updates only  [there's a slim possibility that some of the MATE bits might have issues in the last 2 years]  

2 added years of security updates for packages maintained by the MATE team? Could you supply a reference for this claim? If so, seems like you are safe for the full 5 years, security wise.

---

### Post by Dennis N on 2016-04-21
> **vasa1 said:**
> I tried to find some authoritative link on the part in bold but haven't yet. In other words, it seems logical that the security updates should still come through but I'm not sure if there's some sort of blanket action such that once the three years is up, there'll be _no_ updates at all.

Maybe some Xubuntu LTS user can clarify.

You are right - I have Xubuntu 12.04 still running on one computer here and it is getting updates regularly - only the XFCE Desktop and other Xubuntu specific packages are no longer updated (3 years support period). They were rarely updated anyway unless you used a PPA.

---

### Post by pfeiffep on 2016-04-21
> I tried to find some authoritative link on the part in bold but haven't  yet. In other words, it seems logical that the security updates should  still come through but I'm not sure if there's some sort of blanket  action such that once the three years is up, there'll be _no_ updates at all.

I'm not certain this qualifies as 100% authoritative, but it's from the project leader Martin Wimpress in this[ post]("https://ubuntu-mate.community/t/why-can-t-we-get-5-years-support-for-16-04/5098/10")
[COLOR=#b22222][B]Let's clarify this. Traditionally Ubuntu proper  has a 5yr LTS and will do again for 16.04. Most other flavours only  apply for a 3yr LTS. 
[/B][/COLOR]
[COLOR=#b22222][/COLOR][COLOR=#b22222]**16.04 is our first properly official LTS and after some discussion  with members of the Ubuntu Technical Board, we've decided to follow what  most other flavours do which is a 3yr LTS. **[/COLOR]
[COLOR=#b22222][/COLOR][COLOR=#b22222]**What does this mean? We will support Ubuntu MATE 16.04 upto the  16.04.5 release. After that, the Ubuntu MATE bits won't get updates and  fixes but the underlying Ubuntu base will. &#65279;**[/COLOR]

The best I could do ;-)

---

### Post by Dennis N on 2016-04-21
Yes, this is the same policy that has been in place. It will get all the Ubuntu updates, and not just security. But no updates of any kind from the MATE maintainers.

---

