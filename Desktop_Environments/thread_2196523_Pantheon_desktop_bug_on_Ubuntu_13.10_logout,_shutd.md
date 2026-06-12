---
title: "Pantheon desktop bug on Ubuntu 13.10: logout, shutdown, restart buttons don't work"
date: 2013-12-30
forum: Desktop Environments
---

### Post by Profetak on 2013-12-30
Hello!
I installed Pantheon desktop environment on Ubuntu 13.10 with these command lines:
# sudo apt-add-repository -y ppa:elementary-os/daily
# sudo apt-get update
# sudo apt-get install elementary-desktop

Now the log out, restart and shutdown buttons don't work. I have to shutdown using the terminal. 
These buttons still work in Unity desktop though.

Thanks in advance!

---

### Post by Frogs Hair on 2013-12-30
Check the configuration editor session menu options . I don't remember if Pantheon has its own because I haven't installed it since 12.10, but in Ubuntu it is the dconf editor . Desktop PPA's often have problems because they are not officially supported keep this in mind when experimenting with them.

---

