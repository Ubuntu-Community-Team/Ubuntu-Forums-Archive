---
title: "uninstall gcc 4 and install gcc-3.4"
date: 2005-12-12
forum: General Help
---

### Post by nijinsky on 2005-12-12
Hi All

I'm new to Linux, ubuntu and gcc. Good start eh :-).

I haev installed GCC 4 but to build my USB wifi linux driver in breezy I need gcc 3.4.

How do I uninstall GCC4 for me to install 3.4. When I try and install 3.4 I ge tan error
E: Couldn't find package gcc 3.4.

I have no internet connection on linux. Only on win.

Help appreciated.

cheers
bob

---

### Post by taurus on 2005-12-12
Hellow there from Scotland.  I know a mate from Scotland as well.

If you don't have an internet connection, it's going to be a little tricky!  Basically, you want to use synaptic and at the search field, type in "gcc" and it will present you with a long list of gcc.  Now, pick whichever version you want from that list and mark it for installing!  Otherwise, you may have to use another computer (that connects to the net and running Ubuntu) and download it.  Burn it to a CD or some type of media and transfer it over to your computer. 

By the way, why do you have to build a driver for your wireless card?  What kind of card do you have because you can use windows' driver too...

---

### Post by nijinsky on 2005-12-12
[QUOTE=taurus]Hellow there from Scotland.  I know a mate from Scotland as well.

If you don't have an internet connection, it's going to be a little tricky!  Basically, you want to use synaptic and at the search field, type in "gcc" and it will present you with a long list of gcc.  Now, pick whichever version you want from that list and mark it for installing!  Otherwise, you may have to use another computer (that connects to the net and running Ubuntu) and download it.  Burn it to a CD or some type of media and transfer it over to your computer. 

By the way, why do you have to build a driver for your wireless card?  What kind of card do you have because you can use windows' driver too...[/QUOTE]

Hi there
I'm in Sunny Glasgow (originally from Loch Lomond)

I think I may now have boobed here. I used synaptic to uninstall GCC4 and it seems to be deleteing half the system, like terminal, mozilla components. etc. I'll have to reinstall from disk. Not a big deal really. 

I need to use the linux drivers because I use a belkin USB G wifi stick F5D5070 and the instructions listed here don't seem to work with my setup. I was hopeing the linux drivers would make it work.

All the best
Bob

---

### Post by MartinG on 2005-12-12
When you've got your system back (!), note that you *don't* have to remove gcc 4 to install 3.4.  They can both exist together on the same system.  What you need to do to make sure your system uses 3.4 to build the driver (if you still need to) is as follows:

on the command line, just before you start off with "./configure", enter "export CC=gcc-3.4" .

---

### Post by nijinsky on 2005-12-12
[QUOTE=MartinG]When you've got your system back (!), note that you *don't* have to remove gcc 4 to install 3.4.  They can both exist together on the same system.  What you need to do to make sure your system uses 3.4 to build the driver (if you still need to) is as follows:

on the command line, just before you start off with "./configure", enter "export CC=gcc-3.4" .[/QUOTE]

Thanks Martin

I get "could not find package gcc-3.4" so I'm away to find out where to get it.

I must say that a lifelong windows user may find the commandline a pain, however, as someone that grew up on RISC OS, I find it quite interesting.

I also  appreciate a good OS somtimes requires a bit of tweaking. 

All the best
Bob

---

### Post by MartinG on 2005-12-13
[QUOTE=nijinsky]Thanks Martin

I get "could not find package gcc-3.4" so I'm away to find out where to get it.

[/QUOTE]
Sorry, I thought you had already installed it.  You should be able to get it via synaptic (search for "gcc" and pick the one you need).

---

### Post by nijinsky on 2005-12-13
[QUOTE=MartinG]Sorry, I thought you had already installed it.  You should be able to get it via synaptic (search for "gcc" and pick the one you need).[/QUOTE]

That seems to be the problem. I need GCC 3.4 to build the rt2500 driver but I only have GCC 4 with breezy. I have one file called Gcc 3.3 base; is that it?

Cheers
Bob

---

### Post by MartinG on 2005-12-13
[QUOTE=nijinsky]That seems to be the problem. I need GCC 3.4 to build the rt2500 driver but I only have GCC 4 with breezy. I have one file called Gcc 3.3 base; is that it?

Cheers
Bob[/QUOTE]

If you can't get online to use synaptic, you will have to get files from the following (which is the relevant repository):

[http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4)

You need:
gcc-3.4_3.4.4-6ubuntu8_i386.deb
gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
cpp-3.4_3.4.4-6ubuntu8_i386.deb
and possibly also 
g++-3.4_3.4.4-6ubuntu8_i386.deb (the matching C++ compiler)
libstdc++6-dev_3.4.4-6ubuntu8_i386.deb

Don't mix the versions!

I hope I've covered all the dependencies for you, but it's hard to know which libraries are already covered by your base installation.

---

### Post by BLTicklemonster on 2005-12-13
Can't he just put this 

```
CC=gcc-3.4

export CC
```

in prior to running what he's doing?

---

### Post by linkunderscore on 2005-12-13
[QUOTE=BLTicklemonster]Can't he just put this 

```
CC=gcc-3.4

export CC
```

in prior to running what he's doing?[/QUOTE]


Thats exactly what I was going to suggest. Just make sure you have gcc-3.4 (obviously).

---

### Post by MartinG on 2005-12-13
[QUOTE=BLTicklemonster]Can't he just put this 

```
CC=gcc-3.4

export CC
```

in prior to running what he's doing?[/QUOTE]

Yes, that's where the thread began -- see my first post (4th in the series).  The trouble is that he (A) hasn't got gcc-3.4 (it's not part of the default Breezy install), and (B) hasn't got online access from his breezy installation so can't use apt-get etc. to get the necessary.  As I understand it, he's going to have to download the necessary packages and copy them across -- hence my last post.

---

### Post by BLTicklemonster on 2005-12-13
Sorry, I was juggling bowling balls and someone kept throwing chainsaws and lit arrows at me while I was reading that, and I missed the obvious problem. My bad.

---

### Post by nijinsky on 2005-12-14
[QUOTE=MartinG]Yes, that's where the thread began -- see my first post (4th in the series).  The trouble is that he (A) hasn't got gcc-3.4 (it's not part of the default Breezy install), and (B) hasn't got online access from his breezy installation so can't use apt-get etc. to get the necessary.  As I understand it, he's going to have to download the necessary packages and copy them across -- hence my last post.[/QUOTE]


Hi folks

OK I have now got the files copied to my desktop. So how do I install them.

I typed apt-get install gcc-3.4 and I ge tan error that the /var/lib/apt/lists/lock - open (13 Permission denied)
E: unable to lock the list directory.

I have the files on my desktop. Should I put them somewhere else?

Is there a URL handy on how to use Linux. IE install something.

Cheers
Bob

---

### Post by kaamos on 2005-12-14
If you have the files on your desktop open a terminal and type:
```
sudo dpkg -i ~/Desktop/*.deb
```

The ubuntu wiki ([https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)) has a good starter guide, and a lot of other useful information. So you might try searching there.

Good luck!

---

### Post by nijinsky on 2005-12-14
[QUOTE=kaamos]If you have the files on your desktop open a terminal and type:
```
sudo dpkg -i ~/Desktop/*.deb
```

The ubuntu wiki ([https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)) has a good starter guide, and a lot of other useful information. So you might try searching there.

Good luck![/QUOTE]

Hi there.

This worked. there were a coiuple of dependencies problems but I installe dthe relevent libs and then reinstalled. 

Now if only I could remember why I needed it. :-)

Cheers
Bob; sunny Scotland

---

### Post by linkunderscore on 2005-12-14
[QUOTE=BLTicklemonster]Sorry, I was juggling bowling balls and someone kept throwing chainsaws and lit arrows at me while I was reading that, and I missed the obvious problem. My bad.[/QUOTE]

hahah 


uhh yea... same here. But i was being attacked by an angry swarm of pigmy dophlins with laser beams on their heads "ahaaaaaAaaAaaa bew bew bew" . :)

---

### Post by BLTicklemonster on 2005-12-14
[QUOTE=linkunderscore]hahah 


uhh yea... same here. But i was being attacked by an angry swarm of pigmy dophlins with laser beams on their heads "ahaaaaaAaaAaaa bew bew bew" . :)[/QUOTE]

Huh, same job, different location, apparently!


Hey, glad you got it installed. Were you trying to install nvidia drivers, or something?

---

