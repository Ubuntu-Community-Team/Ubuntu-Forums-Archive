---
title: "gdm no longer starts"
date: 2004-12-04
forum: Desktop Environments
---

### Post by sunset_studies on 2004-12-04
Hello, first post, so please be gentle...

I have been using Ubuntu now since the official release, and it has all worked fine. This morning though, I boot up as usual, the GDM cursor (cross) appears, but that's it. Rather than seeing the login screen, the screen blanks and I am asked something about attempting to reload X even though it already seems to be running. Answering yes/ no just results int the same cursor>blank screen>X question cycle. 

Has this happened to anybody else? I did install/upgrade some packages yesterday, possibly even GTK if I remember correctly. 

Thank you for your time.

---

### Post by Xian on 2004-12-04
I recall a post on this forum regarding that type of error message. As I recall their solution was to delete a particular file located in the tmp directory. Do a search here and see if you can locate that thread, as I am fairly certain their situation was similar to yours.

---

### Post by sunset_studies on 2004-12-04
I found this: [http://ubuntuforums.org/showthread.php?t=5579&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=5579&page=1&pp=10) and it did provide a workaround (kill X and run startx) but I couldn't find mention of deleting any files in order to provide a clean fix (i.e. I don't miss the pretty GDM login screen).

---

### Post by Xian on 2004-12-04
Okay, I found it. Here's the thread I was referring to in my previous post.
There have been a few more contributions since my last read-in.

[Can't Start Ubuntu](http://ubuntuforums.org/showthread.php?t=5947&highlight=gdm)

---

### Post by sunset_studies on 2004-12-05
Thanks! Installing a new version of GDM did the trick.

[http://gnome-look.org/content/preview.php?preview=1&id=18178&file1=18178-1.jpg&file2=&file3=&name=Tobacco+Sky](http://gnome-look.org/content/preview.php?preview=1&id=18178&file1=18178-1.jpg&file2=&file3=&name=Tobacco+Sky) is a GDM login screen far too beautiful to miss.

---

