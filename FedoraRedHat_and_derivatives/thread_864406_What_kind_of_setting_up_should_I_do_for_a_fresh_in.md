---
title: "What kind of setting up should I do for a fresh install of Fedora 8 or 9?"
date: 2008-07-19
forum: Fedora/RedHat and derivatives
---

### Post by Redrazor39 on 2008-07-19
Do I need to set up repos and stuff like openSUSE? Where can I find drivers if my hardware doesn't completely work?

I really need some explanation. Preferably for fedora 8 because I don't like fedora 9.

---

### Post by John.Michael.Kane on 2008-07-19
Fedora 8-9 Installation Guides
[http://www.mjmwired.net/resources/mjm-fedora-f9.html](http://www.mjmwired.net/resources/mjm-fedora-f9.html)
[http://www.mjmwired.net/resources/mjm-fedora-f8.html](http://www.mjmwired.net/resources/mjm-fedora-f8.html)
[http://www.my-guides.net/en/content/view/91/26/](http://www.my-guides.net/en/content/view/91/26/)
[http://www.my-guides.net/en/content/view/103/26/](http://www.my-guides.net/en/content/view/103/26/)

Also without knowing exactly what your hardware is, and what problems you might be experiencing, it will be hard for anyone to help you.

---

### Post by Redrazor39 on 2008-07-19
Thanks! Just for reference, I'm running a Sony VAIO VGN-sz430n. I've had problems with my Fn keys, fingerprint scanner, webcam, memory stick reader, and suspend/hibernate in multiple linux distros (haven't tried fedora yet)

---

### Post by John.Michael.Kane on 2008-07-19
> **Redrazor39 said:**
> Thanks! Just for reference, I'm running a Sony VAIO VGN-sz430n. I've had problems with my Fn keys, fingerprint scanner, webcam, memory stick reader, and suspend/hibernate in multiple linux distros (haven't tried fedora yet)

Forum members would need to know the makers/model of the devices in question. 

As for finding out if your hardware is detected by the distro you are running, or the distro you test. 

You can check by running either command listed below.

```
lshw -short
```

```
lspci -nn
```

---

### Post by Redrazor39 on 2008-07-19
I see. Thanks for the commands. Those will work in Fedora's terminal, right?

---

