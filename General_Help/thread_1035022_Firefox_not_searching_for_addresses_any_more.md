---
title: "Firefox not searching for addresses any more"
date: 2009-01-09
forum: General Help
---

### Post by Benchamoneh on 2009-01-09
Hi all,
When I used Firefox previously - on any OS - and entered a word into the address bar, it always used to search for the most relevant site and take me there. For example when I entered 'bbc' into the address bar and hit enter, Firefox would search and then direct me to [http://www.bbc.co.uk](http://www.bbc.co.uk), however now i just get [http://bbc/](http://bbc/) which is obviously not found. Why doesn't Firefox perform this search any more? As far as I can I've made no changes to it's configuration (there may have been some updates applied from the update manager), and I've tried removing my .mozilla folder from home to see if a new config would make a difference but with no luck.

I'm stumped, has anyone encountered this before or know of a resolution? :confused:

---

### Post by blazemore on 2009-01-09
Go to about:config and enter in the Filter box: keyword.URL 
Rght-click on the line, click on modify, and change to: 
```
http://www.google.com/search?btnI=I%27m ... e=UTF-8&q=
```

---

### Post by Benchamoneh on 2009-01-09
Just gave that a try but it's not made any difference. My keyword.URL value was originally set to:```
http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=
```Additionally I've just noticed that Firefox will still search for an address when multiple words are entered but just not with single words. For example 'bbc uk' gets me to the bbc website but 'bbc' alone does not work.

Thanks for your help. Anything else I could try?

---

