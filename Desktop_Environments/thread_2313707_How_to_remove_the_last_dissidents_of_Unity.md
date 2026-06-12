---
title: "How to remove the last dissidents of Unity?"
date: 2016-02-15
forum: Desktop Environments
---

### Post by prahladyeri on 2016-02-15
*A short story:*

The governance under my dictatorship in the kingdom of Laptop was easy at the beginning. I hired a prime minister called Ubuntu who did the job well, but as trade started to develop with foreign lands and we had to establish new businesses like *Eclipse, Android sdk, Firefox, php* and a few others, our treasury-minister, Mr. Unity started to show the signs of a retard.

The bloke started having some *memory issues*. He was an eccentric chap to begin with, liked to spend a lot of his mental energy on stuff like fancy clothes, hair style, skin ointments, etc. and just couldn't seem to take some time off for my businesses.

As a result, I just fired Unity and hired a new guy called GNOME in his place. GNOME seemed to do the job well at the beginning. Good thing was that he was not as eccentric as Unity and seemed to spare a lot of time and energy for looking after my trades.

However, this didn't last long as my business started expanding even more. I started receiving critical messages from dignitaries of other kingdoms for which I had to create a sub-system of pigeons and and other local-birds called *thunderbird*. I also started expanding my empire and started allocating some parts of my empire to separate missions called *virtual machines*. Again, GNOME seemed to be buckling under the pressure of increasing number of VMs day by day.

Finally, I decided to send GNOME on an early retirement and decided to hire someone professional this time. Fluxbox is the name of the chap, important thing is that he doesn't seem to come with a bloat of his own *memory issues* and likes to just mind his own business without coming in the way of my trades. The performance is quite satisfactory until now, and all residents of my kingdom are also happy with the management of *Fluxbox*. However, I have one small problem still.

Unity, with the help of some of his faithful soldiers has started a revolt against my kingdom. Finally, I had to use my ultimate weapon called *apt-get purge* to destroy Unity for good. However, some of his dissidents are still causing trouble in some parts of my kingdom. For example, in the *menu* province of Evince town as you can see in [this image]("http://i.imgur.com/k5k7GBR.png").

I just want to know whether there is any way to just find and kill all these last dissidents of Unity without causing any major panic in my kingdom? I would prefer not using my ultimate weapon called `format` which can finish off the dissidents, of course, but also cause a lot of civilian damage which I don't want.

Thanks,

*An Emperor in Dilemma*

---

### Post by sudodus on 2016-02-15
Entertaining story :-D

I think it is easier to start from an Ubuntu mini.iso or an Ubuntu Server iso file, and install only the program packages you want. Generally it is easier to add than to subtract program packages in a linux operating system.

---

### Post by buzzingrobot on 2016-02-15
A number of packages in the repos have as dependencies a very few libraries with the word "unity" in their name.  They'll be there on any non-Unity desktop that uses those packages.

---

### Post by vasa1 on 2016-02-15
From the little I understood of the original post, I'd go with the suggestion made by Sudodus. Clean and simple.

On my system, Lubuntu 14.04 LTS, I see:```
05:59 PM ~ $ dpkg -l | grep -i " *unity*"
ii  gir1.2-unity-5.0:amd64                            7.1.4+14.04.20140210-0ubuntu1           amd64        GObject introspection data for the Unity library
ii  libmeanwhile1                                     1.0.2-4.1ubuntu1                        amd64        open implementation of the Lotus Sametime Community Client protocol
ii  libunity-protocol-private0:amd64                  7.1.4+14.04.20140210-0ubuntu1           amd64        binding to get places into the launcher - private library
ii  libunity-scopes-json-def-desktop                  7.1.4+14.04.20140210-0ubuntu1           all          binding to get places into the launcher - desktop def file
ii  libunity9:amd64                                   7.1.4+14.04.20140210-0ubuntu1           amd64        binding to get places into the launcher - shared library
05:59 PM ~ $ 
```A simulated purge of any of these packages, excluding *libmeanwhile1*, wants to remove *usb-creator-gtk**.

Because I have absolutely no issues with these "unity" packages, I've let them be.

---

### Post by CantankRus on 2016-02-16
Are you sure what you're experiencing is not a coup d'état from those pesky little Gnome usurpers
who of late have been espousing a dictatorship with zero tolerance of foreigners? 8-[

---

### Post by oldos2er on 2016-02-17
For technical questions it's best to eschew obfuscation.

---

### Post by vasa1 on 2016-02-17
> **oldos2er said:**
> For technical questions it's best to eschew obfuscation.
+1.

That's true for every form of bonafide communication.

---

