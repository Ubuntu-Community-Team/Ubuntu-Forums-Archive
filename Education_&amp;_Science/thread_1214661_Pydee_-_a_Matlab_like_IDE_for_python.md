---
title: "Pydee - a Matlab like IDE for python"
date: 2009-07-16
forum: Education &amp; Science
---

### Post by ahmatti on 2009-07-16
I just came across an interesting software: Pydee [http://code.google.com/p/pydee/](http://code.google.com/p/pydee/). It is a Python development environment that looks very similar to Matlab. 

I just installed from source and after initial testing it has a very nice feel to it. Indeed with numpy+scipy+matplotlib the experience is very Matlab like, but it seems nice also for general python development. 

It is also cross-platform, which is nice for me because I also need to use windows for teaching (we only have windows in classrooms) I also like cross platform tools in a sense that they can help post grad students to migrate to *nix, which so much more powerful in our line of research. 

Just thought to let you know, in the hope that this helps someone :) I know I have spent quite some time looking for a good python environment.

---

### Post by prvteprts on 2009-07-19
Looks nice. Although I need help in installing. I downloaded the tarball, but there are no configure or make files. How exactly do I install it? Thanks.

---

### Post by ahmatti on 2009-07-19
> **prvteprts said:**
> How exactly do I install it? Thanks.
This is from the Pydee wiki [http://code.google.com/p/pydee/wiki/Installation:](http://code.google.com/p/pydee/wiki/Installation:)

First install the depency:
```

sudo apt-get install python-qscintilla2
```

Then install with the command:
```
sudo python setup.py install
```

Worked for me!

---

### Post by prvteprts on 2009-07-22
Thanks! I tried running setup.py but I did not know that I was missing some dependencies. Though it seems Pydee is not very well documented. Any idea where I could find a decent manual or tutorial?

---

### Post by ahmatti on 2009-07-23
Not apart whats on the website. It is easy enough to use though so you should be able to figure it out :) The menus show the accelerator keys e.g for executing code from the editor in the console. Also you can drag the IDE windows (editor, console,history etc.) to different location using the mouse and the website shows the different start up options.

All in all the experience is very Matlab like.

HTH

---

### Post by prvteprts on 2009-07-24
Yeah, it's easy enough that I could use it right away. I just wish they or someone else would write a manual for it. Thanks for everything!

---

### Post by disophisis on 2009-10-21
bookmarked this - thanks for the info.  I'll try it out.  I'm new to python, i'm currently taking a course... a good IDE for linux would be a nice help.

---

### Post by tuwe on 2009-10-22
> **disophisis said:**
> bookmarked this - thanks for the info.  I'll try it out.  I'm new to python, i'm currently taking a course... a good IDE for linux would be a nice help.

The project was recently renamed to spyder. The new url is [http://code.google.com/p/spyderlib/](http://code.google.com/p/spyderlib/)

---

