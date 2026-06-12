---
title: "Will Xubuntu 8.04 work on a Dell Latitude-CPi A366XT"
date: 2008-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gyzer on 2008-04-29
Computer Specs:
Processor: 366Mhz PII
RAM: 128MB
Hard Drive: 6.4GB

I'm just wanting to use this laptop for surfing the web.

I've ran a LiveCDs of Xubuntu 8.04 on it and it loaded up and all, but I was unable to really do anything once inside the OS, except move the mouse around. Now I know LiveCDs run alot worse then if the OS was installed on the hard drive but I'm really just wanting to make sure this even has a possibility of working. I can upgrade the system to 256MB of RAM, and I can get a new hard drive those are not a problem.

Any insights or sugestions would be welcomed.

---

### Post by felker2 on 2008-04-29
256 MB and a swap partition would make things much better.

---

### Post by gyzer on 2008-04-29
Yeah thats what I thought. How big of a swap partition should I do? Something as big as 1GB or somewhere between 512MB and 1GB?

---

### Post by GavinZac on 2008-04-29
I've installed it today on a Dell Latitude CPi D300XT so I think it should be ok. Remember to avoid heavy multitasking, and its worthwhile stripping down some things you dont need like other locales, bluetooth or printing or, as is the case with some of these old dells, sound.

Since installation is pretty intensive I'd recommend doing it from the alternative install CD.

---

### Post by kerry_s on 2008-04-29
with those current specs, a low resource distro such as dsl or puppy will work wonders.
first choice would be dsl, it has the lowest requirements.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

puppy's alot heavier.
[http://distrowatch.com/index.php?distribution=puppy&month=all&year=all](http://distrowatch.com/index.php?distribution=puppy&month=all&year=all)

list for old computers.
[http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=ix86&status=Active](http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=ix86&status=Active)

---

### Post by gyzer on 2008-04-29
I'm new to ubuntu. I just installed it on one of my main computers a couple weeks ago but I've been loving it. I just found my wife's old laptop that was runing Win 98 Plus, and I thought that I could make is useful again with Xubuntu.

I am going to be using a DLink DWA-130 USB Wireless draft N network adapter on it, which is what I use on my computer runing Unbuntu (and it works just fine with it), will that work with DSL and ndiswrapper? Can ndiswrapper work with DSL?

Thanks

---

### Post by kerry_s on 2008-04-29
it should, i believe dsl has ndiswrapper installed.

---

### Post by felker2 on 2008-04-29
> **gyzer said:**
> Yeah thats what I thought. How big of a swap partition should I do? Something as big as 1GB or somewhere between 512MB and 1GB?

1 GB would be nice.

---

