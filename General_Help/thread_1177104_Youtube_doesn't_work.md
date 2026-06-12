---
title: "Youtube doesn't work"
date: 2009-06-03
forum: General Help
---

### Post by Maysun on 2009-06-03
:(
 
Every video I open on youtube tells me 'an error has ocurred'.
When I then open flash download it tells me I can play flash perfectly.
Now I considered uninstalling flash and downloading the newest version but I'm afraid I don't know how to uninstall flash on a Linux. I don't even know the directory/direction/where it is located/whatever you call it.
 
Any suggestions?

---

### Post by t0p on 2009-06-03
The way to install flash on ubuntu (well, the way that is generally accepted as the best) is to install **flashplugin-nonfree**.  You can do this by opening the terminal and typing

```
sudo apt-get install flashplugin-nonfree
```

However, if you're being told that you can play flash, you most likely already have flash installed.  You can check this by typing in the above command - if you have flash installed already, you'll get a message saying so.  In which case, I don't know what to suggest.

---

### Post by FlyingBuzz on 2009-06-03
I had this problem while I was attempting to watch youtube via GPRS connection.
The flash player youtube uses had thought that my connection was  interrupted so it displays this message. If you have slow internet connection this might be the reason. If flash plays well everywhere else it's not the solution to reinstall it.

---

