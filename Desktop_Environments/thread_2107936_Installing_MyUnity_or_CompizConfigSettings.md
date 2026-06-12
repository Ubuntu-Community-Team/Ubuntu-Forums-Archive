---
title: "Installing MyUnity or CompizConfigSettings"
date: 2013-01-23
forum: Desktop Environments
---

### Post by Panawe on 2013-01-23
When trying to install either of these from Software Centre I run into "Requires Untrusted Packages" dialog with option "OK" or "Repair" but neither results in package being installed!
Just wanted to mess about with Unity appearance, trivial I know but it's snowing and i can't get out!

---

### Post by stinkeye on 2013-01-23
Make sure you have the latest packages...
```
sudo apt-get update
sudo apt-get upgrade
```

Do you get any error messages installing from terminal?
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Panawe on 2013-01-23
Yup, installed okay. Now i have to learn how to use it :(

---

### Post by stinkeye on 2013-01-23
> **Panawe said:**
> Yup, installed okay. Now i have to learn how to use it :(
Are you using 12.04 or 12.10?

---

### Post by Panawe on 2013-01-23
12.04

---

### Post by stinkeye on 2013-01-23
> **Panawe said:**
> 12.04
Ok, couple of commands if you don't know them.
Reset unity to default...
```
unity --reset
```

Reload compiz
```
compiz --replace
```

---

### Post by Panawe on 2013-01-23
Many thanks, I wondered what was going on!!!

---

