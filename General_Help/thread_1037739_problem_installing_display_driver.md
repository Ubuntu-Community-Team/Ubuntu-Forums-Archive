---
title: "problem installing display driver"
date: 2009-01-12
forum: General Help
---

### Post by Zaki ur Rehman on 2009-01-12
Hi Guys
I just installed ubuntu on my Dell Optiplex. First two installation attemps fails, in third attemp, I select safe graphics mode and at partitioing I select use entire disk. It installed successfully, but display is not good. I cant change it. I download a driver from mesa and install it from terminal, but no results. 
Could anyone guide me what to do????

---

### Post by blazemore on 2009-01-12
If you go to System -> Administration -> Hardware Drivers, there should be a way to install it through there.

---

### Post by Zaki ur Rehman on 2009-01-12
when I go there, it says "no proprietary driver found" 
Do I need to reinstall it without safe graphic mode???

---

### Post by blazemore on 2009-01-12
How did you install the driver you downloaded?
Did you have to compile it?

---

### Post by Zaki ur Rehman on 2009-01-12
I installed it like 
sudo apt-get install autorun.sh

---

### Post by blazemore on 2009-01-12
That's not how it works...
```
sudo chmod +x **filename.sh**
```
```
sudo ./**filename.sh**
```

---

### Post by Zaki ur Rehman on 2009-01-12
Thanx Blazemore
do you means to do this on terminal or this is the right way to install?

---

### Post by adamlau on 2009-01-12
He means both.

---

### Post by Zaki ur Rehman on 2009-01-12
so would I uninstall it first?
on the terminal window, How I know where it is going to install/save? it is not asking anything, so what should I do???

---

### Post by Zaki ur Rehman on 2009-01-12
Hy guys
I tried but nothing happend. Please check the massege when I am trying to change visual effects

---

### Post by DeMus on 2009-01-12
> **Zaki ur Rehman said:**
> Hy guys
I tried but nothing happend. Please check the massege when I am trying to change visual effects

Why you want to install the visual effects? Do you want to change Ubuntu into Windows Vista? I thought using Linux was to get rid of the ugly processor consuming visual garbage.

Use Synaptic Package Manager to install a program called EnvyNG
Look it up in Applications | System Tools
Start it, choose either Ati or nVidia and choose install. It will download and install the latest driver automatically. In a few seconds you are ready to re-boot after which the new driver is in use.

DeMus

---

### Post by Zaki ur Rehman on 2009-01-14
Thanx Demus
Actually my resolution is stucked at 600x480. I need it 1024x768. Because my application need it. Also I cant see the ok or cancel button for most applications because of it.

---

### Post by Zaki ur Rehman on 2009-01-14
I put an AGP card I have and now the problem is solved. Just I need to install nvidia driver.

---

