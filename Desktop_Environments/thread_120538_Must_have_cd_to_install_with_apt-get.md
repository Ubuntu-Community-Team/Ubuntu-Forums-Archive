---
title: "Must have cd to install with apt-get?"
date: 2006-01-22
forum: Desktop Environments
---

### Post by Fourthbean on 2006-01-22
I am on a laptop where the only way I can have a cd with me is if I have my docking station.  Is there a way to get around having to have the ubuntu install cd to install new applications?

I suppose I could just copy the iso to my hard drive and mount it via loop, but I would rather have my hard drive space used for other things.

Thanks for the info,
Fourthbean

---

### Post by Michael Steinberg on 2006-01-22
Comment out the references to the cd in /etc/apt/sources.list. Or remove them in the repositories in Synaptic--this does the same thing.

---

### Post by aysiu on 2006-01-22
Translation:
"comment out" means "put a # in front of the line that mentions a CD-ROM."

To edit the sources.list go to Applications > Accessories > Terminal and type these commands: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

---

### Post by Fourthbean on 2006-01-23
Thank you, works great now.

---

