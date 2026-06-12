---
title: "Amarok 1.4.2 and folder.jpg album covers"
date: 2006-08-27
forum: Desktop Environments
---

### Post by citizenkeith on 2006-08-27
I upgraded to Amarok 1.4.2 from 1.4.1. I built from source and everything works great... except the album covers are not loading.

I never used Amarok's "cover manager" because it stores the images in the hidden kde/amarok directory instead of with the music files. So I use albumart-qt to download the covers and save them in the album directory as folder.jpg. This worked perfect in Amarok 1.4.1. Not so in 1.4.2.

Anybody know if I can fix this, and if so, how?

---

### Post by sultanoswing on 2006-08-28
Same problem here...extremely annoying!! 

I use MySQL 5.0.22 for the db - I tried using SQLite, and deleting the old profiles, installing amarok from SVN, reinstalling MySQL (not tried version 4x though), installing the [Dapper package](http://www.imbrandon.com/2006/08/23/get-it-hot-amarok-142-released/), but all to no avail.

I eventually manually added all 1200 album covers using the cover manager, but here's hoping for a better fix than this!!!

---

### Post by muz1 on 2006-08-28
Thanks for letting me know this. I like my album art and will follow this and not upgrade till it is patched. Thanks for letting me know and I hope to find a solution to your problem.
Cheers
muz

---

### Post by sultanoswing on 2006-08-30
FYI, I've filed a bug report so you can keep track of this problem:

[http://bugs.kde.org/show_bug.cgi?id=133174](http://bugs.kde.org/show_bug.cgi?id=133174)

---

### Post by citizenkeith on 2006-09-05
I just build Amarok version 1.4.3 from source. The bug is fixed! :)

---

