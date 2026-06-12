---
title: "Unable to install a game"
date: 2009-06-05
forum: General Help
---

### Post by yonyz on 2009-06-05
I've downloaded a game called 'Foldit' as a .tar.gz archive. I was able to extract it's contents into a new folder, but I'm not able to install it using the './configure' and 'make' commands, even though I had navigated into the archive's newly created folder. The readme file says: "To start the game, run Foldit from this directory". So I run it, and it only created a file called 'initial_run'.
A screenshot of the terminal is attached.

What should I do to install the game?

[IMG]http://i41.tinypic.com/33v11fc.png[/IMG]

---

### Post by michy99 on 2009-06-05
I downloaded Foldit to see if I could get it to work. Turns out you need to have libglut3 installed.```
sudo apt-get install libglut3
```When you start it again, it might give you an error message about not starting correctly the first time, but then it should work.

---

### Post by yonyz on 2009-06-05
It said that when I tried to start it through the Terminal. Now it works.
Thanks.

---

