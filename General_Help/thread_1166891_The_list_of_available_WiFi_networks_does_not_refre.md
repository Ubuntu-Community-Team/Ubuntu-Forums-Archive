---
title: "The list of available WiFi networks does not refresh"
date: 2009-05-22
forum: General Help
---

### Post by Lockheed on 2009-05-22
If I use my laptop at home, suspend it and then resume at different location, the list of available WiFi networks is still the one from my home location. It never refreshes. I have to restart my computer and then I can connect to local networks.

How do I set the list to be refreshed, say, once every minute?

---

### Post by scorp123 on 2009-05-22
> **Lockheed said:**
> If I use my laptop at home, suspend it and then resume at different location, the list of available WiFi networks is still the one from my home location. What Ubuntu release are you using? And what kind of Wifi chipset do you have?

Here is how you could find out these things if you don't know them:

Finding out your Ubuntu release:
```
cat /etc/lsb-release
```

Finding out your Kernel version:
```
uname -a
```

Finding out what your Wifi chipset is:
```
lspci
```

Please post the outputs of those commands here.

My suspicion: You have an Atheros-based Wifi chipset. There is a bug that causes Atheros chipsets not to realise that they are in a new location. The workaround would be to have the Atheros driver reloaded. This can be automated so you don't have to reboot or do anything else manually. Please see here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267339](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267339)

Workaround:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267339/comments/13](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267339/comments/13)

But let me repeat again: I am guessing here. You did not provide any technical details so I am in no way sure that this is your problem. The basis for my guess is that I had the same problem that you describe with laptops that had an Atheros-based Wifi chipset whereas those with Intel chipsets just worked the way they were supposed to. Sorry if I am completely wrong with my guess ... in that case I'd need you to provide the command line output I asked for. :D

---

### Post by Lockheed on 2009-05-22
This atheros workaround fixed the problem.
Will it also work for hibernation or is is only for SUSPEND?

---

