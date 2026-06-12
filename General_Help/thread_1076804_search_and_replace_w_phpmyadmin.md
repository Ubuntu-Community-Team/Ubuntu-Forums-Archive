---
title: "search and replace w phpmyadmin"
date: 2009-02-21
forum: General Help
---

### Post by buzzmandt on 2009-02-21
I couldn't find a proper place to post this so I'll put it here knowing it might be moved (sorry)....

I have a database with about 100 tables in it.
I need to search each table for the field "userid"
then match any userid that is "8" and change it to "1" in the whole database.

I found this ```
     UPDATE tablename SET field = replace(field, &#8220;SearchString&#8221;, &#8220;ReplaceString&#8221;);
``` but it's only good for one table at a time.  

anyone know the code for this on the whole database instead of one table at a time?

thanks.

oh yeah, I also am using phpmyadmin for the sql commands

---

