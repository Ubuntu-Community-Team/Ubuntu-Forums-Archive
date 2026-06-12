---
title: "FireFox &quot;saving as&quot;"
date: 2006-05-30
forum: Desktop Environments
---

### Post by Kmujo on 2006-05-30
anyone else having trouble when trying to save a file manually from php content that it always receive & download the "download.php" file? i'm always using wget to retrieve files from php sites.

---

### Post by FredB on 2006-05-30
Smells like some sites are sending bad mimetypes to firefox, because IE don't care a shit about type and save files on extensions.

---

### Post by disturbed1 on 2006-05-30
gnomelook.org does this all the time.

let's say I want to download a picture, and firefox is wanting to call it pic.php, i just rename it to pic.png and all is well.

---

### Post by mejy on 2006-05-30
[QUOTE=disturbed1]gnomelook.org does this all the time.

let's say I want to download a picture, and firefox is wanting to call it pic.php, i just rename it to pic.png and all is well.[/QUOTE]
That annoys the hell out of me - it means instead of dragging themes into the theme manager you have to download them to a folder before being able to drag them in.  Not alot extra, but when you have to keep doing it gets really tedious.

---

### Post by disturbed1 on 2006-05-30
Every theme I've tried to download have all d/l as the correct tar files, it's only with some pictures that I get this problem.

---

### Post by aysiu on 2006-05-30
Is it a Javascript issue, maybe?

I think to diagnose the problem, you should post a link or two to sites that are not working for you.

If they work for others, then you have a problem. If they don't work for others, the site isn't constructed well.

---

### Post by disturbed1 on 2006-05-30
[quote=aysiu]Is it a Javascript issue, maybe?

I think to diagnose the problem, you should post a link or two to sites that are not working for you.

If they work for others, then you have a problem. If they don't work for others, the site isn't constructed well.[/quote]

[http://www.gnome-look.org/content/show.php?content=39999](http://www.gnome-look.org/content/show.php?content=39999)

click on download, loads up the picture, right click on picutre choose save as - ***download.php***

---

### Post by dejitarob on 2006-05-30
Goto File, Save Page As.

---

### Post by TrinitronX on 2006-05-30
Hmm.... It seems to only happen with pages that use a .php page to serve pictures.  The link to the picture goes to a download.php page, passing a parameter that tells it what picture to show.  Then, I think that page redirects to the actual image, but firefox somehow still thinks the url is http://.....blahblah..../download.php

Probably a bug in firefox that can be reported :P

---

### Post by denzilla on 2006-05-30
Yea, this happens too me on both kde-look and gnome-look. I just change the name and use jpg. Not sure what the actual file type is.

---

### Post by nu2this on 2006-06-14
I'm not sure if this is what ur after but try using the Fx extension Scrapbook 1.0.6 I just tried the page listed & it comes out fine.

---

