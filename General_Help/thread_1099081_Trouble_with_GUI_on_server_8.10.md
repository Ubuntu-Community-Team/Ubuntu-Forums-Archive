---
title: "Trouble with GUI on server 8.10"
date: 2009-03-17
forum: General Help
---

### Post by SomeRandomDude on 2009-03-17
Hello,
Ok to start with I am very new to linux and am trying to install ubuntu server 8.10 for a class and I (along with the rest of the class) are having trouble getting the gnome to install. 

I tried the command "sudo apt-get install gnome" and "sudo apt-get install ubuntu-desktop" and I keep getting "E: Couldn't find package gnome"

Now I do have the server cd in as well as having the computer plugged into the network...

Well, I appreciate any help. Thanks,
Dave

---

### Post by taurus on 2009-03-17
Did you remember to run **sudo apt-get update** first?

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

