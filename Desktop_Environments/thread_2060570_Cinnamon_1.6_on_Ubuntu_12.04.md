---
title: "Cinnamon 1.6 on Ubuntu 12.04"
date: 2012-09-20
forum: Desktop Environments
---

### Post by DEdesigns57 on 2012-09-20
So I just installed the new release of cinnamon 1.6 using the following commands.sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon

Cinnamon was installed but I did get an error about the nemo file manager which is suppose to come with cinnamon 1.6. I got this error during my first first use of cinnamon 1.6 and as a result I seem to be using natalus file manager. Why is this and how can I get nemo? Or does this mean I need to re-install cinnamon?

---

### Post by paulocoghi on 2012-09-26
Just install Nemo, using same repo:

```
sudo apt-get install nemo
```

If this repository does not work, try with **nightly** repo:

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-nightly
sudo apt-get update
sudo apt-get install nemo
```

Please, answer if this solve your problem. :)

---

