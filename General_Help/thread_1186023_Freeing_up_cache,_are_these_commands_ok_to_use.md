---
title: "Freeing up cache, are these commands ok to use?"
date: 2009-06-12
forum: General Help
---

### Post by uberlube on 2009-06-12
I use the System Monitor addon for my panel and its always bothered me that my mem display is constantly green top the top with cashed data. A quick google search got me [this]("http://www.ubuntu-unleashed.com/2008/04/free-up-cache-memory-in-linux.html") result.

Running these commands: 

```
echo 1 > /proc/sys/vm/drop_caches
```
```
echo 2 > /proc/sys/vm/drop_caches
```
```
echo 3 > /proc/sys/vm/drop_caches
```

they sure do wipe out the cache and that tickles me pink, but is this detrimental to the system? Discuss.

---

### Post by uberlube on 2009-06-12
also if they dont do any damage could someone how me a quick script to run this as a 1 click cure.

---

### Post by jacksaff on 2009-06-12
Using all of your memory is a VERY GOOD THING. It means a lot of progrmas are already in memory and so will start very quickly. It doesn't make any other programs slower. They still have to be loaded into memory when they start. It doesn't use more power - the memory chips are drawing power whether the memory is used or not.

---

### Post by uberlube on 2009-06-12
good point. i was more or less talking about the cache built up after im done encoding a dvd and burning it. not much useful stuff built up in that and i loath it sitting in there lol.

---

### Post by dcstar on 2009-06-13
> **uberlube said:**
> good point. i was more or less talking about the cache built up after im done encoding a dvd and burning it. not much useful stuff built up in that and i loath it sitting in there lol.

The Linux kernel manages the resources for the best system performance quite efficiently, some very smart people have put in many thousands of hours (at least....) of work into getting this sort of thing right.

There is nothing to be gained for a user by stuffing around with things like this.

---

### Post by uberlube on 2009-06-13
> **dcstar said:**
> The Linux kernel manages the resources for the best system performance quite efficiently, some very smart people have put in many thousands of hours (at least....) of work into getting this sort of thing right.

There is nothing to be gained for a user by stuffing around with things like this.

hmm well i guess ive been told. wont be using these again.....

---

### Post by lovinglinux on 2009-06-13
> **dcstar said:**
> The Linux kernel manages the resources for the best system performance quite efficiently, some very smart people have put in many thousands of hours (at least....) of work into getting this sort of thing right.

There is nothing to be gained for a user by stuffing around with things like this.

The same old story, which I disagree. There are several threads out there, including one of my own, about decreased system performance when the memory is fully used by the cache.

> **uberlube said:**
> hmm well i guess ive been told. wont be using these again.....

If you are not experiencing any issues when memory is fully used by the cache, then you don't need to free memory like you probably did on Windows. Nevertheless, I do experience performance issues after a while, when the cache is full. So I do clean up the cache memory sometimes, using this command:

```
sudo echo "ready" && sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```

---

### Post by uberlube on 2009-06-13
Im inclined to agree with you about only doing when u see a decrease in performance. Thnx for the code.

---

### Post by jocko on 2009-06-13
> **uberlube said:**
> Im inclined to agree with you about only doing when u see a decrease in performance. Thnx for the code.
I think the decrease in performance you notice when the ram is filled up with cache is because data from ram starts to be swapped to the hard drive, which causes a delay when things that were swapped to the hard drive needs to be read back into ram.
You can tune how aggressive swapping should be by changing "swappiness":
```
gksudo gedit /etc/sysctl.conf 
```
Add this line to the end of the file:
```
vm.swappiness = 10
```
And load the new setting:
```
sudo sysctl -p
```
Swappiness should be a number between 0 and 100, where 100 means things are swapped out very quickly => lots of free memory, but heavy usage of the swap partition, and 0 means things stay in ram as long as possible => high memory usage, but the swap partition is only used if ram is almost full (of other things than cache or buffers).
The default in ubuntu is 60, I keep mine at 0 without any problems.

---

