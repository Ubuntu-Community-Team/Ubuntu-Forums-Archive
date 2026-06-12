---
title: "how to run .exe help pleasssssee"
date: 2009-03-11
forum: General Help
---

### Post by gotenks123 on 2009-03-11
Hi, im at uni and i hav a file, thats a simulation, that need to ru and its a .exe file. im running ubuntu, is there anyway i can run a .exe file?

thank you

---

### Post by yankeeDDL on 2009-03-11
Wine is your best bet. 
Can be installed easily from add/remove.
Note that the performace will be somewhat slow: if the simulation is "CPU intensive", it may take a while.
Ubuntu cannot run Windows' executable (like Windows cannot run Linux's executales).

If you need to do this repeatedly and/or the simulations take several days, you may want to consider installing a VirtualBox with Windows: performance is better.

---

### Post by kidux on 2009-03-11
When I was doing virtual network simulations in my cisco class, I had to run XP in virtualbox to make it go faster. I could run it in WINE, but it was a bit on the slow side.

---

### Post by linuxuser21 on 2009-03-11
It depends on how complex the executable is.

---

### Post by jordilin on 2009-03-11
If this program it's a .NET program, you could run it by means of the mono runtime (which is installed by default in Ubuntu):

```
mono program.exe
```

---

### Post by gotenks123 on 2009-03-11
how do I instal a VirtualBox with Windows?

---

### Post by theozzlives on 2009-03-11
Go to [http://www.virtualbox.org]("http://www.virtualbox.org"). You need the Windows disk.

---

### Post by MaxIBoy on 2009-03-11
First, get a Windows disk. Then, install VirtualBox. Then, create a VirtualBox virtual machine with the Windows disk mounted as the boot drive of the VM, and boot the virtual machine from the Windows disk. Install normally.

---

### Post by mhgsys on 2009-03-11
I just use a dual boot for these things, 
Works better for me then virtualbox or wine.

---

### Post by UbuntuNerd on 2009-03-11
> **gotenks123 said:**
> how do I instal a VirtualBox with Windows?
look at this detail guide [HERE](http://my.opera.com/ubuntunerd1/blog/show.dml/2855482) it shows How to do it step by step

---

### Post by nathang1392 on 2009-03-11
dual-boot is the best way to be sure that you will always have a dependable way to run .exe, but it requires you to have windows in the first place.

---

### Post by mhgsys on 2009-03-11
> **nathang1392 said:**
> dual-boot is the best way to be sure that you will always have a dependable way to run .exe, but it requires you to have windows in the first place.

or on a second disk

---

### Post by carml on 2009-03-11
> **nathang1392 said:**
> dual-boot is the best way to be sure that you will always have a dependable way to run .exe, but it requires you to have windows in the first place.
It's preferable to have Windows in the first place,you'll have less headaches :).

---

### Post by anjilslaire on 2009-03-11
> **carml said:**
> It's preferable to have Windows in the first place,you'll have less headaches :).

heretic, lol

(joke :) )

---

### Post by MaxIBoy on 2009-03-11
I will say that for most stuff, WINE is sufficient. Even for gaming.

So if, in the future, you need to run something a little bit less heavy-duty than a simulation, you can use WINE.

---

