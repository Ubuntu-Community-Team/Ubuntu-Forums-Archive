---
title: "[SOLVED] Icons in Nautilus don't work (in large parts)"
date: 2008-02-08
forum: Desktop Environments
---

### Post by tcommbee on 2008-02-08
I have the following problem(s) in nautilus:
-previews of any sorts aren't generated, i.e. text, office documents, pdfs, images, sound, etc. (but the sandglass (respectively speech bubble) icon appears)
-filetypes are only detected by extension, not content sniffing, i.e. /etc/fstab is of type "unknown", accordingly no apps are associated with "unrecognized" files

forumsearch and google didn't tell anything helpful
-i already checked, that thumbnailers are installed and set in gconf
-reinstalled nautilus
-deleted thumbnail folder
-tested as other user
-reinstalled every single package that could possibly have to do with the problem
-checked files in /usr/share/mime and /usr/share/applications
-did update-mime-database /usr/share/mime
-restarted a zillion times
any ideas?

---

### Post by tcommbee on 2008-02-08
bump

---

### Post by tcommbee on 2008-02-09
bump

---

### Post by tcommbee on 2008-02-09
bump

---

### Post by tcommbee on 2008-02-10
bump

---

### Post by vikrant82 on 2008-02-11
Buddy I am facing similar problems. Its strange there's no related bug in launchpad. I am too lazy to do that .. :popcorn:

More so I am even noticing that nautilus cannot delete non-empty directories in my other NTFS partitions ...

---

### Post by tcommbee on 2008-02-11
A friend of  mine now has the same issue... anyone else? i'll probably file a bug then

---

### Post by kristian on 2008-02-12
I also have troubles with thumbnails not geting generated. However if I open a image with eog and then reloads the folder with nautilus that image will have a thumbnail.

---

### Post by tcommbee on 2008-02-12
then you're luckier than i

---

### Post by vikrant82 on 2008-02-13
With today's nautilus updates, I am starting to get my thumbnails again. :)
But still no luck with deleting non-empty folders on other partitions.

---

