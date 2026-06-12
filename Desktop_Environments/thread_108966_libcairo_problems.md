---
title: "libcairo problems??"
date: 2005-12-27
forum: Desktop Environments
---

### Post by NoWhereMan on 2005-12-27
I can't open some gnome applets/apps or they have strange behaviours (update-manager doesn't show up the window, ecc) and this seems to be related to the following error
```
Traceback (most recent call last):
  File "/usr/bin/gnome-software-properties", line 28, in ?
    import gtk
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden
```

I DO have libcairo installed... so i don't know what's wrong? can anybody help me


PS: merry xmas, and happy new year, great work with ubunt two thumbs up to the developers and everybody helps ;)


**EDIT!**

So many people here asking for help. that I think it will be great hearing that one of them has already fixed his problem

*edit2*: Newbie walthrough on my blog: [http://nowherenet.altervista.org/blog/static.php?page=linux-ubuntu-libcairo6](http://nowherenet.altervista.org/blog/static.php?page=linux-ubuntu-libcairo6)

First of all: [https://launchpad.net/distros/ubuntu/+source/libcairo/+bug/6100](https://launchpad.net/distros/ubuntu/+source/libcairo/+bug/6100) so, here's the catch
> Upgrading libfreetype6 from 2.1.7-2.4ubuntu1 to 2.1.10-1 fixed the problem.
How to fix? Enable/add the dapper repo into your /etc/apt/sources.list
```
deb http://archive.ubuntu.com/ubuntu dapper main restricted
```
Now open synaptic or use apt-get to update libfreetype6 :)
When you're done, you can comment out the new repo :)



bye ;)

---

### Post by pbb on 2006-01-10
Thanks!!! Man, have I been going over this problem for a long time before I was able to fix it.
(Part of the problem is of course that I am a total newbie...)

One question though: is there any reason to keep/remove the added Dapper repository? Same question actually for all other repositories that people everywhere advice you to add...

---

### Post by Gustav on 2006-01-10
You should remove your Dapper repository as quick as possible since it will make bad stuff when you update.

---

### Post by pbb on 2006-01-10
Okay thanks, doing that!

---

### Post by NoWhereMan on 2006-01-10
Dapper is the next release of ubuntu; you shouldn't leave there that repo, because it's still under development ;)

btw, I'm really happy to have been of help! :D 
Cheers, mate ^_^

---

