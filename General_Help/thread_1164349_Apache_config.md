---
title: "Apache config????"
date: 2009-05-19
forum: General Help
---

### Post by caperpc on 2009-05-19
Hi apache guruz...i need a little help plz

here is the sitch
user goes to abc.com and hits the home page
site has 3-4 whatever subpages/links off of that main/home page.
can i lock keep users at the home page without disabling all my links on that page or moving my other pages elsewhere. 

I basically want ppl to visit my home page and no more...not be able to navigate through the rest of my site.

sorry if i didnt articulate my issue.


thanks a million

---

### Post by caperpc on 2009-05-19
sorry i didnt really mean abc.com...meant exampleblahblah.com..in other words my website.

thx

---

### Post by ActiveFrost on 2009-05-19
.htaccess
```
Redirect /restricted.html http://www.google.com 
```

Sure, you don't want to redirect to google - that was just an example ( instead of google, use your domain name ).

---

