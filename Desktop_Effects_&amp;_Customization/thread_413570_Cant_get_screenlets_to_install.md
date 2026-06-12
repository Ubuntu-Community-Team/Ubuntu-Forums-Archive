---
title: "Cant get screenlets to install"
date: 2007-04-19
forum: Desktop Effects &amp; Customization
---

### Post by Fireblend on 2007-04-19
I was trying to install screenlets using the following guide:
[http://hendrik.kaju.pri.ee/screenlets/?q=node/5](http://hendrik.kaju.pri.ee/screenlets/?q=node/5)

But after I installed it there's no icon in my accesories menu, nor I can runit with alt  t+f2... help? It does seem to have installed the packages...

---

### Post by reclusivemonkey on 2007-04-19
Did you use the repos or the package? I used the repos and they work fine for me.

---

### Post by juanhunglow on 2007-04-19
> **reclusivemonkey said:**
> Did you use the repos or the package? I used the repos and they work fine for me.

I used the repo but can't get them to work yet.  

Anyone know of any good how-to's on this topic. something basic for those of us that are obviously slower..

---

### Post by reclusivemonkey on 2007-04-19
In a terminal, type

```

screenlets-control

```

and if you don't get the control box up, paste any errors.

---

### Post by juanhunglow on 2007-04-19
> **reclusivemonkey said:**
> In a terminal, type

```

screenlets-control

```

and if you don't get the control box up, paste any errors.

Rebooted and now they work.
Thanks.

---

### Post by water on 2007-04-22
> **reclusivemonkey said:**
> I used the repos and they work fine for me.

I can't find "screenlets" in either Add/Remove or Synaptic (all repo's are checked) are you referring to compiz-extra?

:water

---

### Post by reclusivemonkey on 2007-04-22
> **water said:**
> I can't find "screenlets" in either Add/Remove or Synaptic (all repo's are checked) are you referring to compiz-extra?

:water

Nope, I am referring to the repos listed on the link at the start of the thread. Add them to your /etc/apt/sources.list and you can install with apt-get. Although they seemed to be installed by default in Fiesty.

---

