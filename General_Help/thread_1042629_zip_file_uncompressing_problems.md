---
title: "zip file uncompressing problems"
date: 2009-01-17
forum: General Help
---

### Post by sefs on 2009-01-17
Hi all,

I downloaded the windows 7 beta 1 vm from [http://www.tuxdistro.com/](http://www.tuxdistro.com/)

However when I tried to unzip it, I get an error "invalid compressed data to inflate".

The archive is not however corrupted as I can uncompress the same with 7-zip in windows xp.

How can I bring ubuntu up to scratch to do the same.

Thanks.

---

### Post by dcstar on 2009-01-17
> **sefs said:**
> Hi all,

I downloaded the windows 7 beta 1 vm from [http://www.tuxdistro.com/](http://www.tuxdistro.com/)

However when I tried to unzip it, I get an error "invalid compressed data to inflate".

The archive is not however corrupted as I can uncompress the same with 7-zip in windows xp.

How can I bring ubuntu up to scratch to do the same.

Thanks.

Have you installed any p7zip packages?

---

### Post by bumanie on 2009-01-17
You should install p7zip as suggested above. > sudo apt-get install p7zip-fullThen anything you need to unzip should only require you to right click on it and choose extract here. If you want to be able to unzip .rar files > sudo apt-get install rar unrar

---

### Post by sefs on 2009-01-17
We are cooking with gas again.  Thank you and thank you.  You really know what's what.

---

