---
title: "Compiling from Source / Scons"
date: 2009-02-07
forum: General Help
---

### Post by mikethehard on 2009-02-07
Hi there,

I'm trying to install this software: [http://minicomputer.sourceforge.net/](http://minicomputer.sourceforge.net/)
The software is fairly new so it's not in the package manager.

It needs to be compiled from source, using scons and i'm totally going round in circles. i've tried just typing "scons" in terminal as it suggested in the text file and aside from installing the main scons ap via get-ap scons as terminal prompted me, I'm no further forwards.


can anyone talk an idiot through the installation procedure for Ubuntu?

i'm diving well into uncharted territories here and i'm sure this is just the tip of the iceberg in terms of getting this program to with with JACK. however, it looks like a really interesting synth and i'm keen to give it a shot...

---

### Post by mikethehard on 2009-02-09
anyone?

---

### Post by snova on 2009-02-09
Assuming you downloaded the package to your home directory, first extract it using whatever program you prefer. Make a note of the directory its files were extracted to.

Open a terminal and run this, posting any errors you might get:

```

cd **<directory>**
scons
scons install

```

Replacing <directory> with the name of the directory it unpacked to.

---

### Post by photon_man62 on 2009-02-09
Oh and

```
sudo apt-get install scons
```

---

### Post by mikethehard on 2009-02-10
Thanks a lot!

I'll try this when I get home tonight.

---

