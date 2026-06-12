---
title: "CCSM not allowing changes to settings"
date: 2007-12-26
forum: Desktop Effects &amp; Customization
---

### Post by evilmonkey on 2007-12-26
Hello,

I'm having a problem with CCSM. The short of it is that it does not allow me to change any of my settings. I try to change the number of vertical desktops from 2 to 4, in two seconds, the bar jumps back to 2. I try to enable desktop cube, I put the checkmark in the box, exit ccsm, open it up again, the checkmark isn't there and of course I have no cube.

The interesting thing is that when I run it with sudo (sudo ccsm from konsole), everything works perfectly. But in order to do that, I also have to run compiz as sudo, which I don't want to do because I want to run automatically on startup. So, can anyone tell me what the problem is? Thanks!

---

### Post by Forlong on 2007-12-26
_Never_ run ccsm or compiz (or any other application that doesn't need root privileges) with sudo!

Now you don't have privileges to edit your own config files.
Here's how to revert things:

First make sure you are the owner of every files in your home directory:
```
sudo chown -R $USER:$USER $HOME
```
Then change the permissions, so you can do whatever you want with the included files:
```
chmod -R u+rwX $HOME
```

---

### Post by evilmonkey on 2007-12-26
> **Forlong said:**
> _Never_ run ccsm or compiz (or any other application that doesn't need root privileges) with sudo!

Sir, yes sir! I Will not do that again, SIR! :P

> **Forlong said:**
> Now you don't have privileges to edit your own config files.
Here's how to revert things:

First make sure you are the owner of every files in your home directory:
```
sudo chown -R $USER:$USER $HOME
```
Then change the permissions, so you can do whatever you want with the included files:
```
chmod -R u+rwX $HOME
```

Thank you very much, it worked. :)

---

