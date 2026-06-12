---
title: "How to get FoFix on Ubuntu. Not understanding it."
date: 2011-10-23
forum: Gaming &amp; Leisure
---

### Post by carrie.kandira on 2011-10-23
Okay so I see this but don't know how to do it. Just got Ubuntu.
wget [http://fofix.googlecode.com/files/FoFiX-3.025-Patch-GNULinux-32bit.tar.bz2](http://fofix.googlecode.com/files/FoFiX-3.025-Patch-GNULinux-32bit.tar.bz2)
tar -xvf FoFiX-3.020-Full-GNULinux-32bit.tar.bz2
tar -xvf FoFiX-3.025-Patch-GNULinux-32bit.tar.bz2
cp -r FoFiX-3.025-Patch-GNULinux-32bit/* FoFiX-MegaLight-3.020-32bit/
rm -r FoFiX-3.025-Patch-GNULinux-32bit
sudo cp -r FoFiX-MegaLight-3.020-32bit/ /usr/local/games/fofix
rm -r FoFiX-MegaLight-3.020-32bit/
sudo editor /usr/local/bin/fofix

You can replace editor with any graphical editor of use. if you do not it will use your console text editor.
Add this into the file:

#!/bin/sh
cd /usr/local/games/fofix && ./FretsOnFire "$@"

And last make it exectuable, I'm also removing the archives as they're not needed anymore but this is highly optional:

sudo chmod +x /usr/local/bin/fofix

But I don't know how or where to do it. I definitely don't know how to make a files executable. Why isn't there a video anywhere showing how to do this? Well, does anyone know how to explain it to me?

Thank you.


I am running Ubuntu 11.04

So I got it through the software center but still have no idea how to make it work. Anyone?

---

### Post by carrie.kandira on 2011-10-24
Hmm, no one?

---

### Post by Elfy on 2011-10-24
For some reason the thread is marked as solved - perhaps that's why no-ones answering :)

I'll unmark it for you.

I assume that you now need help using it - rather than installing it.

Looking at what it is I'll also move it to Games where there's more chance of help.

Edit - did you see this - [http://code.google.com/p/fofix/w/list](http://code.google.com/p/fofix/w/list) ?

---

### Post by carrie.kandira on 2011-10-24
Lol. Well thank you kindly. And I actually do need help installing it. Don't know how to get it to work. Got it from the update manager, but it doesn't really do anything.  I hit solo, then solo tour, click on default guitar, then click the name i made and it just goes to something that says parent folder and midi folder. They don't really do anything.......

---

### Post by thatguruguy on 2011-10-24
You need to have some actual songs (in the format that can be used by FoFix/Frets on Fire) somewhere.  It's asking you where those songs are located.

---

### Post by vmind_test on 2011-10-25
the same question as yours.

---

### Post by thatguruguy on 2011-10-25
Same response.  Get some songs. Provide the information where the songs are located to FoFix. Play those songs.

---

### Post by carrie.kandira on 2011-10-28
Well I do have songs I downloaded on FOF how do I tell FoFiX where they are?

---

### Post by thatguruguy on 2011-10-28
You can put your songs in the ./fofix/songs directory in your home directory.

---

### Post by carrie.kandira on 2011-11-05
Hmm I don't seem to have that directory. And now when I try to download it the way I show it. The text editor doesn't show up. I'm going to take it off then put it back on with the ubuntu software center, what exactly should I do after downloading it again?

---

### Post by thatguruguy on 2011-11-05
The .fofix directory is a hidden directory in your home directory, created the first time you run fofix.  To see it, open nautilus to your home directory, and press the Ctrl key and the h key at the same time.  If you don't have a songs directory in your .fofix directory, you can create one by typing:

You can create the directory by typing the following in a terminal:
```
mkdir ~/.fofix/songs
```

---

