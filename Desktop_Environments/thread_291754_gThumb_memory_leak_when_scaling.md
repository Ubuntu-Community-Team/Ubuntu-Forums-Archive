---
title: "gThumb memory leak when scaling"
date: 2006-11-02
forum: Desktop Environments
---

### Post by superTP on 2006-11-02
Hello, all,
I am running into what appears to be a memory leak in gThumb or one of it's dependent libraries.  I have about 100 large (2500x2000) pictures on my digital camera that I want to share on the web.  I selected all of them in gThumb then ran Tools->Scale Images to scale them down to a reasonable size for web viewing.  Before I knew it, all of the memory in my system was used up and the machine came to a grinding halt.  

I tried a couple more times using a smaller number of pictures.  Looking in system monitor I can scale about 10-12 images before all of the memory in my system is used up.  The really annoying part and what qualifies this as a memory leak to me is that I have to close qThumb before the memory is freed.   It would be on thing if I could only scale 10 at a time but right now, I can only scale 10-12 **per session** in gThumb.  

Anyone seen this?  A quick google search doesn't turn up anything.

---

### Post by po0f on 2006-11-02
superTP,

I don't know about gThumb leaking memory (have no real use for the program since I don't own a digital camera), but maybe you can use ImageMagick instead to hack together a script that will convert all your images for you? [Click](http://www.imagemagick.org/script/command-line-processing.php).

---

### Post by superTP on 2006-11-03
Thanks for the tip.  I talked to the upstream guys and this is fixed in their current source tree.

[http://bugzilla.gnome.org/show_bug.cgi?id=349576](http://bugzilla.gnome.org/show_bug.cgi?id=349576)

---

