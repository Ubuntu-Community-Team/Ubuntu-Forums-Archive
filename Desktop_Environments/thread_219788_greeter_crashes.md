---
title: "greeter crashes"
date: 2006-07-20
forum: Desktop Environments
---

### Post by bedog on 2006-07-20
When I reboot my Ubuntu 6.06, I get the following message:
"The greeter app seems to be crashing. Attempting to start a different one."
When I click OK I get a login page, although a different one than the "normal".

How can I either fix the crashing one, or select another as standard?

I need this since I'm doing a lot of work on the machine from remote locations, and with this error message I cannot remote login after a restart.

Any help is appreciated.

---

### Post by bedog on 2006-07-20
no ideas of how to change the greeter app?

---

### Post by MatthewRhodes on 2006-08-26
I have the very same problem, its since I attempted to change the theme. I have tried repackaging and installing the gdm using the terminal, but no result.

---

### Post by Aicani on 2006-08-27
Mistake...

---

### Post by Ramses de Norre on 2006-08-27
From terminal: ```
sudo aptitude install kdm
echo "/usr/bin/kdm"|sudo tee /etc/X11/default-display-manager
```
You'll now be using kdm instead of gdm.

And maybe ```
sudo aptitude purge gdm && sudo aptitude install gdm
``` can fix the problem..

---

