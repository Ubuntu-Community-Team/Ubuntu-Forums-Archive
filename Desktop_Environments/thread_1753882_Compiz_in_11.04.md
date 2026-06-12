---
title: "Compiz in 11.04"
date: 2011-05-09
forum: Desktop Environments
---

### Post by shashanksingh on 2011-05-09
I tried enabling desktop cube with rotate cube in compiz in natty 11.04.
It then requested me to disable desktop wall.

When I did so, the title bar (with the closing and minimizing icons has dissapeared!!

The whole GUI has become unstable. Wierd..

---

### Post by Paddy Landau on 2011-05-09
I believe you can type the following in a terminal to reset the settings and make it stable again:
```
unity --reset
```

---

### Post by sikander3786 on 2011-05-09
These 2 links might be of interest to you.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

This one for enabling cube.

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by mc4man on 2011-05-09
> **sikander3786 said:**
> These 2 links might be of interest to you.
This one for enabling cube.

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

You may want to note that if these plugins get disabled to re-enable
window decoration
place windows
move window
resize window
scale

> 
The first conflict arises between 'Reveal Mode' from 'Ubuntu Unity Plugin' and 'Rotate Flip Left' from 'Rotate Cube'. I would recommend to 'Disable Rotate Flip Left' here as we don't want to disturb Unity.

That is an [erroneous conflict]("https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/774462"), one can use both if desired, reveal is based on cursor bumping left screen edge, flip left uses cursor grab, there is no conflict

---

### Post by shashanksingh on 2011-05-09
> **sikander3786 said:**
> These 2 links might be of interest to you.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

This one for enabling cube.

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

Thank you.
Nice Blog

---

### Post by shashanksingh on 2011-05-09
just for the record, I dont use unity, I want to remove it from my default "ubuntu" session. Even if I remove it from synaptic, the "ubuntu" session has no desktop manager then and gives me a blank desktop.

I have to log in as "ubuntu classic" to use gnome.

Any ideas as to how I can use gnome as my "Default" theme??

---

### Post by sikander3786 on 2011-05-09
> **shashanksingh said:**
> just for the record, I dont use unity, I want to remove it from my default "ubuntu" session. Even if I remove it from synaptic, the "ubuntu" session has no desktop manager then and gives me a blank desktop.

I have to log in as "ubuntu classic" to use gnome.

Any ideas as to how I can use gnome as my "Default" theme??
Logging in once into 'Ubuntu Classic' should always log you in to the Gnome session unless otherwise, you change it back to 'Ubuntu'.

Or you can go to System > Administration > Login Screen and choose your default session.

---

### Post by sikander3786 on 2011-05-10
> **mc4man said:**
> You may want to note that if these plugins get disabled to re-enable
window decoration
place windows
move window
resize window
scale


That is an [erroneous conflict]("https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/774462"), one can use both if desired, reveal is based on cursor bumping left screen edge, flip left uses cursor grab, there is no conflict
Thanks for your kind suggestions. The blog post has been updated :-)

---

### Post by shashanksingh on 2011-05-12
> **sikander3786 said:**
> Logging in once into 'Ubuntu Classic' should always log you in to the Gnome session unless otherwise, you change it back to 'Ubuntu'.

Or you can go to System > Administration > Login Screen and choose your default session.

Is there any way I can change the default desktop manager for a certain session?

---

### Post by sikander3786 on 2011-05-12
> **shashanksingh said:**
> Is there any way I can change the default desktop manager for a certain session?
Yes you can. Which desktop manager you are using and which one you want to use?

---

### Post by shashanksingh on 2011-05-12
> **sikander3786 said:**
> Yes you can. Which desktop manager you are using and which one you want to use?

Im using gnome, and I want it to be the default one for ubuntu.
Ive uninstalled unity but the default ubuntu session is "desktopless"

---

