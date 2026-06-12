---
title: "Help with PCMCIA edimax ep-4103DL"
date: 2005-10-11
forum: Desktop Environments
---

### Post by alnet on 2005-10-11
I try to install the PCMCIA edimax ep-4103DL card on my laptop with no success.
I'm new in Linux world, the system doesn't find any card inserted and I have no idea how to make it work :(

---

### Post by eMuNiX on 2005-10-11
Some more info on your laptop make/model would be helpful :)

---

### Post by GeneralZod on 2005-10-11
The good news is that it appears to be supported:

[http://www.linuxcompatible.org/cdetail10701.html](http://www.linuxcompatible.org/cdetail10701.html)

Open up a command prompt, and try 

```
sudo modprobe 8139too
```

and then paste the results of doing 

```

ifconfig

```

---

### Post by alnet on 2005-10-11
my laptop is Compaq Armada m300

---

### Post by drgreborn on 2005-11-28
Having teh same problem as this. After doing teh modprobe thingy the ifconfig still shows no eth0. Any idea why?

---

