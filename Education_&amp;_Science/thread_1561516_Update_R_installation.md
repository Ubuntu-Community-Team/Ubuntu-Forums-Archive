---
title: "Update R installation"
date: 2010-08-26
forum: Education &amp; Science
---

### Post by bryncoles on 2010-08-26
Greetings friends! I am trying to update my R installation. I boot R with root privileges in the usual way 

```
sudo R
```

but after typing 

```
update.packages(,dep=T)
```

it tells me

> Warning: unable to access index for repository [http://www.freestatistics.org/cran/src/contrib](http://www.freestatistics.org/cran/src/contrib)
Warning message:
In open.connection(con, "r") : cannot open: HTTP status was '409 Conflict'

Any idea what I'm doing wrong?

---

### Post by akniss on 2010-08-26
After you type 'update.packages()' are you presented with a list of repositories to choose from?  Perhaps try choosing another repo and see if that fixes the problem?

---

### Post by bryncoles on 2010-08-26
Good try akniss, But alas, I get the same problem when trying different servers. Boo!

---

### Post by gunksta on 2010-08-26
This is what I like to call a "shot in the dark".

Did you install the packages as root? Do you have to? I usually install my R packages in my home folder in ~/R/ which is separated into x86/ and x64/ for different computers. I sync all of this globally with UbuntuOne.

Thus -- why install / update them as root?

How many packages have you got installed manually?

I find the deps=TRUE to be problematic at times because I have many packages I install via the Ubuntu repos and many I install manually. I wind up just keeping track of all the deps by hand of the 5-8 packages I install manually so I can "update" them by reinstalling manually.

---

