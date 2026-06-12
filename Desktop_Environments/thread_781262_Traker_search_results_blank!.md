---
title: "Traker search results blank!"
date: 2008-05-04
forum: Desktop Environments
---

### Post by nivosh on 2008-05-04
hello.
on ubuntu 8.04 fresh install.
using tracker it presents the results of the search in the categories on the left but trying to see the results leaves me with a blank screen.

no matter which category i choose the results stayes blank.

any idea how to solve? tracker isnt much use that way...

---

### Post by NightwishFan on 2008-05-04
Simple in Searching and Indexing properties check enable indexing and then wait a bit and it should work. If still no, log out and back in. I am quite sure that should do it.

---

### Post by nivosh on 2008-05-04
thanks for the quick reply! great forum great peaple!

about your advise, the problem happens After i indexed my files.

the categories on the left show search results for example:

Documents (120 results)

but when i press that category, instead of getting the results it displays nothing...

---

### Post by NightwishFan on 2008-05-04
Ah.. I never had that problem myself. I am not on Gnome right now so I cannot tweak around the options myself. Hopefully your thread gets some attention though. Quite possibly there is a simple solution.

---

### Post by Deeta on 2008-05-04
I can confirm this problem. Indexing was switched on by default after I upgraded to hardy (on the release day, so it should have had time to index) and I tried to use tracker several times but it never worked and only offered the categories with result numbers but which in turn upon opening resulted in blank results.

---

### Post by nivosh on 2008-05-04
do you think we should post it as a bug?

can anyone else confirm this problem?

---

### Post by Deeta on 2008-05-04
Well given that Ubuntu's mission is more or less to make Ubuntu accessible to people without excessive computer background this would certainly qualify as a bug. Not a showstopper one, but a bug nevertheless.

I have not reported any bugs as of yet though, so if you report one and give me the link here then I can chime in in the bug report thread. (think they are on launchpad or so) <--- cluelessness showing ;-)

---

### Post by nivosh on 2008-05-04
Looks someone beat us to it...:)

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/163544](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/163544)

most of them says that re-indexing and restarting trackerd did the trick.

i'm going to check it tonight.

---

### Post by Deeta on 2008-05-04
Yeah Re-indexing seems to have improved my results too.
Not sure if it is perfect yet, but it is ok :)

Thanks for locating the launchpad thread!

---

