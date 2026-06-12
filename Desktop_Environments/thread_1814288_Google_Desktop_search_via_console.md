---
title: "Google Desktop search via console"
date: 2011-07-29
forum: Desktop Environments
---

### Post by mag_dex on 2011-07-29
Hi, 

Do you know if there is any easy way to do Google Desktop search from console.
I have my short wrapper to some cmd such as find, locate and so on. It would be nice if I could use Google Desktop from the program.

---

### Post by sanderd17 on 2011-07-29
No easy way that I know, but you can use wget to get a html page. Something like

```

wget http://www.google.com/search?q="test"

```

But I think you would need to do some serious parsing before you get something usefull of it.

But there are already apps that provide google search for different desktop environments (it's build in to Gnome 3 as example). But you have to tell me your DE first.

---

