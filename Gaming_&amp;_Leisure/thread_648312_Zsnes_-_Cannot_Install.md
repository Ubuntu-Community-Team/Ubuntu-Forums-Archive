---
title: "Zsnes - Cannot Install"
date: 2007-12-23
forum: Gaming &amp; Leisure
---

### Post by Lord DEA on 2007-12-23
Hello everybody,

I'm trying to install Zsnes to Ubuntu Feisty. Here's what I did:

-  I downloaded the file from www. Zsnes.com. (the name of the file is zsnes151src.tar.bz2).
-  I extracted it, and got two folders: "docs" and "src".
-  I looked into the src folder for the file "install-sh", and clicked it.
-  A window is displayed asking mo what to do with the file: "Run in terminal", "Display", "Cancel" and "Run".
-  After I click "Run", nothing happens.
-  I also tried "Run in terminal", but the terminal closes right after it opens.
-  If I select "Display", guess what.... nothing happens. The text editor doesn't even show up.

Please help me with this.

Thanks.

---

### Post by zcal on 2007-12-23
Go to your terminal and enter
sudo apt-get install zsnes

Easy peasy.

---

### Post by acoustibop on 2007-12-23
Presumably the OP wants to use 1.51 rather than 1.43, zcal.  1.43 is the version in the Feisty repositories.  I did the same when I was using Feisty.

@Lord DEA: Since you're downloading the source rather than a pre-compiled package, you'll have to compile it before installing it.  If you look in the docs folder, there should be instructions on how to do this.

You may be able to find pre-compiled .debs for 1.51 - I think they have been posted in this forum, if you'd care to search.

---

### Post by zcal on 2007-12-23
> **acoustibop said:**
> Presumably the OP wants to use 1.51 rather than 1.43, zcal.

Nah.  Looks like a general request for help getting the program running.  Repos are always the easiest solutions.  1.43 ought to be fine for most games.

---

