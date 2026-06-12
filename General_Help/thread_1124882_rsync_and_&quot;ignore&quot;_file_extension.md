---
title: "rsync and &quot;ignore&quot; file extension"
date: 2009-04-13
forum: General Help
---

### Post by wesg on 2009-04-13
I'm thinking of my media server, and have made a bash script that converts m4a files to mp3 so that mediatomb can use it. I'm going to use the directory as an archive of all my media, which means using rsync.

How can I get rsync to only copy based on the file name, and essentially ignore the extension? 

So for example, files aaa.mp3 and bbb.mp3 exist in my archive, and files aaa.m4a and ccc.m4a exist in my copy source. How can I get rsync to ignore aaa.m4a because aaa exists in the archive, but still copy ccc.m4a.

Thanks!

---

### Post by HalPomeranz on 2009-04-13
There's no rsync option to do what you want to do.  You'll have to write a script that compares the list of files in each directory without the file type extensions (hint: the "basename" command is your friend here) and generates a list of files that need to be copied.

---

### Post by fredharris on 2010-12-21
Did you manage to find a solution? I need the exact same method of syncing.

---

