---
title: "How to refresh thumbnails?"
date: 2010-11-26
forum: Desktop Environments
---

### Post by Buecai9ahd on 2010-11-26
Recently due to partitioning and a power failure Ive had to now copy all my backup movies etc. back onto ubuntu as they are corrupted. 
At the moment the thumbnails of the movies are the generic orange media image and when I replace it with the backup movie, across to ubuntu and refresh the browser, the thumbnail stays the same i.e. it doesn't show a small screen cap of the movie.
Is there a way to 'refresh' them properly as it were?
I am running Ubuntu 10.10.
Thanks for any help/ideas.
Sam

---

### Post by tom4everitt on 2010-11-27
The thumbnails are stored in 

~/.thumbnails

Removing that directory should force them to be regenerated. Hopefully that will solve your problem.

---

### Post by Buecai9ahd on 2010-11-27
That worked great, thanks!

---

