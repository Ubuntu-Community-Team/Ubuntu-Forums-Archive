---
title: "Synaptic package manager or not (newbie question)"
date: 2009-06-21
forum: General Help
---

### Post by Ojustaboo on 2009-06-21
Hi all, getting myself a little confused here with regards to using the Synaptic package manager.

I am following instructions to patch and compile wine, happy so far.

One of the first instructions was to do:

sudo apt-get build-dep wine

Which produced a long list of programs/libraries it was about to get and install and asked me whether I wanted to continue.

I could have selected Y and it would have gone off and got everything needed. But I was thinking along the lines that if I install loads of things this way, I will start loose track of what's actually installed and what version. 

So instead, I spent 30+ mins going through the list of the packages it was going to get and selecting them in the package manager and installed them this way.

Am I being correctly careful or am I missing the point somewhere and creating loads of unnecessary work for myself?

thanks

boo

---

### Post by Cheesemill on 2009-06-21
Synaptic is just a graphical front-end for apt-get. Any changes you make to the system with apt-get will be mirrored in Synaptic and vice-versa.

Either option will give you exactly the same end result so in my opinion you just made alot of unnecessary work for yourself.

---

### Post by Ojustaboo on 2009-06-21
Many thanks. Should have asked first :)

---

### Post by egalvan on 2009-06-21
Anything installed via apt-get also shows up in Synaptic's database.
And the other way around.

I ran three different tests for this, to see what would happen.

I selected a prorgam I wanted,
checked to make sure it was NOT listed as "installed" under Synaptic,
installed with
```

``` "apt-get",
then ran Synaptic again.
Sure enough, the program was now listed as "installed". :)

Sometimes it's easier, or faster, to run "apt-get"
and then again, it may be easier, or faster, to run "Synaptic"

"apt-get" is (usually) easier for one single program/library that you already know the name.

Synaptic is (usually) easier for searches, and installing multiple items at once (unless working from a list you can cut-n-paste)

Your Mileage May Vary

Your Likes and Dislikes Will Definitely Vary


> **Ojustaboo said:**
> Many thanks. Should have asked first :)

Then you would not have had as much fun as I did :)

---

### Post by Ojustaboo on 2009-06-21
Many thanks

Much appreciated

---

