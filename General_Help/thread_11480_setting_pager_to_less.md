---
title: "setting pager to less"
date: 2005-01-17
forum: General Help
---

### Post by wastrel on 2005-01-17
I have my pager set to "/usr/bin/less" in my PAGER bash environment variable and in /etc/alternatives.  
When I tab-complete and get a long list, however, "more" is used as the pager.

What do I do to fix this?

---

### Post by mendicant on 2005-01-17
I think bash is actually using a built in pager for readline.  See the man page for bash or readline:

       page-completions (On)
              If set to On, readline uses an internal more&#8208;like pager to  dis&#8208;
              play a screenful of possible completions at a time.

---

### Post by wastrel on 2005-03-02
[QUOTE=mendicant]I think bash is actually using a built in pager for readline.  See the man page for bash or readline:

       page-completions (On)
              If set to On, readline uses an internal more&#8208;like pager to  dis&#8208;
              play a screenful of possible completions at a time.[/QUOTE]

Thanks you're correct.  I turned this off by putting 

page-completions off 

in ~/.inputrc, but now bash doesn't use a pager at all.

Does anyone know how to make bash call less to page through long tab-complete output?  
I'm sure my previous linux systems did this....

---

