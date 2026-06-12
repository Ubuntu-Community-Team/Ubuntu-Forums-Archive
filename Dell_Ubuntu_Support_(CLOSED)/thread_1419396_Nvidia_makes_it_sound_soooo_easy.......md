---
title: "Nvidia makes it sound soooo easy......"
date: 2010-03-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nc-kane on 2010-03-01
I downloaded the recommended v96 drivers for my nvidia mx4000 graphic card and all went well. 
No error messages or prompts telling me the install was aborted, cancelled, removed, or otherwise. I go to bed that night happy. 
I go to access my nvidia console under the administration menu and I get this message:

You do not appear to be using the NVIDIA X driver.
 Please edit your X configuration file
 (just run `nvidia-xconfig` as root), and restart the X server. 

*Wasn't that the driver I downloaded & installed in synaptic!?*
Just run it as root in what? 
The terminal? 
How do I get to this "root"?
What is it talking about?

---

### Post by wojox on 2010-03-01
Sure open the terminal and 

```
sudo nvidia-xconfig
```

Then enter your password, remember you won't see it as echo is off.

---

### Post by nc-kane on 2010-03-01
Thanks. Man that was quick. 
I typed it in & this is what came up:

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

I don't mean to come off so dense, but I get the feeling I'm missing something?

---

### Post by nc-kane on 2010-03-01
never mind.... :oops:
 I rebooted for another installation & that took care of it. 
Thanks :-D

---

