---
title: "cups and hp imaging"
date: 2006-03-07
forum: Desktop Environments
---

### Post by deathbyswiftwind on 2006-03-07
Id like to remove cups and the hp imaging from starting up when my computer boots. I have no printer and no use for them. When I click on them in synaptics and mark for removal it says it will remove the ubuntu-desktop and I sure dont want to do that. If there is anyway to just keep them from loading it would save  some system resources for more important things like quake 4 ;)

---

### Post by jpkotta on 2006-03-07
```
sudo update-rc.d -f hplip remove
sudo update-rc.d -f cupsys remove
```

---

