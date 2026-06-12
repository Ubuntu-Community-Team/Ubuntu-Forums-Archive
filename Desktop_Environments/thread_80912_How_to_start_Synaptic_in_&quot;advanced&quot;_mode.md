---
title: "How to start Synaptic in &quot;advanced&quot; mode?"
date: 2005-10-23
forum: Desktop Environments
---

### Post by kananga on 2005-10-23
How can I set Synaptic so it always launches in the "advanced" mode?

---

### Post by heart_reaver on 2005-10-23
Didn't get whcih mode you are asking for.
If its smart update you are looking to set as default you can 

System>>Synaptics>>Settings>>Prefrences>>

Make system upgrade : Smart Update

if its some thing else, make more details or attach screenshot for what you are asking for

---

### Post by kananga on 2005-10-23
Synaptic starts in a basic mode to begin with, and then you have to go to File > Advanced to switch to the advanced mode. I want to bypass this step and have it just launch directly in this advanced mode.

---

### Post by DarkAngel88 on 2005-12-11
Sorry for wakin' up an old thread.. but I was looking for the same issue and I found it !

So if anybody want's to know how to start Synaptic in "advanced" mode, it's pretty easy : 

```
sudo synaptic
```

---

### Post by aysiu on 2005-12-11
Advanced:
```
gksudo synaptic
```

Simple:
```
gksudo gnome-app-install
```

---

### Post by anil_robo on 2005-12-11
You can change the properties of your "add applications" menu launcher by smeg.

Open a terminal window, type ***sudo smeg*** and press enter. In the window that comes up, find "add applications" shortcut. Double click it, edit the command to be "sudo synaptic". That way, whenever you click on it, you'll start in advanced mode always.

---

