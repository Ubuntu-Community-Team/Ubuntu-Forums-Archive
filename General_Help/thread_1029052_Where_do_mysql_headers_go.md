---
title: "Where do mysql headers go?"
date: 2009-01-03
forum: General Help
---

### Post by isaidnosmoking on 2009-01-03
Hey guys,

I need to know the default location for the mysql header files when you do,

> sudo apt-get install mysql-client-5.0

sudo apt-get install mysql-server-5.0

Or does it come from a separate package?

I feel apt-get simply distributes the mysql installation across various folders instead of having a base dir something like /usr/local/mysql (which at least for me is more manageable).

Anyway, what i am trying to do is install php5 **manually** with mysql enabled *(I don't want this to be spreading across folders :()* !. However, i get the following error,


> configure: error: Cannot find MySQL header files under yes.
Note that the MySQL client library is not bundled anymore!

thanks,
PS: I am on the Ibex

---

### Post by thingy87654321 on 2009-01-03
i can tell you where your headers don't go............................................................................................................
in the lost and found, what where you guys thinking you sick people

---

### Post by isaidnosmoking on 2009-01-03
> **thingy87654321 said:**
> i can tell you where your headers don't go............................................................................................................
in the lost and found, what where you guys thinking you sick people

:???: umm well, happy new year to you. :popcorn: *wink* lol

Any help appreciated, Ty.

---

### Post by LateNiteTV on 2009-01-03
>  			 				configure: error: Cannot find MySQL header files under **yes**.
Note that the MySQL client library is not bundled anymore!

what is that "yes" about?

---

### Post by isaidnosmoking on 2009-01-03
> **LateNiteTV said:**
> what is that "yes" about?

im not sure, i do the following to configure php,

> ./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql

i think it should be --with-mysql=/path/to/mysql/headers

but im not sure *where* the mysql headers are.

---

### Post by cariboo on 2009-01-03
Why not just install php5 from the repositories and be done with it. It would be a lot easier. 

Have you tried opening Synaptic, then highlighting mysql-server-5.0, next click the properties-->installed files tab and see where the files are installed.

Jim

---

