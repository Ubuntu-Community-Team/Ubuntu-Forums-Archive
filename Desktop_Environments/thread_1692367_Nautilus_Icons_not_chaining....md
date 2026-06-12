---
title: "Nautilus Icons not chaining..."
date: 2011-02-21
forum: Desktop Environments
---

### Post by Isaacgallegos on 2011-02-21
Not sure why this is happening. I've tried searching for a solution but it's not clear where I went wrong. I wasn't doing any real modifications to anything. 

Attached is a picture of Nautilus not changing with one of the default themes, "High Contrast".

---

### Post by Frogs Hair on 2011-02-21
Here is on going thread , this is affecting a number of users.[http://ubuntuforums.org/showthread.php?t=1575703&highlight=gnome+reverts](http://ubuntuforums.org/showthread.php?t=1575703&highlight=gnome+reverts)

---

### Post by Isaacgallegos on 2011-02-21
Thanks for the link! This is an easy fix. 


> **kanaifu said:**
> 
   1. sudo gconf-editor
   2. /apps/nautilus/preferences/theme
   3.  --> delete "default" string
   4. restart


On #3 just delete the word default and leave it blank! :)

---

