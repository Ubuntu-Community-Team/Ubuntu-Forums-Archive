---
title: "Applying Patch"
date: 2011-07-06
forum: Desktop Environments
---

### Post by silveringking on 2011-07-06
Hello I am having a problem with empathy on ubuntu 11.04, you see I used ubuntu before as a server but now I am using it as a desktop too, windows is a pain in the ***, I can tell with 2 days of ubuntu that this is so much easier...

Anyway...

I am having a problem with empathy, it doesn't show my nick or my personal message on msn... Only my email!

So I found this:

[https://bugs.freedesktop.org/show_bug.cgi?id=13124](https://bugs.freedesktop.org/show_bug.cgi?id=13124)

and I made the patch anexed!

Then I did this on the terminal:

> diff -ruN 0001-aliasing-use-new-public_set_alias.patch.old 0001-aliasing-use-new-public_set_alias.patch.new > 0001-aliasing-use-new-public_set_alias.patch.diff

Sorry for being such a noob but I don't even know how to setup the path for diff...

So how do I find it correctly? And how I setup the path? If I open nautilus it seems to be that the search on root is rather slow...

Thank you!

---

### Post by psusi on 2011-07-06
diff generates a patch file, you apply it with the patch program.

Typically patch -p1 < 0001-aliasing-use-new-public_set_alias.patch

---

### Post by silveringking on 2011-07-06
Hello I am trying to do:

sudo patch -p1 < /home/carlos/Área de Trabalho/0001-aliasing-use-new-public_set_alias.patch

and

sudo patch -p1 < 0001-aliasing-use-new-public_set_alias.patchbash: 0001-aliasing-use-new-public_set_alias.patch

and the bash retrieves to me that the file or the directory is inexistent! Maybe this fix is outdated?

---

### Post by psusi on 2011-07-07
Are you in the directory of the source code of the program it is supposed to patch?

---

