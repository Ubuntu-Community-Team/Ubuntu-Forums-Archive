---
title: "Feisty was fast Ibex slow"
date: 2008-12-26
forum: General Help
---

### Post by cd-r80 on 2008-12-26
Hi! Formatted my Feisty & installed Ibex. It is slow. Hd is all the time crunching. I removed scrollkeeper which was all the time using much cpu. Why I should need that scrollkeeper. What came with Ibex that is slowing my machine? I use Xubuntu.

---

### Post by cd-r80 on 2008-12-27
Login takes 60 seconds. Sad system.

---

### Post by jezsoadam on 2008-12-27
What is your hardware configuration? If you tell me, It can helps to find the solution.

---

### Post by cd-r80 on 2008-12-27
It is old. Celeron 850 Mhz & 128MB RAM.

---

### Post by gTinker on 2008-12-27
> **cd-r80 said:**
> It is old. Celeron 850 Mhz & 128MB RAM.

It is always a good idea to read the release notes for an operating system before one tries to install it.

> 8.10 Release Notes
System Requirements
 The minimum memory requirement for Ubuntu 8.10 is 256 MiB of memory. (Note that some of your system's memory may be unavailable due to being used by the graphics card.)

That's why you see all the "crunching", it's busy swapping all the time. And "minimum" usually runs but doesn't always give the best user experience.

---

### Post by cd-r80 on 2008-12-27
I had in my mind that Xubuntu is still lightweight distro, but not anymore then. What makes it need more memory?

---

### Post by jezsoadam on 2008-12-27
You should buy some ram (256/512MB, much is better), but I think you only can buy used ones for that computer. Be care for the type of the RAMs (SD/DDR). I think it's SD, but I'm not sure, so you should check it.

I think Xubuntu will be slow too, but It will be a little bit faster than Ubuntu. Perhaps LXDE, or fluxbox, but more memory can be the best choise....

---

### Post by tjwoosta on 2008-12-27
in my experience a debain base install is much much lighter weight then ubuntu, yet it is still very familliar feeling to ubuntu users (since ubuntu is based on debain)

---

### Post by cd-r80 on 2008-12-27
Yes I have there extra 128 MB. Sad is that Feisty was faster, and needed only 128 MB. I haven't seen yet what Ibex makes better than Feisty and I mean in Xubuntu. Is that kernel compiled with too much things on it or what? If so I compile my own?

---

### Post by albinootje on 2008-12-27
> **cd-r80 said:**
> I had in my mind that Xubuntu is still lightweight distro, but not anymore then. What makes it need more memory?

Can you try fluxbox and icewm ?
If you're the only user on your machine, then read some more about starting X from the command-line, and then you can remove the graphical display manager.

---

### Post by cd-r80 on 2008-12-27
In Mandrake it was only StartX from console.. Is it more complicated in Ubuntu? Does it help a lot to remove GDM? Feisty had it too.

---

### Post by albinootje on 2008-12-27
> **cd-r80 said:**
> In Mandrake it was only StartX from console.. Is it more complicated in Ubuntu? Does it help a lot to remove GDM? Feisty had it too.

If you want to use "startx", you will need to edit ~/.xinitrc if you want something else than the default desktop (xfce4 in your case).
It's not so clear to me why Intrepid would need more resources than Feisty, but my impression is that the Gnome desktop started to use more software which is started at the startup of X.
In Gnome you choose what you don't want in your gnome-session startup (for example bluetooth stuff).
I don't know how that would work in xfce4, but I assume it's possible and not too difficult too.

---

### Post by cd-r80 on 2008-12-27
I will Investigate that gdm thing. If it is that what makes problems.

---

### Post by tjwoosta on 2008-12-27
i highly doubt that removing gdm will speed up your computer that much, you best options are to either add more memory or find a much lighter weight distro

---

### Post by albinootje on 2008-12-27
> **tjwoosta said:**
> i highly doubt that removing gdm will speed up your computer that much, you best options are to either add more memory or find a much lighter weight distro

+1 I Agree.
Unfortunately RAM for older machine is quite a bit more expensive than for newer machines, but on a machine like that I'd personally prefer to have 512 Mb of RAM.

Depending on what you need from a web-browser, you can also try a more light-weight browser like kazehakase, galeon, epiphany-browser, or even links2 (start with : links2 -g and read the documentation) or dillo.

Thunderbird is a cool email-client, but pretty heavy.
I think Evolution is also relatively heavy.
Claws-mail, balsa and sylpheed are much lighter.

---

### Post by cd-r80 on 2009-01-06
No help with xdm. I installed Hardy. It feels & logs in faster.

---

