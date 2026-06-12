---
title: "Installing Kate"
date: 2005-07-27
forum: Desktop Environments
---

### Post by ubuntuubuntu on 2005-07-27
I wanted to install Kate but the installation program said that I hadn't installed KDE. Is it really necessary to install KDE in order to use Kate? If so, could someone explain me (please, step by step, because I haven't got used to Linux) how I install KDE?
Thanks.

---

### Post by SGC on 2005-07-28
Before installing kde, try to install kate with apt-get, from the terminal run the following command:
```
sudo apt-get install kate kate-plugins
```

That should install kate with all of it's dependencies , but if that does not works for you then, you can install kde (Kubuntu) with this command:
```
sudo apt-get install kubuntu-desktop
```

---

