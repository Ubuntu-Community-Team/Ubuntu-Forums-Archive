---
title: "Desktop blog editing?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by uzusan on 2006-07-03
Does anyone know of any good blog editing programs?

Im looking for something that will work with both Ubuntu and XP. Although XP support is optional as i can just use qumana for that.

I need a program that can link into a wordpress blog.

I could just use the web interface, but i prefer using a desktop program.

---

### Post by lexios on 2006-10-30
Unfortunately, there is none! I have searched for hours and I am very dissapointed.

Seems like there is a Performancing plugin for firefox, but does not work on FF2. I found another called Drivel but it was not covering my needs.

There are plenty of editors in Win but just few for linux. SAD.

---

### Post by ioslipstream on 2006-10-30
Blogtk is about the most full featured blogging client available in the repos.  Performancing for firefox does work in FF2.

---

### Post by StackError on 2006-12-07
> **ioslipstream said:**
> Blogtk is about the most full featured blogging client available in the repos.  Performancing for firefox does work in FF2.
BlogTk is pure crap !!!!!!!!!!
performacing is a bit better... but what i don't understand is why no one is the vast Linux universe hasn't written a quality Blog Editor for Linux!!!!!
I would like to see something that is a cross between W.Bloggar or BlogJet with the Technorati tagging options!!!

If any one ever does..please let me know asap!!!!!

or better yet maybe someone can figure out how to get BlogJet or W.bloggar to run in wine! I have tried and they just wont run!!!!!

SE

---

### Post by 23meg on 2006-12-07
See if these work for you:

[http://www.dropline.net/drivel/](http://www.dropline.net/drivel/)
[http://www.gnome.org/~seth/gnome-blog/](http://www.gnome.org/~seth/gnome-blog/)

---

### Post by StackError on 2006-12-11
I am looking for something with professional editing tools, ping lists, tagging, and keyworking, something like blogjet or w.bloggar

Thx
SE

---

### Post by Mateo on 2007-01-14
BlogTK doesn't support more than 1 category, nor does Drivel.  Also, I don't think either work that well with wordpress blogs.  I think BlogTK works with it, but the categories don't even show up.  Ohh well, i guess we'll have to wait for further development and just use wordpress' own program until then.

---

### Post by AvixK7 on 2007-04-29
I'm a bit late in the discussion but you could try the blog feature in the flock web browser.

---

### Post by mbirth on 2008-06-15
As Qumana is a Java app, you can use it on Ubuntu, too. Just download the Mac ZIP-file and dig in the "Resources" directory inside. You'll find the Qumana.jar and some sub-directories. Unpack them to a dir and launch "java -jar Qumana.jar" to start Qumana.

I'm just trying to find out, why it crashes when trying to edit a post. If I sudo it, it runs fine.

Cheers,
  -mARKUS

**UPDATE:**
After some search, I found out that the problem lies with the Java GtkLookAndFeel. When running as root, it doesn't know of Gnome and launches in MotifLookAndFeel. This is why it worked. To let it not discover Gnome, launch it like:

env -u GNOME_DESKTOP_SESSION_ID java -jar Qumana.jar

Have fun!

---

### Post by BloGTK on 2008-06-18
> **StackError said:**
> BlogTk is pure crap !!!!!!!!!!
performacing is a bit better... but what i don't understand is why no one is the vast Linux universe hasn't written a quality Blog Editor for Linux!!!!!
I would like to see something that is a cross between W.Bloggar or BlogJet with the Technorati tagging options!!!

If any one ever does..please let me know asap!!!!!

or better yet maybe someone can figure out how to get BlogJet or W.bloggar to run in wine! I have tried and they just wont run!!!!!

SE

Heh, I beg to differ. BloGTK is in fact 62.5% crap, and the rest is sawdust filler.

BloGTK does actually support most of what you want. The Advanced tab lets you do keywords/tags (which are the same in WordPress), and you can ping multiple addresses in the TrackBack URI field by separating each address with a comma. The only drawbacks are that the editor sucks, and there's no multiple category support.

Someone really should make a version of BloGTK that's a complete from-the-ground rewrite with syntax highlighting, undo/redo, better spell check, etc... maybe it could even support multiple categories too...

---

