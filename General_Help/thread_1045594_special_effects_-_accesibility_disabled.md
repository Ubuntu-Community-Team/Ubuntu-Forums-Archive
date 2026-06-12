---
title: "special effects - accesibility disabled?"
date: 2009-01-20
forum: General Help
---

### Post by TrevorFamous on 2009-01-20
I downloaded the thing that lets me adjust special effects, but it says "Accesibility - Disabled" how do I fix this to enabled?

---

### Post by gettinoriginal on 2009-01-21
Go to System, Preferences, Appearance, Visual Effects, and select Extra or Custom.  :p

---

### Post by TrevorFamous on 2009-01-22
Thats another thing.
I can't. It doesn't let me. A message pops up saying I don't have the correct authorization. I'm the only account other than root.

---

### Post by ellalan on 2009-01-22
You could try enabling simple ccsm in synsptics,then try changing the visual effects to normal,custom or extra.
Most of the compiz effects will work with "normal"

---

### Post by gettinoriginal on 2009-01-22
Try this, go to System, Administration, Users/groups, it should list you and root, root will be greyed out. Hightlight it and choose unlock (should ask for your password), then modify and add yourself to the "root" group by checking both boxes.

---

### Post by TrevorFamous on 2009-01-22
> **gettinoriginal said:**
> Try this, go to System, Administration, Users/groups, it should list you and root, root will be greyed out. Hightlight it and choose unlock (should ask for your password), then modify and add yourself to the "root" group by checking both boxes.

just did it. It doesn't help out.

> You could try enabling simple ccsm in synsptics,then try changing the visual effects to normal,custom or extra.
Most of the compiz effects will work with "normal"
explain. no idea what simple ccsm is. I'm new to the linux/ubnuntu scene. btw. I get this error message when trying to enable it now.

> Desktop effects could not be enabled. 

Maybe it's because I did safe graphics mode when installing? Not sure.

---

### Post by ellalan on 2009-01-23
> **TrevorFamous said:**
> just did it. It doesn't help out.


explain. no idea what simple ccsm is. I'm new to the linux/ubnuntu scene. btw. I get this error message when trying to enable it now.

 

Maybe it's because I did safe graphics mode when installing? Not sure.
System->Administration->Synaptic Package Manager
Type simple ccsm in the search box and tick the box on the left to install.

---

### Post by gettinoriginal on 2009-01-23
This should give you admin permissions.  Open a terminal and enter the following:

```
sudo adduser **your_user_name** admin
```

---

