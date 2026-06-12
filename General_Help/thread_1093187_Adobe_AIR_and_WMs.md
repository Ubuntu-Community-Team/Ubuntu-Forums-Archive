---
title: "Adobe AIR and WMs"
date: 2009-03-11
forum: General Help
---

### Post by ReformatMe on 2009-03-11
Sorry if I've posted this in the wrong place, I couldn't see anywhere that this might fit in.
When I'm running Adobe AIR applications, they retain the window decorations. I've uninstalled Compiz and this hasn't fixed the problem. I've been looking for some time and I cannot find how to fix this, I've been looking to fix it through metacity but I'm probably searching for the wrong thing. I wish to use the program's custom chrome.
Anyone acheived this or can think of anything that may help?

Thanks!
[Screenshot of Adobe AIR application]("http://i43.tinypic.com/256zj9x.png")

---

### Post by whitethorn on 2009-03-11
you could give devilspie a try.  It's kinda a windows design manager for metacity (don't really know how to explain).  

```
sudo apt-get install devilspie
nohup devilspie
```

then you need to create a config file which devilspie will read which describes what you want to do with each program.

nano ~/.devilspie/adobeair.ds

> 
if (is (application_name) "Name of Program probably Adobe...") (undecorate)
   

which pretty tells devilspie when a program called ??? is started remove the window decoration.  There are a lot of other uses for devilspie, such as starting only certain programs on different desktops, setting a specific size and location.  

You can read up on it here

[http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie)

---

### Post by ReformatMe on 2009-03-11
Thanks a lot! Exactly what I was looking for, much appreciated :D

---

