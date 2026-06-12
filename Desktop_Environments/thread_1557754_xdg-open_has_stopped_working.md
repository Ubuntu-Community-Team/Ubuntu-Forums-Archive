---
title: "xdg-open has stopped working"
date: 2010-08-21
forum: Desktop Environments
---

### Post by Zalbor on 2010-08-21
This is kind of a strange issue. xdg-open is supposed to open any kind of file or directory in the desktop manager's default application for that kind of file, whatever the desktop manager might be. I'm using KDE, and this used to work perfectly.

For a couple of weeks now (at the least) it has somehow stopped working. This is the output I get when trying to open a simple text file:
```
$ xdg-open /home/user/Desktop/text
Warning: unknown mime-type for "/home/user/Desktop/text" -- using "application/octet-stream"
Error: no "view" mailcap rules found for type "application/octet-stream"
```
this is for an image:
```
$ xdg-open /home/user/Desktop/image.jpg 
Error: no "view" mailcap rules found for type "image/jpeg"
```
and this is for a directory:
```
$ xdg-open /home/user/Desktop/
Warning: unknown mime-type for "/home/user/Desktop/" -- using "application/octet-stream"
Error: no "view" mailcap rules found for type "application/octet-stream"
```

Putting double quotes around the file's address makes no difference, and URLs still work fine.
I've tried it with different kinds of files, in different directories, created by different programs.

Does anyone have any ideas?

EDIT: As far as I know, xdg-open simply calls the DM's specific command to open things, which in my case is kde-open. kde-open works fine, so it should be something "between" xdg-open and kde-open that causes the problem.

---

### Post by ben2talk on 2011-05-24
No fixes for this?

My xdg-open simply opens Nautilus for everything. If I click 'play' in Miro it opens Nautilus, images and pdf's downloaded in firefox and chromium also open Nautilus...

This sucks!

---

### Post by Copper Bezel on 2011-05-25
If you read this before I edited it, don't do what I suggested, or undo it. Please only post your problem in one thread or, otherwise, include all of the details when you repost it. = )

---

