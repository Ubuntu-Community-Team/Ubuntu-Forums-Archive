---
title: "djl Game Manager"
date: 2010-02-21
forum: Gaming &amp; Leisure
---

### Post by arnab_das on 2010-02-21
This is an installation wizard/manager for all games out of the box (not in the repos etc.). Works really well, has a great interface (simple single click 'Install', 'Play' and 'Remove', doesnt require you to compile or build anything, installs all the dependencies) and the best part is that it has loads of games in its repos. I have shifted loayalties from playdeb.net to this manager. (Interestingly it was in playdeb that I found it :P )

Here's the link to the website: [http://en.djl-linux.org/](http://en.djl-linux.org/)

---

### Post by Pressondude on 2010-02-21
I just installed it, installed battletanks, and now it's whining about a lack of a shared library that I installed, and it still won't run battletanks

---

### Post by dmdevotee on 2010-03-24
is there any repo to install from, instead of running the script?

---

### Post by dmdevotee on 2010-03-24
if nobody knows the answer, can anyone help me with this?

i have the script on /home/dmdevotee/djl/djl.sh, and when i do sudo sh /home/dmdevotee/djl/djl.sh it works fine

how can i do a launcher for that??

i tried to write in "command" box of app launcher:

gnome-terminal -x /home/dmdevotee/djl/djl.sh

and then

/bin/sh -c /home/dmdevotee/djl/djl.sh


but it didn't work

---

### Post by arnab_das on 2010-03-25
the script should automatically make a launcher for u under the Games menu.

---

### Post by handy on 2010-03-26
When I had djl installed, I spent the time & installed all of the libraries & such, after that whenever you install another game you don't have them complaining about that you need so & so file.

I liked how you could move games that weren't even installed by djl into its directory & have it list the link. It appealed to me having all games stored in one place & accessible via one menu system. ;)

---

### Post by _h_ on 2010-03-26
Having looked on their forums, this software is extremely bugged.

And some of the stuff it writes to your hard drive isn't in English (like the folders it creates in ~/.djl, are not in English).

---

### Post by arnab_das on 2010-03-26
> **_h_ said:**
> Having looked on their forums, this software is extremely bugged.

And some of the stuff it writes to your hard drive isn't in English (like the folders it creates in ~/.djl, are not in English).

well i have been using the software for a few months now. i think its decently written. yes, there are some rough ares, eg. i do sometimes get errors after downloading a game (which can be very frustrating). but overall, it reduces the hassles of compiling games etc. had it not been for this software, i would have never ever taken the pains to install Assault Cube.

---

### Post by _h_ on 2010-03-26
> **arnab_das said:**
> i would have never ever taken the pains to install Assault Cube.

How so? AssaultCube is standard in the ubuntu repos, and it's only ~40mb.

---

### Post by arnab_das on 2010-03-26
> **_h_ said:**
> How so? AssaultCube is standard in the ubuntu repos, and it's only ~40mb.

i think the one in djl is a later version.

---

### Post by handy on 2010-03-26
I didn't find the few instances of non-English names to be a problem.

It sure must be a pain for all the people who's native language is not English to have to deal with the language that we happened to be born into?

---

### Post by Raffles10 on 2010-04-07
DJL states quite explicitly that it installs games "but without dealing with any dependencies" these have to be done manually.

---

