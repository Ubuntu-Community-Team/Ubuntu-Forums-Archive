---
title: "dd/mm/yyyy date format"
date: 2012-06-01
forum: Desktop Environments
---

### Post by sonihbk on 2012-06-01
hi friends 

i am using ubuntu 11 & to run my some application i need

date format as dd/mm/yyyy

please help me how can i set it ???

---

### Post by steeldriver on 2012-06-01
are you asking how to specify the output format for the standard UNIX 'date' command? you can get the basics from the man (manual) page

```
man date
```unfortunately it doesn't give any examples, try something like

```
date "+%d/%m/%Y"
```

---

