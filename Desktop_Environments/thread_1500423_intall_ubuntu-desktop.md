---
title: "intall ubuntu-desktop"
date: 2010-06-03
forum: Desktop Environments
---

### Post by philo_71 on 2010-06-03
hi,

i have an 8.04 lts, i want to install ubuntu-desktop.
i do :
sudo apt-get update
sudo apt-get upgrade
-----------------------------------------------------------------------------
sudo atp-get install ubuntu-desktop
...
...
ubuntu-desktop : 
>> depend : seahorse.....
>> depend : yelp....
>> recommand : gnome-user-guide
>> recommand : ubuntu-docs
>> E: packet failed .........
--------------------------------------------------------------------------------
sudo apt-cache search ubuntu desktop 
>> ubuntu-destop found !
>> kubuntu found !
>> more....

then i tried :
sudo apt-get install kubuntu-desktop..
>> it's works, i do <ctrl+c>
>> because i want ubuntu-desktop
********************************************************************************
can i do about seahorse and yelp this on errors packets,
how can i restore seahorce and yelp ?


Best regards
Philo

---

### Post by wojox on 2010-06-03
Try a

```
sudo apt-get dist-upgrade
```

---

### Post by philo_71 on 2010-06-03
> **wojox said:**
> Try a

```
sudo apt-get dist-upgrade
```

i do :
apt-get dist-upgrade
>> 0 install 0 remove 0 update 
>> do nothing !!


best regards
philo

---

### Post by wojox on 2010-06-03
What Desktop are you running now?

---

### Post by philo_71 on 2010-06-03
> **wojox said:**
> What Desktop are you running now?
>> kubuntu i thing can runnig but i don't install it !
>> edubuntu have a  errors about depand  ubuntu-desktop..

>> i hope to answer at your question !



best regards
philo

---

