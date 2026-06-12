---
title: "Installing Unity on lucid lynx, possible?"
date: 2011-08-22
forum: Desktop Environments
---

### Post by resero on 2011-08-22
Hello there from Argentina:
The past 4 months I've been using Ubuntu 11.04 desktop on my laptop  and I really **really liked Unity**. Due other factors (stability, printer drivers issues, Java conflicts) I decided to go back to Lucid Lynx 10.04.3 LTS.
Now I ask you as a linux n00b:
[CENTER][B]It is possible to have my desktop like the Natty default on Lucid?
 ie: run Unity un Ubuntu 10.04.3?[/B]
[/CENTER]
I read all the post about Unity here and found nothing about Unity on lucid. I found the information in unity.ubuntu.com useless.
I believed that after install lucid with something like *sudo apt-get unity* wil do the trick, maybe add some repository at most. But it's not the case.
Now I'm confused it seems that Unity is not a full desktop environment: it works on Gnome 2. I can't find information about Unity on other distributions neither, it looks like a Ubuntu desktop.

---

### Post by Frogs Hair on 2011-08-22
It is possible to install Unity 2D on Ubuntu 10.10 , but I find nothing for 10.04 .[http://www.ubuntugeek.com/how-to-install-unity-2d-on-ubuntu-10-10-maverick.html](http://www.ubuntugeek.com/how-to-install-unity-2d-on-ubuntu-10-10-maverick.html)

---

### Post by MG&amp;TL on 2011-08-22
I want to know about this too...presumably you can manually get a .deb and install it?

---

### Post by sebadov on 2011-08-26
I would like to know how too !! The repository doesn´t work any more

---

### Post by sebadov on 2011-08-27
Help!! We really want to try the controversial "Unity"

---

### Post by kyletstrand on 2011-08-28
I don't care for unity personally, but i found this page that might work:

[http://www.ubuntugeek.com/how-to-install-unity-in-ubuntu-10-0410-10.html](http://www.ubuntugeek.com/how-to-install-unity-in-ubuntu-10-0410-10.html)

It seems to easy, but it may be true:

```
sudo apt-get install unity
```

I don't care to try it myself, but I'm curious to see if it works.

---

### Post by coffeecat on 2011-08-28
> **kyletstrand said:**
> I don't care for unity personally, but i found this page that might work:

[http://www.ubuntugeek.com/how-to-install-unity-in-ubuntu-10-0410-10.html](http://www.ubuntugeek.com/how-to-install-unity-in-ubuntu-10-0410-10.html)

It seems to easy, but it may be true:

```
sudo apt-get install unity
```

I don't care to try it myself, but I'm curious to see if it works.

I believe that will give you the mutter-based version of Unity which was used in 10.10/Maverick, rather than the compiz-based Unity in 11.04. Unity was completey rewritten for 11.04 and is a far better user-interface than the Maverick one, which is missing several features that are there in the 11.04 version. If you liked Unity in 11.04, I don't believe you'll like this version of Unity.

Also, I'm surprised that link suggests that you "sudo apt-get install unity" in Lucid. According to this:

[http://packages.ubuntu.com/search?keywords=unity&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=unity&searchon=names&suite=all&section=all)

... there is no unity package for Lucid. But there is an ubuntu-netbook package for Lucid:

[http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=ubuntu-netbook](http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=names&keywords=ubuntu-netbook)

I suspect the link meant to say that you install ubuntu-netbook in Lucid and unity in Maverick. However, that will give you the Lucid ubuntu-netbook desktop in Lucid, which is not what Unity is now in Natty.

---

