---
title: "Compiz"
date: 2009-05-16
forum: Desktop Environments
---

### Post by PhilMize on 2009-05-16
Sooo I'm new to kubuntu and I'm not sure exactly whats up with kde. It seems a little buggy and or hesitant on my lenovo.But it just feels right compared to gnome. So I'm wondering how do I configure compiz in kde? I have synaptic installed and installed compiz, well I think I did. Are there separate versions of compiz? One for kde, one for gnome? Is he reason I can't get it working because I'm running 9.04? On ubuntu 9.04 compiz was all sorts of effed up, but before I switched to kubuntu, I ran ubuntu 8.10 and had everything working perfectly. If anybody could show me a few pointers to kde, is there anything I should be doing? O and for w/e reason pidgin won't stay open when i close it... like it doesn't go to the system tray. Annoying is all really.

Thanks,
:o

---

### Post by Screwdriver0815 on 2009-05-16
when you run Kubuntu Jaunty you actually don't need Compiz because Kwin - the window manager of KDE supports 3d effects by default when you have a graphics driver which supports 3d. Just go into system settings -> desktop -> desktop effects (on the lefthand side). There you can switch on the effects and choose which you want to use.

anyway there is a different compiz for KDE: compiz-kde but I don't know how this works in KDE 4.2 

Pidgin you also don't need (if you have installed it seperatly) because Kopete does the job as good as Pidgin.

---

### Post by krazyd on 2009-05-17
I would also recommend the built-in kwin desktop effects over compiz. It is much more usable and uses less resources than compiz here.

---

### Post by PhilMize on 2009-05-17
yes i had the desktop effects enabled but i rebooted and they are gone and now when i open them i can see they are all enabled but they arnt working...


and kopete is gay because it doesnt support gtalk

---

### Post by krazyd on 2009-05-18
> **PhilMize said:**
> yes i had the desktop effects enabled but i rebooted and they are gone and now when i open them i can see they are all enabled but they arnt working...Do windows go transparent when you drag them?
> **PhilMize said:**
> and kopete is gaylets keep this conversation at a 10yr old + level.
> **PhilMize said:**
> because it doesnt support gtalk[http://wiki.kde.org/tiki-index.php?page=Google+Talk+support](http://wiki.kde.org/tiki-index.php?page=Google+Talk+support)

---

### Post by PhilMize on 2009-05-18
> **krazyd said:**
> Do windows go transparent when you drag them?
lets keep this conversation at a 10yr old + level.
[http://wiki.kde.org/tiki-index.php?page=Google+Talk+support](http://wiki.kde.org/tiki-index.php?page=Google+Talk+support)

*coughs* *clears throat* :-\" errr umm did I say that?

Anyways, I booted it up this morning and it magically works now. But it's a little bit glitchy. Its just not smooth, but it may be because support for my graphics card after 8.10 was dropped.No biggy I'll deal.

---

### Post by krazyd on 2009-05-18
> **PhilMize said:**
> *coughs* *clears throat* :-\" errr umm did I say that?

Anyways, I booted it up this morning and it magically works now. But it's a little bit glitchy. Its just not smooth, but it may be because support for my graphics card after 8.10 was dropped.No biggy I'll deal.
That's good! ;)

What's your graphics card? Radeon HD something?

---

### Post by PhilMize on 2009-05-20
> **krazyd said:**
> That's good! ;)

What's your graphics card? Radeon HD something?


](*,)
Integrated... Intel Chipset I believe...

---

### Post by krazyd on 2009-05-23
That's your problem then. Intel graphics are flaky in Jaunty because the driver is undergoing a major rewrite at the moment. you might have to stick to 8.10 until 9.10, or try something like the xorg edgers ppa.

---

### Post by PhilMize on 2009-05-27
Yea >_> thats what i figured... ugh 9.10 can't come fast enough!

---

