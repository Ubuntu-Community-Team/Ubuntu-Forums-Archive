---
title: "google earth wont coorectly display text in crossover"
date: 2008-12-08
forum: General Help
---

### Post by inxygnuu on 2008-12-08
Hi, I just installed google earth on Ubuntu using crossover, wine, and the .bin Linux version, and it wont display any correct text at all. If anyone could help me that would be nice. i really don't know what to do.:confused:

---

### Post by bettlebrox on 2008-12-08
I haven't tried installing it using Crossover, but the Linux port create by Google (using Wine) seems to work fine:
[http://earth.google.com/gallery/index.html#p=linux](http://earth.google.com/gallery/index.html#p=linux)

Or you build it yourself using the googleearth-package package.

---

### Post by inxygnuu on 2008-12-09
what do you mean? I extracted the .bin file, but the earth would not load.

---

### Post by inxygnuu on 2008-12-09
I just installed it in wine, but same problem.

---

### Post by bettlebrox on 2008-12-15
> **inxygnuu said:**
> what do you mean? I extracted the .bin file, but the earth would not load.

I'm not sure what you mean? You said you installed it using Crossover? Where did you get the .bin file from?

---

### Post by inxygnuu on 2008-12-15
no, sorry, I should have said that I installed it in Linux format (.bin), using wine, and using crossover (like wine). None of them display text correctly.

---

### Post by bettlebrox on 2008-12-16
> **inxygnuu said:**
> no, sorry, I should have said that I installed it in Linux format (.bin), using wine, and using crossover (like wine). None of them display text correctly.
I understand now! I'd bet you don't have the Microsoft fonts installed and that's the problem.. Install the msttcorefonts package and see if that fixs the problem.

Install it from the command line using:

sudo apt-get install msttcorefonts

---

### Post by inxygnuu on 2008-12-16
didn't work for me... Do I need to restart? It never works in openGL mode, that is why I took so long (hand to log-off). Should I restart?

---

### Post by bettlebrox on 2008-12-17
Yes you probably need to restart for this to take affect (or restart X).

---

### Post by dark_harmonics on 2008-12-19
I totally dont understand why you would run something that has a native linux client in wine. It works perfectly for me using the linux installer.

First save the bin file to an easy to get to directory. I created a downloads directory in my home folder. 

Open a terminal and change to the folder. Then type:
```
sh GoogleEarthLinux.bin
```
To start the installer

---

### Post by inxygnuu on 2008-12-19
> **dark_harmonics said:**
> I totally dont understand why you would run something that has a native linux client in wine. It works perfectly for me using the linux installer.

First save the bin file to an easy to get to directory. I created a downloads directory in my home folder. 

Open a terminal and change to the folder. Then type:
```
sh GoogleEarthLinux.bin
```
To start the installer

I already did that. None of my methods worked. I will retry in a while, because I need to add special effects to some videos.

---

### Post by dark_harmonics on 2008-12-19
Ok I must've missed that from reading your posts. 
That was all i needed to do on the 4 or 5 computers i installed this on, but maybe your situation is different. Could you post any error messages from that process? The native installer always worked great for me :)


Just a side note that you shouldn't need any sudo to run the installer (actually its better if you don't)

---

### Post by inxygnuu on 2008-12-20
No error message!:) The picture is the only thing that happens. those symbols are representing real text.

---

### Post by poliltimmy on 2009-02-13
the windows version works just fine in crossover

---

