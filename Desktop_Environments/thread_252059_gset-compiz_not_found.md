---
title: "gset-compiz not found"
date: 2006-09-06
forum: Desktop Environments
---

### Post by baosheng on 2006-09-06
it was funny.
I have add the responsitories
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
   deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main


but when I executed 
sudo apt-get install gset-compiz
i got the answer saying that gset-compiz not found.

it should work, according to my experience of using xgl/compiz.

Can anyone tell me what is the problem?

---

### Post by Johan! on 2006-09-06
gset-compiz is replaced by csm.

Read the compiz.net forums for more information :)

Also, you need to start compiz with compiz-start

---

### Post by baosheng on 2006-09-06
> **Johan! said:**
> 

Also, you need to start compiz with compiz-start

Do I need to make any configuration to start compiz by compiz-start?

---

### Post by Uncle Spellbinder on 2006-09-07
Just add */usr/bin/compiz-start* to your startup programs

---

