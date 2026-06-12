---
title: "Change locale from comma to period as decimal separator"
date: 2009-06-10
forum: Desktop Environments
---

### Post by jakslev on 2009-06-10
Dear Everybody, 

I am having problems getting the correct Locale setting for my system. 
I am looking for an English language version of the Spanish locale - guess it would be called "en_ES". 

In my environment file I have added these lines:

sudo gedit /etc/environment

LANG=en_DK.UTF-8
LC_CTYPE=en_DK.UTF-8
LC_NUMERIC=es_ES.UTF-8
LC_TIME=en_DK.UTF-8
LC_COLLATE=en_DK.UTF-8
LC_MONETARY=es_ES.UTF-8
LC_MESSAGES=en_DK.UTF-8
LC_PAPER=es_ES.UTF-8
LC_NAME=en_DK.UTF-8
LC_ADDRESS=en_DK.UTF-8
LC_TELEPHONE=en_DK.UTF-8
LC_MEASUREMENT=en_DK.UTF-8
LC_IDENTIFICATION=en_DK.UTF-8

My aim is to get commas and periods used like in Denmark and Spain (where 10.000,57 euros is correct and not 10,000.57 euros) but with euro symbol as currency and langage in English. 

Any hints on what files I need to play with? 

Cheers, 

jakslev:popcorn:

---

### Post by laughlin.bill on 2010-07-06
Any response on this?  I'm having the same problem - need English as the primary language, but Spanish (Spain) style date (dd.mm.yyyy), currency(€), and decimal formats(#.###,00).

I had previously read a thread which instructed the creation of a custom local, which I did and called en_EU to be sort of a generic english-europe locale setting.  BIG MISTAKE!!! Now every program that relies on locales throws some sort of error message saying "Locale en_EU not found".  It's a pain in the a$$.

---

### Post by laughlin.bill on 2010-10-07
Bump!

---

