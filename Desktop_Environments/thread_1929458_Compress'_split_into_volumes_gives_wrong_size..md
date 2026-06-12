---
title: "Compress' split into volumes gives wrong size."
date: 2012-02-22
forum: Desktop Environments
---

### Post by ickefes on 2012-02-22
Hi fellows.
I want to create CD's with compressed archives using 7z (only file type that I can supporting split volumes) and after that making redundancy files with PAR2. Therefore I need the compressed files to be around 630 MB so that a 10% PAR2 redundancy file will take up ~690 MB of a CD. The problem is that when I set the split volumes to 630 MB using 7z algorithm it ends up as 660 MB which will then with 10% redundancy end up bigger than my CD's can store.

I am using Ubuntu 11.10 x64/amd64 with all the latest updates up 'til today.
Regards.

---

### Post by ickefes on 2012-02-22
I tried installing the rar plugin/extension and set the split volumes to 630 MB but it ended up as 660 MB with rar too. Just wanted to let you know. I will use WinRAR through WINE for now to be sure that it all will work without any worries for now.

Do you guys maybe have a recommendation for a GUI program similar to WinRAR (with precise split volumes among things) but open source?

Regards

---

### Post by jwbrase on 2012-02-22
What you're running into is confusion related to the fact that "mega" traditionally means "1 million", but that in computer related contexts it often means "1,048,576". 7zip is using the "1,048,576" definition, and some other program you're using (likely something Windows based, as Linux and applications for Linux tend to use the "1,048,576" definition pretty consistently) is using the "1 million" definition.

It's not a bug in any of the programs you're using, but rather a "people using the same word with different meanings" issue.

630 megabytes with mega meaning 1048576 is approximately equal to 660 megabytes with mega meaning 1 million. Specifying a size of 600 megabytes to 7zip (which seems to be using the 1048576 definition) should give you 630 megabytes as seen by a program that uses the 1 million definition.

See: [http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)

---

### Post by ickefes on 2012-02-22
Thank you jwbrase. I think understand somewhat what your saying. So a CD that can hold stated 700 MB of storage is actually around 734 MB in "non-Windows" terms? Regards.

---

### Post by ickefes on 2012-02-22
No need for more assistant. I will look for MiB vs MB and KiB vs KB in the future to know the difference and use calculators to know which size I want for files to fit certain mediums.

Regards.

---

