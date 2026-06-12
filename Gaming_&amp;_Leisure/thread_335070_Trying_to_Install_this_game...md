---
title: "Trying to Install this game.."
date: 2007-01-09
forum: Gaming &amp; Leisure
---

### Post by abstractstrife on 2007-01-09
Well recently my brother installed linux on my computer, now I'm no expert but I can do a few simple things. To put it simply, I am a slave the the GUI.

Now I'm trying to Install a simple game called tibia. [http://download.tibia.com/tibia-7.82-6.tgz](http://download.tibia.com/tibia-7.82-6.tgz)

However I have no idea what to do,  Any help would be greatly appreciated as my brother is currently not able to help me.

Thanks,
Abstract

---

### Post by meng on 2007-01-09
[www.psychocats.net/ubuntu/installingsoftware](www.psychocats.net/ubuntu/installingsoftware)
The basics of installing from source are

1. Extract
tar zxvf tibia-7-82-6.tgz

2. change to directory
cd tibia--7-82-6

3. Configure
./configure

4. Make
make

5. Make install
sudo make install


Good luck.

---

### Post by abstractstrife on 2007-01-09
None of those commands work for this. I have used all those at one point, so I'm sure I'm not getting it wrong. I can extract the files just fine, and change directory fine, but /configure and make and make file do nothing I just get errors.

---

### Post by meng on 2007-01-09
Just to repeat, it's
./configure (got to have a . there)
make
sudo make install

---

### Post by quartzy on 2007-01-09
```
sudo apt-get install build-essential
```

---

### Post by abstractstrife on 2007-01-10
That worked almost completely perfectly :).

Now I am not sure how to start the game. I tried        sh Tibia

but it says a bunch of error stuff so there is this patch.sh file, so I tried 'sh patch.sh' and a notice came up that said, failed to patch tibia, please reinstall. So I tried to reinstall, and it did nothing.

Really, thanks for all this help.. it can be a bit frustrating with linux.

---

### Post by K.Mandla on 2007-01-10
Moving to Gaming & Leisure. :)

---

### Post by hscottyh on 2007-01-10
I dowloaded it from your link....

Seems it doesn't need compiling. In terminal from the directory you extracted it to just do:
./Tibia 

and it works!

If you don't want to run it from a terminal everytime you can make a menu entry for it. 

In Edgy:
System -> Preferences -> Menu Layout

---

### Post by abstractstrife on 2007-01-18
Okay, well that didn't work. When I try ./patch.sh it says fail. when I try ./Tibia it gives me a visuals error, something about 0x5b or something.

So I install wine from adept package manager and install windows tibia, and it launches but the screen its just a blur sort of. I can really see anything and it doesn't respond. :'(

---

