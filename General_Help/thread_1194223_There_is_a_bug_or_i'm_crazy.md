---
title: "There is a bug or i'm crazy"
date: 2009-06-22
forum: General Help
---

### Post by scanmarc on 2009-06-22
Hi everybody

Last night i was scriptting. Whats my surprise when i test it. I put the code below:

#!/bin/bash

#VARIABLES

date
eval `date "+day=%d; month=%m; year=%G"`
echo $year

Ok? when i put the date to year 2009 in my system the script says:

dj gen  1 17:37:25 CET 2009
2009
:P

Thats ok! well, when i change the year to 2010 thats the result:

dv gen  1 17:38:23 CET 2010
2009
:confused:

Here there is an error, well can be a problem, the next what i do was change de year to 2011

ds gen  1 17:39:35 CET 2011
2010

and...

dg gen  1 17:40:36 CET 2012
2011

:popcorn:
Can any one explain me what hapens?

---

