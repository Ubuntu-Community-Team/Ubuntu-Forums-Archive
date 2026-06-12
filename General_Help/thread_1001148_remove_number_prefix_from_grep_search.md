---
title: "remove number prefix from grep search"
date: 2008-12-03
forum: General Help
---

### Post by meg23 on 2008-12-03
When I run this command

```
elinks -dump www.google.com/news | grep 'tech'
```

I get this output in a text file:

 222. [http://www.redorbit.com/news/technology/1603883/us_computer_shipments_expected_to_fall_next_year/](http://www.redorbit.com/news/technology/1603883/us_computer_shipments_expected_to_fall_next_year/)
 223. [http://www.reuters.com/article/technologyNews/idUSTRE4B24YO20081203](http://www.reuters.com/article/technologyNews/idUSTRE4B24YO20081203)
 235. [http://www.telegraph.co.uk/scienceandtechnology/technology/microsoft/3545778/Xbox-360-outsold-PS3-on-Black-Friday-claim-Microsoft.html](http://www.telegraph.co.uk/scienceandtechnology/technology/microsoft/3545778/Xbox-360-outsold-PS3-on-Black-Friday-claim-Microsoft.html)
 236. [http://www.telegraph.co.uk/scienceandtechnology/technology/microsoft/3545778/Xbox-360-outsold-PS3-on-Black-Friday-claim-Microsoft.html](http://www.telegraph.co.uk/scienceandtechnology/technology/microsoft/3545778/Xbox-360-outsold-PS3-on-Black-Friday-claim-Microsoft.html)

Is there anyway to suppress the number prefix from being inserted or is there any other utility can produce the matches with the number. I am trying to parse these urls into another program.

---

### Post by fragos on 2008-12-03
Elinks put those there. Look at "elinks --help".

---

### Post by firsttimeuser on 2008-12-03
not quite sure what you want, are you tyring to get rid of the first column?

---

### Post by meg23 on 2008-12-03
When I run it with the --no-numbering flag, I get the output without the numbers but the period sticks around.    
   
   . [http://www.nytimes.com/2008/12/03/technology/start-ups/03hawaii.html?em](http://www.nytimes.com/2008/12/03/technology/start-ups/03hawaii.html?em)
   . [http://www.nytimes.com/2008/12/03/technology/start-ups/03hawaii.html?em](http://www.nytimes.com/2008/12/03/technology/start-ups/03hawaii.html?em)
   . [http://www.dailytech.com/Hawaii+Endorses+Plan+for+Electric+Cars+/article13578.htm](http://www.dailytech.com/Hawaii+Endorses+Plan+for+Electric+Cars+/article13578.htm)
   . [http://www.nytimes.com/2008/12/03/technology/start-ups/03hawaii.html?em](http://www.nytimes.com/2008/12/03/technology/start-ups/03hawaii.html?em)

How can I get rid of the period?

---

### Post by meg23 on 2008-12-03
I am trying to get rid of the line numbers ie "222." in the output

---

### Post by firsttimeuser on 2008-12-03
> **meg23 said:**
> I am trying to get rid of the line numbers ie "222." in the output

simple, just put

elinks -dump [www.google.com/news](www.google.com/news) | grep 'tech' | awk '{print $2}'

---

### Post by meg23 on 2008-12-03
that did it thanks!

---

