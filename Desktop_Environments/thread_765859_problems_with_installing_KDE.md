---
title: "problems with installing KDE"
date: 2008-04-24
forum: Desktop Environments
---

### Post by esc_phr34k on 2008-04-24
hey guys, i just tried installing kde on my Ubuntu by using this command 

sudo apt-get update kubuntu-desktop && sudo apt-get install kubuntu-desktop

but i get an this 

[PHP]Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgrated, or removed.
0 packages upgraded, 0 newly installed, 0 to remove 0 not upgrated.[/PHP]

I dont know what else to do, can you guys please help

---

### Post by LaRoza on 2008-04-24
> **esc_phr34k said:**
> hey guys, i just tried installing kde on my Ubuntu by using this command 

sudo apt-get update kubuntu-desktop && sudo apt-get install kubuntu-desktop

but i get an this 

[PHP]Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgrated, or removed.
0 packages upgraded, 0 newly installed, 0 to remove 0 not upgrated.[/PHP]

I dont know what else to do, can you guys please help

Run this:

```

sudo apt-get update && sudo aptitude install kde-core

```

kubuntu-desktop is the entire Kubuntu setup, kde-core is smaller. If you want all of Kubuntu's apps, you can install kubuntu-desktop after (it will add what is missing)

---

### Post by esc_phr34k on 2008-04-24
thx but i still get the same error message.

---

### Post by ben2talk on 2008-12-07
try 'gksudo synaptic'

search kubuntu

---

