---
title: "is awn working correctly?"
date: 2007-02-13
forum: Desktop Environments
---

### Post by shrndegruv on 2007-02-13
Hey

I installed awn from svn last night, and dont know if the following are bugs or "features"

1.  when i start it, first time i right click i can add a launcher.  but then every other time i right click it gives me preferences or close as an option.  meaning i cant add another launcher
2.  preferences doesnt do anything.
3.  when i restart awn, it loses the launcher i set in the previous run.

can someone lemme know if theres works similar?  right now seems useful as a window list and nothing more....

---

### Post by kenkun on 2007-02-13
hm mine works differently. i dragged apps from the Menu Bar on to the awn bar to add launchers.  and when i restart awn, it doesnt lose the launchers i've set up. try doing a clean reinstall.. i had a couple of problems with it until i did one..

---

### Post by shrndegruv on 2007-02-13
right so originally I installed from source, available on the google hosting site, then I downloaded from svn.  

how would i completely remove my installation?  i tried make uninstall but it doesnt seem to help

---

### Post by kenkun on 2007-02-13
```
sudo apt-get autoremove avant-window navigator
```

try installing the svn released by reacocard, his works best for me.. go [here]("http://www.ubuntuforums.org/showpost.php?p=2121429&postcount=73") and follow his instructions.. omit the last wget because you will not need it.. it gives you a 404 error anyway.. 

hope that helps!

---

### Post by shrndegruv on 2007-02-13
thanx

i followed those and now my launchers persist, but i still cant call up preferences...

---

### Post by kenkun on 2007-02-13
i call up mine by right clicking the most left side of awn.. give it a shot!

---

### Post by shrndegruv on 2007-02-13
right thats what ive been trying to do.  the option is there but nothing happens.

i bet something is left over from when i downloaded the source and manually installed...is there any way to tell which files get installed?

---

### Post by kenkun on 2007-02-13
hm thats odd.. 
how about typing
```
avant-preferences
```
on terminal?

i'm afraid i can't answer your question there.. hopefully someone else can answer it..

---

### Post by shrndegruv on 2007-02-13
i get the following

```

/usr/local/share/avant-window-navigator/window.glade

(avant-preferences:9724): libglade-WARNING **: could not find glade file '/usr/local/share/avant-window-navigator/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 250, in ?
    app = main()
  File "/usr/local/bin/avant-preferences", line 125, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=APP) 
RuntimeError: could not create GladeXML object

```

now, when i installed from source the executable went in /usr/local/share, but my current exe, from svn build is in /usr/bin.  Its looking in the wrong place--there is a window.glade file in /usr/share/avant....

---

### Post by kenkun on 2007-02-13
well i suppose you could try to copy it over.. :lol: (just talkin out of my a$$, but if worth a shot)

---

### Post by reacocard on 2007-02-13
> **shrndegruv said:**
> i get the following

```

/usr/local/share/avant-window-navigator/window.glade

(avant-preferences:9724): libglade-WARNING **: could not find glade file '/usr/local/share/avant-window-navigator/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 250, in ?
    app = main()
  File "/usr/local/bin/avant-preferences", line 125, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=APP) 
RuntimeError: could not create GladeXML object

```

now, when i installed from source the executable went in /usr/local/share, but my current exe, from svn build is in /usr/bin.  Its looking in the wrong place--there is a window.glade file in /usr/share/avant....

Just do a 
```
sudo rm /usr/local/bin/avant-preferences
sudo rm /usr/local/bin/avant-window-navigator
```
That'll get rid of any remaining executables from your source install, which should eliminate your problem.

---

### Post by shrndegruv on 2007-02-14
that got 'em!

thanx

---

