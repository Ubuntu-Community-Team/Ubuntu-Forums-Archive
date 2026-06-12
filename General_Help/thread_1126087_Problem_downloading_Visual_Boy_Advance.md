---
title: "Problem downloading Visual Boy Advance"
date: 2009-04-15
forum: General Help
---

### Post by Tribulation on 2009-04-15
A friend of mine is trying to download VBA but it keeps telling him that it couldn't connect to the mirror. Is there some way around this problem?

---

### Post by Svensk023 on 2009-04-15
you could just try to download it from a website. They should have tarballs of it and maybe, if your lucky, a .deb somewhere.

but it sounds like they mirror might be down temporarily

---

### Post by Tribulation on 2009-04-15
I don't remember how to install anything on Linux to be quite honest, I haven't had to in a long time, I just use the package manager.

---

### Post by Svensk023 on 2009-04-15
well as a refresher course, here is how to compile from source code

to get the necessary packages, in the terminal type

```
sudo apt-get install build-essential
```

now assuming you have the .tar.gz file downloaded you can unpack the archive by typing in

```
tar xvf [archive name here]
```

change into the directory 

```
cd [directory name]
```

to complie, input

```
sudo make
```

followed by

```
sudo make install
```

and then just type in the program name in the terminal, or create a launcher for it, and you're golden

---

