---
title: "gd library PHP 5"
date: 2009-03-03
forum: General Help
---

### Post by BramWillemsen on 2009-03-03
Hi,

I am trying to get LAMP to work for several days now, but without success. This is the first time that I use linux, but i think that I am starting to get the hang of it. The problem is that I want to have mysqli support in php, so i cannot install the basic package. 

I already compiled and installed mysql 5.1 sucessfully. Before i can compile php i need to prepare a list of the required libraries according to my book. I want to include gd when i ./config with the --with-gd command. Does anyone have experience with this ?

All the posts that i saw suggested to download php5-gd, but that assumes that you installed the regular php package. But this package does not have mysqli so that's not really an option either. Can anyone please give me a hint about how to use compile php with gd support ? since ubuntu does not have gd i think

kind regards,

Bram

---

### Post by dgoosens on 2009-03-03
hi,

you will find all the info you need here...
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by BramWillemsen on 2009-03-03
but if i install it like that i won't have mysqli right..

---

### Post by Roanoke on 2009-03-03
You can just substitute php-mysql with php-mysqli afaik.

---

### Post by BramWillemsen on 2009-03-03
i guess i should try that then. installing zlib and libpng and such generates such a huge load of errors that i am nowhere close to installing gd. 

But since i already got mysql 5.1 installed (not default 5.0.6 of ubuntu), do i have to remove that one too to get 5.0.6 ? It took so long to compile and install mysql 5.1 that i would hate to remove it again. Or will the packages that i download automatically recognise it ?

And if i have to remove 5.1, can i just delete the directory since i compiled / installed it there without the synaptic package manager?

Sorry for all the questions but i don't really understand the details yet.

Bram

---

### Post by BramWillemsen on 2009-03-03
So basically, will my compiled/installed mysql 5.1 work with the php5/apache2 packages that can be automatically installed?

---

### Post by BramWillemsen on 2009-03-03
bump

---

### Post by BramWillemsen on 2009-03-03
bump

---

### Post by Roanoke on 2009-03-03
It would be nice if you didn't bump every hour. We do this as volunteers, and it would be nice if you were a bit more patient.
Why don't you just use apt-get to get all your packages instead of compiling?

---

