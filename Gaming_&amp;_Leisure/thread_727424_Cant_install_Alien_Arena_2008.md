---
title: "Cant install Alien Arena 2008"
date: 2008-03-17
forum: Gaming &amp; Leisure
---

### Post by rickrob on 2008-03-17
Hey not very savy when it comes to linux.How do i install  alien arena 2008?Every time i double click om the crx file nothing happens no pop up nothing?

---

### Post by scragar on 2008-03-17
you can install it from synaptic on gutsy(7.10), so I'm guessing your using an older distro right?

---

### Post by Melcar on 2008-03-17
You may have to compile it yourself.  I had to in order for it to work on my 64bit machine.  Try digging through here (this is how I got it to compile):

[http://ubuntuforums.org/showthread.php?t=717132&page=2]("http://ubuntuforums.org/showthread.php?t=717132&page=2")

---

### Post by rickrob on 2008-03-17
Im running a 32 bit and if i use synaptic wont it install the last version and not the new one?

---

### Post by Melcar on 2008-03-17
Synaptic still has the 2007 version  I think.  Try launching the game from the terminal.

---

### Post by rickrob on 2008-03-17
I already have the 2007 version but i would like to try the newer version 2008.Downloaded it, but wont install!

---

### Post by Melcar on 2008-03-17
Try running the crx binary from the terminal.  You're probably missing a dependency.

---

### Post by rickrob on 2008-03-17
Its bizarre cause the crx file will not execute.Also i am not to sure about how im suppose to run the binary in the terminal cause usely i would just change the permissions then i would have the option to run in terminal.

---

### Post by Melcar on 2008-03-17
The binaries are executables.  Just move to the location of the binary and run it:

```
cd /home/<location of file>
./crx

```

... the terminal will then give you an output as to why it's not running.

---

