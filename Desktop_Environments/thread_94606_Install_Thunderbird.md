---
title: "Install Thunderbird"
date: 2005-11-24
forum: Desktop Environments
---

### Post by majke on 2005-11-24
I need help installing Thunderbird on my laptop, I set it up on my desk top with "sudo apt-get install mozilla-thunderbird". But when I enter that on my laptop it say's it is not available, but there are references to it. I have the program downloaded and I put it on the desktop to make it easy to find but I cannot get it to install.

Thanks

---

### Post by canadianwriterman on 2005-11-24
Why not just install it through Synaptic? Then you don't need apt-get install at all.

---

### Post by Sebby on 2005-11-24
I did it using apt-get install mozilla-thunderbird, but I had to update my repositories first. Update your sources.list from [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php), remembering to apt-get update after you have done so. Then try apt-get install mozilla-thunderbird again.

:D

---

### Post by majke on 2005-11-24
[QUOTE=Sebby]I did it using apt-get install mozilla-thunderbird, but I had to update my repositories first. Update your sources.list from [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php), remembering to apt-get update after you have done so. Then try apt-get install mozilla-thunderbird again.

:D[/QUOTE]I am using breezy badger does this change things

---

### Post by aysiu on 2005-11-24
You shouldn't have to enable extra repositories to install Thunderbird.
Still, just in case it has something to do with this, can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by Sebby on 2005-11-24
[QUOTE=majke]I am using breezy badger does this change things[/QUOTE]
If you scroll down on that page, you'll see theres the sources for Breezy.

aysiu says you shouldn't need to do it, and I suspect he's right, but it's worth a try. The worst that can happen is you have up-to-date repositories. :p

---

### Post by aysiu on 2005-11-24
[QUOTE=Sebby]
aysiu says you shouldn't need to do it, and I suspect he's right, but it's worth a try. The worst that can happen is you have up-to-date repositories. :p[/QUOTE] Also, the first instruction you're given to put in the command-line is the command to back up your current /etc/apt/sources.list, so you really have nothing to lose.

---

