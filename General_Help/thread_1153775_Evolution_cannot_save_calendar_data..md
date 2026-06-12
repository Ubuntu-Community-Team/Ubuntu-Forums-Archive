---
title: "Evolution cannot save calendar data."
date: 2009-05-09
forum: General Help
---

### Post by kozlovsk on 2009-05-09
Evolution cannot save calendar data: Error opening file... No such file or directory.


Jaunty system, fresh install. After Evolution first start .evolution folder is created in home folder normally. After entering Tasks data got the message:

[IMG]http://ubuntuforums.org/picture.php?albumid=1085&pictureid=3863[/IMG]



there is actually no local/system/tasks.ics in .evolution/tasks at all and the file in not created

same problem with Calendar and Memos data 

permission problems? but the whole .evolution folder with some files in it is created normally. Tried 777 permissions with no luck.

Have taken a look at the 8.10 structure of .evolution folder:
In 8.10 we had .evolution/tasks/local/system/tasks.ics
same thing for memos, calendar adn addressbook
In 9.04 there are no "local" directories at all


Tried to delete .evolution, and it is recreated normally upon the next restart of Evolution, but again with no "local" directories in it.



P.S.

After right click > Properties on .evolution folder got this error:

[IMG]http://ubuntuforums.org/picture.php?albumid=1085&pictureid=3864[/IMG]

may be it will give a clue to someone?

Thanks for your time!

---

### Post by kozlovsk on 2009-05-09
Solved it.

I had finnish language set in System > Administration > Language support (actually didn't have all the components of it installed)

Changed it back to English (United States), logged in again, deteted .evolution, and launched Evolution

.evolution was created with all the necessary files.

---

### Post by kozlovsk on 2009-05-09
Kinda asked myself, and answered myself  ;)

Can't find how to mark thread as SOLVED.

---

