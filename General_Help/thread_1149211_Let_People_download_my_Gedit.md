---
title: "Let People download my Gedit"
date: 2009-05-05
forum: General Help
---

### Post by mdgrech on 2009-05-05
I've turned gedit into an amazing text editor that is perfect for web development.  Many of my friends have requested it...what is the easiest way I could package gedit with all my plugins and custom snippets so they could just easily download it and install it?  Thanks guys.

---

### Post by kpkeerthi on 2009-05-05
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)
[http://fridge.ubuntu.com/node/1125](http://fridge.ubuntu.com/node/1125)

---

### Post by mdgrech on 2009-05-05
blah... lol I take it there isnt any easy way?

---

### Post by wsonar on 2009-05-05
What other plugin's do you need?

I'm happy with it just coloring my code for me :)

---

### Post by FluffyElmo on 2009-05-05
Custom settings are saved in the* ~/.gnome2/gedit/* directory, for instance plug-ins are generally stored in *~/.gnome2/gedit/plugins/*, so in theory you could just copy that directory to their system and be good to go. 

I haven't actually done this so there may be some issues depending on the specific plug-ins you use but it should give you a place to start.

---

### Post by mdgrech on 2009-05-06
mmm that sounds like a start...it sounds like the package would contain gedit...and the settings found in ~.gnome2/gedit  LoL now I just need to figure out how to package it.

---

### Post by mdgrech on 2009-05-06
@wsonar  I added a file browser plugin, the embedded terminal plugin, and the web browser plugin.  It also has auto-complete functionality, along with syntax highlighting capability for Ruby on Rails.  In addition I also have included a ton a useful starting templates, along with snippets that can dramatically speed up the coding process.  It's truly a full blown ide, but each of those features can easily be turned off/hidden, and its still ultra light weight after all it is gedit!

---

### Post by albinootje on 2009-05-06
> **mdgrech said:**
> It's truly a full blown ide, but each of those features can easily be turned off/hidden, and its still ultra light weight after all it is gedit!

Sounds serious.. well done! 

Why don't you let someone else package it, and have a project page under a different name ?
Did you contact the author(s) of Gedit already ?

---

### Post by mdgrech on 2009-05-06
I like that idea, I do web development so i could easily create a product page.  I have not contacted the authors of gedit yet but maybe I should do that.  Would anyone here be willing to package it for me (please pretty pretty please)?

---

### Post by monsterstack on 2009-05-06
Maybe you could attach the files you have made or edited here.

---

### Post by benj1 on 2009-05-06
could you not just create a download script?

---

### Post by mdgrech on 2009-05-06
Alright I archived my ~/.gnome2/gedit directory and have attached it to this reply.  Thank you for willingness to archive it!!

To others who are following this post feel free to test it out on your local gedit by unzipping the contents and replacing ~/.gnome2/gedit with the folder you just unzipped and make sure to let me know what you think :)

---

### Post by mdgrech on 2009-05-08
anyone? :)

---

### Post by albinootje on 2009-05-08
> **mdgrech said:**
> anyone? :)

I downloaded your gedit plugins, and tried the web browser plugin, that's a nice surprise :)

By the way, I suggest to remove the .pyc files from the tar.gz archive, they contain your username it looks like.

About packaging for Debian see here to get an idea :
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

