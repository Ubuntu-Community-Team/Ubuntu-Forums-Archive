---
title: "encoding in amaroK 1.4"
date: 2006-06-08
forum: Desktop Environments
---

### Post by D!mon on 2006-06-08
It was possible to select encoding for IDv tags in the amaroK 1.3.x;
where is the same option in 1.4??

---

### Post by nekr0z on 2006-06-10
Same problem here: I used to have ID3v1 tags set up in cp1251 when I was using amarok 1.3.x, now it's impossible, they all seem to be default to UTF-8. 

Even more of a problem is: as I edit some tag, using non-latin characters, it doesn't write ID3v2 tags, but spoils ID3v1 instead. ID3v1 tags are not unicode by origin, so as I open the same file again the tags are spoiled to some mess (although I just have edited them manually!) 

What the heck happened to the world's best player???

---

### Post by nir78 on 2006-07-10
Same problem here also! anybody found something ??

Nir

---

### Post by grray on 2006-08-14
If you have problems with cp1251 encoding

1. Add to the sources.list: "deb [http://rusxmms.sourceforge.net/ubuntu/rusxmms](http://rusxmms.sourceforge.net/ubuntu/rusxmms) dapper main"
2. apt-get update
3. sudo apt-get install libtag1c2a
4. rescan collection in amarok
5. all fine

---

### Post by nekr0z on 2006-08-15
Seems to be a solution, but will it not spoil all my files now, as I already got half of them tags converted to UTF-8?

---

### Post by D!mon on 2007-03-17
how can I patch libtag if I have Edgy x64?
As a workaround, the great tool is: [http://sourceforge.net/projects/tag2utf](http://sourceforge.net/projects/tag2utf)
If your music collection is all in one folder it will do the work, but plugin/lib for amarok will be more great of course

---

### Post by idanool on 2007-08-18
Hello!

I have the same problem, but with hebrew tags, so the suggested hack is not good for me.
in amarok 1.3.x I used encoding ISO-8859-8-I.
is there a solution for amarok 1.4.x ?

thanks

---

### Post by chacham23 on 2007-09-28
> **idanool said:**
> Hello!

I have the same problem, but with hebrew tags, so the suggested hack is not good for me.
in amarok 1.3.x I used encoding ISO-8859-8-I.
is there a solution for amarok 1.4.x ?

thanks

same here some one??

---

### Post by klaasvanschelven on 2007-10-03
bump

---

