---
title: "Beryl and ATi Radeon 9250 PCI"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by DarkPontiac on 2007-07-14
I have installed Mesa 7.0 Drivers for my ATi Radeon 9250. It says that Direct Rendering is equal to yes.

What I cannot figure out is when when I am scrolling through a website will it lag a whole lot but when I wobble a window it is fine?

I am new to ubuntu and love the 3d effects but they arn't good for web browsing. At first I though it was firefox but it does it in the kde browser to (the one that came with kde when I installed it)

I am running off of 7.04 of Ubuntu and I hate to see that fglrx has dropped support for my card :(

What can I do to fix this? also when I run stuff like glxgears (which only gets about 500 fps... 49 fps with beryl on) or to check the opengl or whatever it says

"libGL warning: 3D driver claims to not support visual 0x4b"

Whats this mean and can I fix it?

Thanks for reading and hope for a reply.

---

### Post by macogw on 2007-07-14
You should be using the open source radeon driver with that card, not mesa...or are you referring to libmesa?

the kde one is called Konqueror, by the way

is Firefox kitchy when you turn off desktop effects too or just when they're on?  That's a pretty old card, so it could just be a matter of the card's limitations with trying to do both at once.  I think there's also a smooth scrolling option somewhere (move down the page in blocks or smoothly)

---

### Post by DarkPontiac on 2007-07-14
> **macogw said:**
> You should be using the open source radeon driver with that card, not mesa...or are you referring to libmesa?

the kde one is called Konqueror, by the way

is Firefox kitchy when you turn off desktop effects too or just when they're on?  That's a pretty old card, so it could just be a matter of the card's limitations with trying to do both at once.  I think there's also a smooth scrolling option somewhere (move down the page in blocks or smoothly)

What is the open sourced drivers? I downloaded the ones from [www.mesa3d.org](www.mesa3d.org). The 7.0 ones.

When the desktop effects are off, it scrolls perfectly, in both browsers. With beryl on, its not only browsers but sometimes even the file explorer seems to lag. 

Smooth scrolling... is that something i find in beryl's option manager? (Sorry but i cannot get on my pc that has ubuntu until later... people are sleeping lol)

---

