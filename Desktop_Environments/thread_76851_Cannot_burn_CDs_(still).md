---
title: "Cannot burn CDs (still)"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Pig Monkey on 2005-10-15
I'm having the same problem with Breezy Badger as I was with Hoary: [I cannot burn cds]("http://ubuntuforums.org/showthread.php?p=301859").

I've enabled dma.
This is on a Dell Inspiron 8600 with a NEC CD/DVD+-RW ND-6500A burner.
I'm burning at a nice slow 4x.
Running GnomeBaker as root returns the following in the terminal:
```
Xlib: unexpected async reply (sequence 0x6f4b)!
```
Running GraveMan as both user and root simply returns "Operation Failed" as soon as I start the ISO burn.

The GnomeBaker output is too long for this post, so I've uploaded it here:
[http://pig-monkey.com/gnomebaker-error]("http://pig-monkey.com/gnomebaker-error")

---

### Post by manicka on 2005-10-15
Probably not what you want to hear, but I gave up on gnomebaker and use k3b

---

### Post by afonic on 2005-10-15
I use NeroLINUX all the time:
[http://www.nero.com/eng/NeroLINUX.html](http://www.nero.com/eng/NeroLINUX.html)

There is a demo version, so chech it out.

---

### Post by Pig Monkey on 2005-10-15
I installed k3b and it works fine, but I don't understand why. K3b, Gnomebaker, Graveman -- these are all just front ends to the command line tools. It shouldn't make a difference.

Oh well, at least I get that cool k3b trumpet when there's a successful burn.

---

### Post by nix4me on 2005-10-15
Yep, k3b is nice.

Does nautilus burner work for you?

They all work for me.

nix

---

### Post by joelito on 2005-10-15
[quote=nix4me]
Does nautilus burner work for you?
[/quote]
Works for me so far...

Maybe you must install cdrdao from the universe/multiverse repository...

---

### Post by Pig Monkey on 2005-10-15
I never tried the nautilus burner -- dragging and dropping files like that always seemed a little odd to me.

cdrdao is installed.

---

