---
title: "swap file usage always at 0%, is it disabled?"
date: 2008-12-09
forum: General Help
---

### Post by Rubicon421 on 2008-12-09
I recently added a screenlet that shows usage for RAM, CPU and swap file. The RAM and CPU respond as expected to actions that would increase demand on them but the swap always sits at 0% no matter what I am doing. 

How can I test that it is even working, or working right? Could my swap file use be disabled? I have a live CD install of 8.10 64 bit.

---

### Post by logos34 on 2008-12-09
it's possible you have a lot of ram and the system never needs to use it

double check system>admin>system monitor>resources tab

you can do

sudo swapon -a

then check again.  as long as there's a swap entry in /etc/fstab it will activate it

---

### Post by hyper_ch on 2008-12-09
open a terminal, run
```

sudo apt-get install htop

```
then
```

htop

```

and you'll have a nice overview over your system.

---

### Post by mali2297 on 2008-12-09
In a terminal, run
```

free -m

```
Does it report a non-zero total swap? (Look in the last row, first column.)

---

### Post by logos34 on 2008-12-09
> **hyper_ch said:**
> open a terminal, run
```

sudo apt-get install htop

```
then
```

htop

```

and you'll have a nice overview over your system.

yeah, htop is great,  it's what i use--no ram-hogging gui and it makes killing apps easy

---

### Post by MarblePanther on 2008-12-09
Thanks for the recommendation, htop rocks (i always used system monitor)

---

### Post by Rubicon421 on 2008-12-09
I have 4 GB of RAM and system monitor is showing 0 of 1.8GB used for the swap file. So I guess I just have enough RAM that I don't need it. RAM was 850MB of 4GB used.

---

### Post by hyper_ch on 2008-12-09
if you're on 32bit you can't use more than 4gb ram anyway.

---

### Post by kgas on 2008-12-09
The following link will give further information about the swap file usage.

[http://www.cyberciti.biz/tips/linux-swap-space.html](http://www.cyberciti.biz/tips/linux-swap-space.html)

nixCraft is a nice site, keeping good guides to GNU/Linux usage.

---

### Post by oldos2er on 2008-12-09
> **Kill Vista said:**
> I have 4 GB of RAM and system monitor is showing 0 of 1.8GB used for the swap file. So I guess I just have enough RAM that I don't need it. RAM was 850MB of 4GB used.

 I have 2GB RAM, and have never touched swap--and I do have quite a few programs running concurrently.

---

### Post by Slim Odds on 2008-12-09
> **Kill Vista said:**
> How can I test that it is even working, or working right? 

Run every application on your machine (at the same time). You'll get some swapping then!!!

:lolflag:

---

### Post by pietjanjaap on 2008-12-09
Start a movie, Start a movie, Start a movie, Start a movie, Start a movie, Start a movie, Start a movie, etc.
Then after a lot of movies you will see it increase.
I had the same, always 0 ram.

---

