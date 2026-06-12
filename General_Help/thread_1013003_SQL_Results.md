---
title: "SQL Results"
date: 2008-12-16
forum: General Help
---

### Post by CrusaderAD on 2008-12-16
I have a fairly simple sql statement like this:

```

sql = " SELECT TOP 3 name, description, image, Discontinue_YN, productid " & _
          " FROM product " & _
          " WHERE Discontinue_YN = 'N' " & _
          " AND category = " & RS4("category")
```

It returns 3 results. What I need to do is assign a variable to each result to I can refer to them later. Apparently I need to loop the query. How do I assign the variables to each result?

---

### Post by kanikilu on 2008-12-16
I'm not really sure that this is the appropriate venue for this, but...

Are you wanting to assign the variables in sql ([http://dev.mysql.com/doc/refman/5.1/en/user-variables.html)?](http://dev.mysql.com/doc/refman/5.1/en/user-variables.html)?) Or are you wanting to process the results in another language (e.g. PHP)?

If you're wanting to do it in SQL, I can't really help other than pointing you to the manual...my experience with MySQL has been pretty basic.

If you're wanting to use another language to process the results, it would help to first know what languague.

PHP seems to still be a popular choice these days, if that's the case check out the [manual]("http://us.php.net/manual/en/ref.mysql.php") first (obviously), and if you can't find what you're looking for or no one else can help you here, you might want to try a more appropriate forum like the [phpfreaks.com forums]("http://www.phpfreaks.com/forums/index.php").

---

### Post by CrusaderAD on 2008-12-16
Ok... I'll take a look at the link. It's actually a Visual Basic 6 program I'm putting together. I figure it was more of a SQL question, but then again, maybe not. I just like posting in here cause I am mostly a Ubuntu user and I get great help in these forums!

---

### Post by CrusaderAD on 2008-12-16
I there anyway to run this statement:

sql = " SELECT TOP 3 name, description, image, Discontinue_YN, productid
      " FROM product " & _
      " WHERE Discontinue_YN = 'N' " & _
      " AND category = " & RS4("category")

But skip the first row? Something like SELECT TOP 3 SKIP 1? I tried it but I get a syntax error.

---

