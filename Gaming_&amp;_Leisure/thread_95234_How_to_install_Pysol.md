---
title: "How to install Pysol?"
date: 2005-11-26
forum: Gaming &amp; Leisure
---

### Post by sue7504 on 2005-11-26
I've located & downloaded pysol-4.82.src.tar.bz2 & managed to extract it to a folder. 
After that, I'm stuck with how to install it & make an icon for easy access.  I do have a file called games-server.py in /usr/games.  I can't see a 'make' or configure file within the folder. I've tried Synaptic but it doesn't seem to have it listed.  Do I need to add an extra 'source location' to get syanptice or ept-get to worK?
TIA
SUE

---

### Post by Remmelas on 2005-11-26
You can install via synaptic, but you have to enable the 'universe' repositories.  

adding the following to your /etc/apt/sources.list will do this

```
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
```

then do 
```
sudo apt-get update
```

and it will show up in your synaptic package manager, or you can do 

```
sudo apt-get install pysol
```
from the command line

---

### Post by sue7504 on 2005-11-26
Many thanks for that.  Worked fine once I'd enabled the 'universe' repository.  I even managed to create my own desktop launcher/icon!@!

Thanks again for the quick assistance
Sue

---

