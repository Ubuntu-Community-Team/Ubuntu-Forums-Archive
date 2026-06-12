---
title: "Change Unity Panel Components"
date: 2011-04-21
forum: Desktop Environments
---

### Post by enarsee on 2011-04-21
I have a lot of NTFS partitions and all those partitions when mounted, show up in the panel; and then the panel gets crowded,IS there any way of modifying the panel such that it doesnt show mounted drives and trash (don't) use it much

And also IS there a way to pin Wine Applications on to the panel ?

---

### Post by enarsee on 2011-05-03
Bump

---

### Post by matt_symes on 2011-05-03
Hi

> I have a lot of NTFS partitions and all those partitions when mounted, show up in the panel; and then the panel gets crowded,IS there any way of modifying the panel such that it doesnt show mounted drives and trash (don't) use it much

Yes there is. You have to use either *gconf-editor* and edit the compiz-1 or compizconfig-1 settings or use *dconf-editor* and edit the unity specific settings there. I can't remember exactly which at the moment.

```
sudo apt-get install dconf-tools
```

for the second one.

I am currently booted into 10.04 as i am doing some work. If you can't find out how to change it, bump this thread as i will be booting into Unity later and i will track down the settings for you.

Kind regards

---

### Post by werewolves on 2011-05-03
[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

Under the "Configuration Editor" section.

---

### Post by matt_symes on 2011-05-03
Hi

```
sudo apt-get install dconf-tools
```

start 

```
dconf-editor
```

Navigate to 

/desktop/unity/devices and change to never to hide the mounted drives from the launcher

Kind regards

---

