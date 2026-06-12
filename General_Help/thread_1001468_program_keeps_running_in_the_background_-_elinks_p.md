---
title: "program keeps running in the background - elinks problems"
date: 2008-12-04
forum: General Help
---

### Post by linorics on 2008-12-04
I have Ubuntu server 8.04. I'm using Elinks to save a website as a text file. 

elinks -dump [www.foobar.com](www.foobar.com) > webpage.txt

but every time I do this it makes elinks run in the background, and saves nothing to the text file. 

elinks -dump [www.foobar.com](www.foobar.com) > webpage.txt
[2] 15991

Any idea's what is wrong? It worked fine when I was testing it on cygwin. But when i did it on ubuntu it didn't work:-(

---

### Post by weemadarthur on 2008-12-04
> **linorics said:**
> I have Ubuntu server 8.04. I'm using Elinks to save a website as a text file. 

elinks -dump [www.foobar.com]("http://www.foobar.com") > webpage.txt

but every time I do this it makes elinks run in the background, and saves nothing to the text file. 

elinks -dump [www.foobar.com]("http://www.foobar.com") > webpage.txt
[2] 15991

Any idea's what is wrong? It worked fine when I was testing it on cygwin. But when i did it on ubuntu it didn't work:-(

Are there any ampersands (&) in the URL? Try 
elinks -dump "www.foobar.com" > webpage.txt  (Note the quotation marks).

---

### Post by linorics on 2008-12-04
Yup that was the case. I guessed that right after I posted it. But I got so busy testing it that I forgot to to replay back here.

But that was the problem. So thanks!

---

