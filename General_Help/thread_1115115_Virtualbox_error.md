---
title: "Virtualbox error"
date: 2009-04-03
forum: General Help
---

### Post by Ranger1230 on 2009-04-03
When I try to run virtual box I get the error:


Could not create the default settings file '/home/chris/.VirtualBox/VirtualBox.xml' (VERR_ACCESS_DENIED).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
VirtualBox
Interface: 
IVirtualBox {557a07bc-e6ae-4520-a361-4a8493199137}

but if I type in the terminal:
sudo virtualbox

it works fine. do I really have to use the sudo command to run the program? if not what's wrong and how do I fix it?

---

### Post by kestrel1 on 2009-04-03
I think you need to add your username to the virtualbox users group.

Edit:
Use this from the command line:```
sudo usermod -a -G vboxusers youruser
```
youruser = your username.

---

### Post by Ranger1230 on 2009-04-03
I did I look and its there

---

### Post by kestrel1 on 2009-04-03
Try this:```
chown /home/chris/.VirtualBox
```

---

### Post by Ranger1230 on 2009-04-03
thanks that chown /home/chris/.VirtualBox worked great

---

### Post by kestrel1 on 2009-04-03
Just as a bit of an explanation running chown changes the permissions on the folder so that you become the owner.
Why you were not the owner after installing & adding yourself to the vboxusers group is a bit of a mystery, but at least are now up & running.
Any further questions on Virtual Box please do not hesitate to ask.

---

