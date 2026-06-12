---
title: "Nautilus bug, crashes when right clicking .mp4 files and selecting properties"
date: 2005-12-11
forum: Desktop Environments
---

### Post by ndhskp on 2005-12-11
Nautilus crashes every time when right clicking .mp4 video files and selecting properties. Is any workaround to this problem available.  It's not critical but I would like to be able to access the properties dialog box on a file without Nautilus crashing.  Any ideas on this would be great.

This is the specific file in question however this happens with all .mp4 video files.

[http://smartdelivery.watchmactv.com/mactv/mp4/087-ConaniPod.mp4](http://smartdelivery.watchmactv.com/mactv/mp4/087-ConaniPod.mp4)

---

### Post by bvc on 2005-12-12
also happens when getting the properties of any image filetype
....pretty sad for a 'stable' release :rolleyes:

---

### Post by ndhskp on 2005-12-12
What are you talking about exactly.  When I click on jpeg and tif files I get the properties dialog just fine.  I use 5.10.  Maybe there is a per user config problem in Nautilus that causes some file types to crash & not others depending on the needs of the user.  For example a heavy video user may have something set up favoring video files and thus causing crashes of certain file types.  And of course  office, programmers, audio editors ect. users may see other types of file crashes.  The real problem is that Nautilus continues to remain dependant on third party libs to display thumbnails, properties ect.  As a result if the xine engine can't handle .mp4 then Nautilus goes poop.  Maybe your image libs are giving Nautilus the finger when it calls on them.  But really Nautilus shouldn't be calling on those 3rd party libs and instead if they can't handle it, it should obtain the properties via some non-interactive way with the file.

---

### Post by linkunderscore on 2005-12-12
[QUOTE=bvc]also happens when getting the properties of any image filetype
....pretty sad for a 'stable' release :rolleyes:[/QUOTE]

No it doesn't ?

---

### Post by bvc on 2005-12-12
Well it does here on breezy....
Of course this is not a clean install....it's been upgraded all the way from beta warty but that shouldn't be an excuse after cleaning $HOME of gnome config stuff. No biggy really, I can just open the image in an image viewer. Just a little annoying I can't rt-click>properties.

---

### Post by linkunderscore on 2005-12-12
I am using breezy...an uprgrade from hoary and it works fine for me :shrug:

---

### Post by mcpish on 2005-12-12
Yes I have the exact same problem, I'm glad it's not just me.

---

### Post by ustrucx on 2005-12-13
I have many problems with libs showing finger to my poor nautilus, like librsvg and its a know bug that crash anything that have a .svg, like a menu icon or a thumb inside nautilus, and this is only on some instalations, some ppl dont even know that there is a bug there hehe.
And its a brand new instalation.
I have a friend that says nautilus dont EVER crash, i have to show my finger to him :p.

---

### Post by talz13 on 2007-01-01
It's an old post, but I'm having the exact same issue now on edgy!  I have some mp4 files, and I cannot access the properties because nautilus crashes whenever I right click and hit properties.  Are there any known issues with this anymore?

---

### Post by raul_ on 2007-01-01
Really old thread :D try typing
```

nautilus

```

in the terminal and when it crashes see if something pops up in the terminal

---

### Post by talz13 on 2007-01-05
Hmm, I thought there would be something more interesting to come from that, but all it displayed was:

```
jeff@jeff-laptop:~$ nautilus

** (bug-buddy:5278): WARNING **: Couldn't load icon for Open Folder
jeff@jeff-laptop:~$ 

```


I tried it the first time when I had backgrounded a few processes in this window, and got one other message, but I'm not sure if it's related or not:
```

** (bug-buddy:5207): WARNING **: Couldn't load icon for Open Folder
Previous frame inner to this frame (corrupt stack?)

```

---

