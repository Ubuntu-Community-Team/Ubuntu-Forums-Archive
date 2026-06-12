---
title: "Wierd bugs after trying LiveCD"
date: 2008-12-10
forum: General Help
---

### Post by wolfgangjt on 2008-12-10
I have Windows Vista Home Basic and a friend told me to try the LiveCD, i did the whole process and after that i popped it in and tried it out (was impressed) and i tried the firefox on it and some other things, well i took it out (by clicking shutdown and hitting enter when it tells me to) and well today when i logged on for the first time after trying it, my internet was VERY laggy. An example is:

Playing CSS and getting 500-1000 PING (usual 50-90) and 14-27 choke (usual 0)

I tried unplugging my modem and router to no avail. This is pissing me off... even looking at sites is slower.

---

### Post by iponeverything on 2008-12-10
> **wolfgangjt said:**
> I have Windows Vista Home Basic and a friend told me to try the LiveCD, i did the whole process and after that i popped it in and tried it out (was impressed) and i tried the firefox on it and some other things, well i took it out (by clicking shutdown and hitting enter when it tells me to) and well today when i logged on for the first time after trying it, my internet was VERY laggy. An example is:

Playing CSS and getting 500-1000 PING (usual 50-90) and 14-27 choke (usual 0)

I tried unplugging my modem and router to no avail. This is pissing me off... even looking at sites is slower.

the ubuntu live CD does not touch your windows installation, as it remains read-only and it has absolutely no power to change the quality of your Internet provider.

---

### Post by wolfgangjt on 2008-12-10
any idea whatsoever? cause this is really weird and my only idea to how this happened was the Ubuntu LiveCD because i did nothing else beside play CSS and download Ubuntu and Burn it Via the burner the guide recommends.

---

### Post by iponeverything on 2008-12-11
I have no idea what is going on with your computer.

What I can tell you is this.  Burning the Ubuntu ISO to CD and booting the CD - running it TOTALLY IN MEMORY without it ever having write access to your windows partition. And then booting back into windows and blaming windows slowness on the Ubuntu live CD -- does not make sense.

---

### Post by blazemore on 2008-12-11
Dude it's totally a coincidence
From the Vista "command prompt" run
```
ipconfig /flushdns
```

Sometimes works. Or try unplugging and plugging in your router.

---

