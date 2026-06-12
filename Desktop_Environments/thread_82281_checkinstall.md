---
title: "checkinstall"
date: 2005-10-26
forum: Desktop Environments
---

### Post by noobgr on 2005-10-26
hi
i am trying to install a program and when i write sudo checkinstall i take this text

bash: checkinstall: command not found

what to do?:confused:

---

### Post by KingBahamut on 2005-10-26
sudo apt-get checkinstall 

at the base directory for and in which you are installing from source.

---

### Post by kleeman on 2005-10-26
Doesn't sound like it is installed....

sudo apt-get install checkinstall

---

### Post by noobgr on 2005-10-26
when i write sudo apt-get install checkinstall

i get 

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package checkinstall

---

### Post by noobgr on 2005-10-26
ok i solved it.

---

### Post by jrib on 2005-10-26
You have to enable universe, read: [https://wiki.ubuntu.com//AddingRepositoriesHowto](https://wiki.ubuntu.com//AddingRepositoriesHowto)

[edit]ha that's what I get for not refreshing my page before posting, was that the problem or was it soemthing else?

---

