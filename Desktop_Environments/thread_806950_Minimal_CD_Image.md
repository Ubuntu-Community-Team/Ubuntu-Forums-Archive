---
title: "Minimal CD Image"
date: 2008-05-25
forum: Desktop Environments
---

### Post by Lomz on 2008-05-25
I found the information about Minimal CD images ([https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")) it seems that it is just the Gnome-edition here.
Is it possible to use these images to install ubuntu without Gnome but with Xfce?

---

### Post by bwhite82 on 2008-05-25
Minimal CDs do not come with desktop environments. They install just the base command-line system. From there, you can add whichever DE you wish.

> sudo apt-get install xfce4

---

### Post by mali2297 on 2008-05-25
> 
The Minimal CD uses a text-based installer like the Alternate CD, making the CD image as compact as possible. 


If it is like the Alternate CD, you should have the choice of installing a command-line system. After you've got the command-line system installed, you can then continue to install a basic xfce setup with the commands
```

sudo apt-get update
sudo apt-get install xorg xterm gdm xfce4 firefox gksu synaptic

```

---

### Post by Lomz on 2008-05-26
> **mali2297 said:**
> If it is like the Alternate CD, you should have the choice of installing a command-line system. After you've got the command-line system installed, you can then continue to install a basic xfce setup with the commands
```

sudo apt-get update
sudo apt-get install xorg xterm gdm xfce firefox gksu synaptic

```


Is things like network-manager installed from default?
Is there a difference between the xfce package and the xfce4 package?

---

### Post by mali2297 on 2008-05-26
> **Lomz said:**
> Is things like network-manager installed from default?

You can check what is included in the command-line system here:
[http://packages.ubuntu.com/hardy/ubuntu-minimal](http://packages.ubuntu.com/hardy/ubuntu-minimal)

> Is there a difference between the xfce package and the xfce4 package?

There is no xfce package. That's a mistake from my part, it should have said [xfce4]("http://packages.ubuntu.com/hardy/xfce4").

---

