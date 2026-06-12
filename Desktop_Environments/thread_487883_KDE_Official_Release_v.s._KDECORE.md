---
title: "KDE Official Release v.s. KDECORE"
date: 2007-06-29
forum: Desktop Environments
---

### Post by evolving_monkey on 2007-06-29
Hello all,

I have Ubuntu loaded and I want to add KDE. I was curious what the the community thinks.
I am looking at the KDE official modules or just adding the kde-core and adding to it what I need.

Also I wasn't sure if the KDE official modules would conflict with Ubuntu/Kubuntu. I considered just adding the kubuntu-desktop but I wasn't sure if I really wanted or needed everything in it.

Thanks for your thought s and comments.

---

### Post by benerivo on 2007-06-29
I would just install the kde core. It gives you a full working desktop, but you may not have the 'extras' that go with it such as the k3b cd burner, or amarok, or probably 20 other things most of you might never use. The kde official modules include all the alternatives to the Gnome packages so that Kubuntu is a full distro by itself. I don't beleive there is any conflict, and you may use kde programs in Gnome and vice-versa. I have done it myself and just added what i wanted to the core selection, and it worked fine.

---

### Post by evolving_monkey on 2007-06-29
Thanks benerive. Sounds like good advice. I'm firing up Synaptic now.

---

### Post by Freddy on 2007-07-01
Don't use synaptic for this, you might want to delete your kde.core later on. 
Use ```
sudo aptitude install kde-core
```
instead.
Aptitude is a far better choice cause it will remove all unnecessary dependencies if you after trying kde out, choose to delete it.

/Freddan

---

### Post by evolving_monkey on 2007-07-02
Unfortunately I didn't receive the post until after I had already installed kde-core through synaptic. Is it still "safe" this way?

If everything is fine for now I will probably just leave it. I am still pretty new to Linux so I have accepted the fact that i will probably end up reloading at some point due to a goofy noob mistake. After said future noob mistake occurs I will try to load it that way. 

Also, is it better to load software in general that way? Should I just use Synaptic to view the package explanations and then install via command prompt? Do you then go back and install the recommended and suggested software options you want in the same way? 

So far I am really impressed with Ubuntu. I'm not an OS zealot, but I am beginning to understand why so many prefer Linux over Windows. I appreciate any suggestions the community has to offer.

Thank you for your replies.

---

