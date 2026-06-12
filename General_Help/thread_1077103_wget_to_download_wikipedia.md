---
title: "wget to download wikipedia"
date: 2009-02-22
forum: General Help
---

### Post by 7raTEYdCql on 2009-02-22
As absurd as it may sound. Can i download Wikipedia, using wget??

---

### Post by mcduck on 2009-02-22
Probably you can, but most likely you shouldn't. It would cause _really_ heavy load on Wikipedia's servers, and I'm quite sure you wouldn't have nearly enough hard disks space to store everything anyway. Not to forget that it would take a *lot* of time, even with a high-speed connection.

Last time I've seen somebody trying to download a fairly large web site (nothing even close to size of Wikipedia) to his computer both web server and his own computer crashed under the load and because of running out of memory and disk space. He was lucky and the web site's admins didn't sue him for it (as he clearly had no idea how large such web sites actually are).

---

### Post by nithu.ji on 2009-02-22
but, y to download the enire wikipedia? For,it, u may get afull book of encyclopedia na?;)
[www.itblogs.in](www.itblogs.in)
irene

---

### Post by 7raTEYdCql on 2009-02-22
Thanks mcduck, that was fairly shocking. But it was nice to know.

---

### Post by dcstar on 2009-02-22
> **mcduck said:**
> Probably you can, but most likely you shouldn't. It would cause _really_ heavy load on Wikipedia's servers, and I'm quite sure you wouldn't have nearly enough hard disks space to store everything anyway. Not to forget that it would take a *lot* of time, even with a high-speed connection.
.........

This question reminds me of the old Dilbert cartoon where his pointy-haired boss tells him to back up "The Internet".......   :D

---

### Post by snova on 2009-02-22
[http://en.wikipedia.org/wiki/Wikipedia_database](http://en.wikipedia.org/wiki/Wikipedia_database)

---

### Post by mb_webguy on 2009-02-22
> **dcstar said:**
> This question reminds me of the old Dilbert cartoon where his pointy-haired boss tells him to back up "The Internet".......   :D

Which makes you wonder how the [Internet Archive]("http://www.archive.org/index.php") manages to do exactly that.  2 PetaBytes doesn't seem nearly enough...

---

### Post by Vadi on 2009-02-22
Wikipedia offers downloadable versions already

---

### Post by paddysteed on 2009-06-19
> **i.mehrzad said:**
> As absurd as it may sound. Can i download Wikipedia, using wget??
Believe me. it is abserd. Well you could crawl it using
```
wget --random-wait -r -p -e robots=off -U mozilla http://en.wikipedia.org/wiki/Main_Page
```
which is the answer to your question. But i warn you that it will be around 2 Terra bytes

---

### Post by kostkon on 2009-06-19
Check the [Wikipedia on DVD]("http://www.wikipediaondvd.com/site.php"), if you like.

---

### Post by SerenityKill3r on 2009-06-19
You can download Wikipedia, minus the images.

The file is 14GB, and just contains the articles in HTML format.

---

### Post by tetron on 2010-01-29
Although, probably too late for the current poster, I have just downloaded the latest wikipedia downlaod.
 
Link From:
 
[http://en.wikipedia.org/wiki/Wikipedia_database](http://en.wikipedia.org/wiki/Wikipedia_database)
 
Latest articles was a 5.39 GB downlaod
 
wget works for downloading the file but other methods may not
~10 hours on university connection
 
There are some issues to be bourne in mind:
 
1st that the file is bigger than 4GB which is the limit for IE 8 possibly firefox too despite published quotes elsewhere!
 
Internet explorer 8 has 4GB temp file limit for example, but you don't find this out until you have downloaded 4GB.
 
If you are transferring the file ensure that you can use a non FAT32 file system as otherwise the file is too big.
 
 
A single 24GB file was extracted from the xml.gz2 I have yet to check the data but if I find a problem I hope to repost.
 
As I need this on a windows XP computer I was using UltimateZip which could have problems extracting but hopefully all is OK.
 
Hope this is of help to someone,
 
David

---

### Post by Syock on 2011-04-12
This is a very old thread, and I'm summoning it from the graves.

One vital rationale to be using wget instead of downloading whole database is: you may end up using only at most 10% of the the downloaded data. That amounts to 500MB for a 5GB db, but the the rest of 4.5GB is wasted. Why would I want to download that? So if I get to wget it, I can select articles that I want. If a link I clicked on is not available locally, then I only have to resume wget to retrieve it and add to the collection.

So far, I have not found any offline tools specialized for wikipedia that does this. Kiwix, Wikitaxi, they all need a prebuilt db.

I'll try to find out how to use wget, and update here accordingly.

---

