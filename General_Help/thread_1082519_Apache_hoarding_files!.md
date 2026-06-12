---
title: "Apache hoarding files!"
date: 2009-02-27
forum: General Help
---

### Post by linuxisevolution on 2009-02-27
I have a server that I access via ssh and edit it's files with nfs. It serves the sites in my sig. Today I tried to do the news update on [http://98.219.177.90/apache2-default/linforum/forum/forum/book/site/news.html](http://98.219.177.90/apache2-default/linforum/forum/forum/book/site/news.html)

( site url is [www.wbaker.co.nr](www.wbaker.co.nr) )

So after editing the file, I saved it to where I had the server mounted ( /home/winrid/server/.....). I can reopen the file and the changes are saved.I can open the file on the server and it is there too, but when I go to the site the page remains as it was before I worked on it. I have the file linked to /var/www/apache2-default/linforum/forum/forum/book/site. I opened the file from there and I can see the file from ssh and it's contents correctly as they should ( it saved correctly ). But if I navigate in firefox to that directory the file is not saved!!!:confused: So, gedit and mousepad see the file correctly but Firefox does not?:confused::confused::confused: From my understanding apache or squid might be caching the file and not allowing me to change it. On that news page do you see the latest news title as "Back on task?"

If you do, then the problem is on my end. If you see "Chapter 16 of DoubleShear Finnished! -2009" then that is the old file... :( How do I make apache see the new file?

---

### Post by dcstar on 2009-02-28
> **linuxisevolution said:**
> I have a server that I access via ssh and edit it's files with nfs. It serves the sites in my sig. Today I tried to do the news update on [http://98.219.177.90/apache2-default/linforum/forum/forum/book/site/news.html](http://98.219.177.90/apache2-default/linforum/forum/forum/book/site/news.html)

( site url is [www.wbaker.co.nr](www.wbaker.co.nr) )

So after editing the file, I saved it to where I had the server mounted ( /home/winrid/server/.....). I can reopen the file and the changes are saved.I can open the file on the server and it is there too, but when I go to the site the page remains as it was before I worked on it. I have the file linked to /var/www/apache2-default/linforum/forum/forum/book/site. I opened the file from there and I can see the file from ssh and it's contents correctly as they should ( it saved correctly ). But if I navigate in firefox to that directory the file is not saved!!!:confused: So, gedit and mousepad see the file correctly but Firefox does not?:confused::confused::confused: From my understanding apache or squid might be caching the file and not allowing me to change it. **On that news page do you see the latest news title as "Back on task?"**

If you do, then the problem is on my end. If you see "Chapter 16 of DoubleShear Finnished! -2009" then that is the old file... :( How do I make apache see the new file?

a) Yes.
b) Clear the cache in YOUR browser - that is what you are seeing.

---

