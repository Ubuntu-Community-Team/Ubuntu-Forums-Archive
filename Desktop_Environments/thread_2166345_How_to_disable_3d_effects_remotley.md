---
title: "How to disable 3d effects remotley"
date: 2013-08-08
forum: Desktop Environments
---

### Post by justanotherjoe on 2013-08-08
So I am having an issue with vnc showing a black screen on my desktop at work that I need to get into, it is running 12.04 unity. One of the common causes of this seems to be having 3d effects enabled but I cant seem to disable that from an ssh shell. Is there any ways to do this from a remote ssh session?

---

### Post by SweetAurora on 2013-08-08
Unfortuantly, you can't disable the 3D effects for Unity as that would disable Unity itself. BUT if you log into Unity 2D on you computer before leaving for work, you should be able to get in. You know how to get into the Unity 2D desktop? On the login screen, there should be a white circle near the entry box. Click it and select "Unity 2D". :)

---

### Post by hamishmb on 2013-08-10
Well, this is an idea that might not work: You could theoretically get back into lightdm (desktop manager and selecter) and select Unity 2D by running something along the lines of:

lightdm --test-mode

The test mode allows you to run it as a normal user, rather than root.

Hope this helps.

---

