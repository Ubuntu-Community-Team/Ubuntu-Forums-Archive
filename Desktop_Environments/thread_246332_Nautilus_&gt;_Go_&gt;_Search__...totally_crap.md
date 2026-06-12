---
title: "Nautilus &gt; Go &gt; Search  ...totally crap?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by latebeat on 2006-08-29
Hi there,

I don't know if the search function works for everyone else *but* me, but on my machine it's utterly CRAP! It never finds anything or finds totally irrelevant results.


An image is worth 1000 words so here are some screenshots:


A random folder
[IMG]http://store.itsyourftp.com/~latebeat/Pics/f1.png[/IMG]


Search for that single file in it!! 
[IMG]http://store.itsyourftp.com/~latebeat/Pics/f2.png[/IMG]
No results!


Search for *.pst
[IMG]http://store.itsyourftp.com/~latebeat/Pics/f4.png[/IMG]
No results


Search for *.png
[IMG]http://store.itsyourftp.com/~latebeat/Pics/f3.png[/IMG]
How do these even relate to png!


Why is it so useless? Is it supposed to actually do anything or is there something wrong with my installation? Gnome-search-tool works fine as can be seen below but sometimes it's nice to be able to do a quick search inside a folder from nautilus.

[IMG]http://store.itsyourftp.com/~latebeat/Pics/f5.png[/IMG]

---

### Post by andrewlondonuk on 2006-08-29
I'm sorry i can't help but could you tell me what theme and icon packs you have installed. That install looks mint.

Again, sorry i can't help.

---

### Post by latebeat on 2006-08-29
> **andrewlondonuk said:**
> I'm sorry i can't help but could you tell me what theme and icon packs you have installed. That install looks mint.

Again, sorry i can't help.

Icons: Vista-Inspirate
Theme: VistaBut and changed the window borders to resilience
all from gnome look.

Please keep the thread on the topic
 :D

---

### Post by justin whitaker on 2006-08-29
Hmm, I found the same thing when I tried it...I use beagle, though, so I usually search through that.

---

### Post by VirtuAlex on 2006-08-29
Something is defenitely wrong. On my machine it is able to find exact file. It does not seem to understand wildcards like *, but it just finds nothing instead of completely unrelated stuff... It works if I omit * altogether.

---

### Post by latebeat on 2006-08-29
> **VirtuAlex said:**
> Something is defenitely wrong. On my machine it is able to find exact file. It does not seem to understand wildcards like *, but it just finds nothing instead of completely unrelated stuff... It works if I omit * altogether.

mmm
have you set up beagle with extended attributes or not? Do you know ?

---

### Post by VirtuAlex on 2006-08-29
No, I do not use beagle. I usually search with find or with Gnome Commander when I don't feel like typing. However I think Gnome Commander suck. Had I use kde I would employ Krusader for it. It is much better, but unfortunately does not fit into gnome very well.

---

### Post by SirKillalot on 2006-08-29
works perfectly for me..

---

### Post by latebeat on 2006-08-29
> **SirKillalot said:**
> works perfectly for me..
Any points or suggestions to fix it then ?
Have you set-up beagle as well? Are u using extended attributes?

---

### Post by kerry_s on 2006-08-29
I use the deskbar it gives you multiable ways of searching, dang handy little app and it's already installed. add to panel>deskbar

---

### Post by BuffaloX on 2006-09-01
> **kerry_s said:**
> I use the deskbar it gives you multiable ways of searching, dang handy little app and it's already installed. add to panel>deskbar

Thanx cool, but dosn't work with Samba, unless thay are mounted...

---

### Post by latebeat on 2006-09-01
> **kerry_s said:**
> I use the deskbar it gives you multiable ways of searching, dang handy little app and it's already installed. add to panel>deskbar

I have the deskbar installed as well but it's not quite the same thing is it? Sometimes I would like to just use nautilus search thing to search quickly withing huge folders.

---

### Post by Anduu on 2006-09-01
Give this a shot...Open a terminal and type:

```
sudo updatedb
```

then try a search.

---

### Post by pt123 on 2006-09-01
My problem is that it doesn't search in the folder I am in & subfolders. But resorts to my "HOME" folder which is not intuitive is there a way to fix this?

---

### Post by Atomic Dog on 2006-09-01
I have the same issue in nautilus -totally clean ubuntu install.  The search bar that was suggested works...not exactly what I want, but better than nothing.

---

### Post by LKRaider on 2006-09-02
Nautilus search feature is really counter-intuitive

A few bug reports relating to this:
[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/28537](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/28537)
[http://bugzilla.gnome.org/show_bug.cgi?id=340332](http://bugzilla.gnome.org/show_bug.cgi?id=340332)
[http://bugzilla.gnome.org/show_bug.cgi?id=328725](http://bugzilla.gnome.org/show_bug.cgi?id=328725)

---

### Post by Anduu on 2006-09-02
I never use search via nautilus anyway.I just use the "search for files" option from the places menu.There I can be as specific/general as I wan't...

---

### Post by 3rdalbum on 2006-09-02
I ended off installing kfind from repos. That definately works.

---

### Post by latebeat on 2006-09-02
> **pt123 said:**
> My problem is that it doesn't search in the folder I am in & subfolders. But resorts to my "HOME" folder which is not intuitive is there a way to fix this?

Exactly right on the money...
Not everything is located in my HOME directory.

---

### Post by latebeat on 2006-09-02
> **3rdalbum said:**
> I ended off installing kfind from repos. That definately works.

You don't need kfind, gnome-search-tool works quite well. However, the topic is why nautilus doesn't search the directories that you're in.

---

