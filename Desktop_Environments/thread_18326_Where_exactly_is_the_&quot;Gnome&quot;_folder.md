---
title: "Where exactly is the &quot;Gnome&quot; folder?"
date: 2005-03-06
forum: Desktop Environments
---

### Post by Gorlaz on 2005-03-06
Hey all, 
Am a new Ubuntu (&Linux) user making the move from "some other system", forgot its name... ;)

On a Knoppix or something CD-only distro I tried out it had the game Bombermaze. My girlf has, unfortunately, become addicted to it!

I've downloaded the tarball from [http://www.nongnu.org/bombermaze/](http://www.nongnu.org/bombermaze/) into my /home/username folder. Cool. Great. 

Have then tried to do the next section of the instructions;

tar xvfz bombermaze-0.6.3.tar.gz (nb: need to subsitiute 0.6.3 for current build - 0.6.6)
cd bombermaze-0.6.3
./configure
make
make install

and have run into issues - apparently it needs to be installed into the "Gnome" program directory which unfortunately I just can't find which one it is! I know I need to use the adjustment to the ./configure line - ./configure --prefix=PATH (From [http://www.nongnu.org/bombermaze/install.html](http://www.nongnu.org/bombermaze/install.html))

I've opened the root folder (I think - I typed "/" into nautilus and have got what looks to be the contents of the hdd) and gone through as many folders as I can but can't figure out which one I need to install this into.

Can someone help a poor noob? Many thanks or I'm gonna get in trouble!

---

### Post by alastair on 2005-03-06
Why don't you just install the package. It appears to be available.

Either - open "synaptic" package manager, "search" for "bomber" and install.

Or type :

sudo apt-get install bombermaze

---

### Post by alastair on 2005-03-06
Actually - if you have done the "make/make install" (and no errors), it will already be installed.

See if runs by typing "bombermaze" in a shell perhaps. 

Otherwise - just install the package.

---

### Post by Gorlaz on 2005-03-06
Hey Alastair,

I tried searching through Synaptic, but I don't think my package lists are searching the larger repositories - will look into it more.

I have run the /make commands, but got some missed file errors, which I think are tied up with not being in the Gnome folder.

Thanks for the patience!

---

### Post by poofyhairguy on 2005-03-06
[QUOTE=Gorlaz]Hey Alastair,

I tried searching through Synaptic, but I don't think my package lists are searching the larger repositories - will look into it more.

I have run the /make commands, but got some missed file errors, which I think are tied up with not being in the Gnome folder.

Thanks for the patience![/QUOTE]

definately look in the universe and multiverse. I see it in hoary...

---

