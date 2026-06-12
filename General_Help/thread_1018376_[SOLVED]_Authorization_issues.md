---
title: "[SOLVED] Authorization issues"
date: 2008-12-22
forum: General Help
---

### Post by shortylonglegs on 2008-12-22
When I open things like the sessions or users tools from System > Administration, there is a box that says 'unlock' which normally lets me change the settings after clicking it and entering my password.  This box is now greyed out and so I can't change these settings.  I was also having trouble with synaptic, but just restarting x cleared that up, but I suspect they are related, because these issues started at the same time.  The error I got with synaptic said something along the lines of 'could not copy user authorization file'  I don't get any errors on the other things, it just won't let me change any settings.  Any ideas?

---

### Post by eBoxNet on 2008-12-22
did you reboot your system?

---

### Post by shortylonglegs on 2008-12-22
Yes, rebooted and no change.  I also just tried starting x as root, to check if it worked there, but the 'unlock' button was still grayed out there too.

---

### Post by eBoxNet on 2008-12-22
did you try to add another user account on your system and check if you have the same prob?

(i am just thinking out loud)

---

### Post by eBoxNet on 2008-12-22
i hope this will solve your problem : [http://ubuntuforums.org/showthread.php?t=481167](http://ubuntuforums.org/showthread.php?t=481167)

---

### Post by shortylonglegs on 2008-12-22
That other thread didn't solve it, and I don't have any other accounts on my computer as of now.  How can I create a new user from the shell?  I know there's useradd, but I couldn't get it to add the user with root access.

---

### Post by eBoxNet on 2008-12-22
```
sudo useradd -G admin newusername
```

---

### Post by shortylonglegs on 2008-12-22
Ok, I'm having the exact same problem with the other account too.

---

### Post by eBoxNet on 2008-12-22
what ver do you have?

try this one : [http://ubuntuforums.org/showthread.php?t=844313](http://ubuntuforums.org/showthread.php?t=844313)

---

### Post by shortylonglegs on 2008-12-22
That last thread is the same problem I'm having, but there isn't a solution there.  
I have Ubuntu 8.10 installed. 
I have to go, but thanks for all the help so far.

---

### Post by eBoxNet on 2008-12-22
did you try to run users-admin in terminal ? (no sudo)
post the output.

---

### Post by eBoxNet on 2008-12-22
try this :

- In terminal: sudo polkit-gnome-authorization
- Within the Authorizations window select "Manage system configuration"
- Under "Implicit Authorizations", click on Edit.
- By default Anyone and Console are set to "No", and Active Console is set to "Admin Authentication". Change Console to "Admin Authentication".

---

### Post by shortylonglegs on 2008-12-22
Ok, the polkit-gnome-authorization thing worked.  Thanks so much for all the help.

---

