---
title: "Thumbnailing of comic books fails in lucid"
date: 2010-04-19
forum: Desktop Environments
---

### Post by __init__ on 2010-04-19
There is a following convention: tar/zip/rar archive renamed to cbt/cbr/cbz is recognized by some application as a comic book file, so file managers can open it using corresponding viewers, which treat sequence of images inside as pages of a book. And nautilus used to recognize cbt files, making thumbnails from the first image in such renamed archive back in karmic. It still recognizes such file as "Comic Book Archive" after upgrade to lucid but fails to thumbnail it now. It tries to do that though, showing icon with the clock for a moment, but almost instantly fails, printing "Error loading document: File type Tar archive (application/x-tar) is not supported" to the console. When I am trying to open cbt file in evince (which is responsible for making document thumbs in gnome afaik) it displays exactly the same error message. Cbt files itself are completely valid and can be opened easily with Comix for example. Thumbs created in karmic are still displaying fine as well.

Sorry for my clumsy english. :)

---

### Post by __init__ on 2010-04-20
Bump. Any thoughts how to fix it?

---

### Post by tyle on 2010-04-22
> **__init__ said:**
> Bump. Any thoughts how to fix it?

Indeed annoying. Reading + thumbnailing of cbt files worked fine under Ubuntu 9.10 with a compiled evince 2.29.5, but now that I updated to lucid, the cbt files will no longer be opened nor thumbnailed by evince.

I solved this by compiling evince 2.30 from source. After having done this reading and thumbnailing works fine in Ubuntu 10.04 as well. This looks like an Ubuntu-specific problem as compiling the same version of evince from source works without problems.

Hope this helps.

Edit: Filed a bug report for this problem: [http://bugs.launchpad.net/ubuntu/+source/evince/+bug/568663](http://bugs.launchpad.net/ubuntu/+source/evince/+bug/568663)

---

### Post by skeptikos on 2010-09-29
I was able to solve this by installing rar and unrar.

Now evince as well as comix can open my cbr files.

Hope that helps.

---

