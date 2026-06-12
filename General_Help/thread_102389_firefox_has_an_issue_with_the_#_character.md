---
title: "firefox has an issue with the # character"
date: 2005-12-11
forum: General Help
---

### Post by Trab on 2005-12-11
yeah, it sucks, but firefox wont load things that have the # character in the url....

on the unbutu guide page [http://ubuntuguide.org](http://ubuntuguide.org) if i click on one of the topics, it works fine, but if in plesk i click on the sessions manager it doesnt work... or on froogle.com if i try to add somethign to my shopping list it also doesnt work...
an example of hte urls that dont work:
[https://MYPLESKSITE:8443/left.php3#](https://MYPLESKSITE:8443/left.php3#)

thanks
-Trab

---

### Post by Sp@z on 2005-12-12
I had to bump this because I noticed the same thing, anytime I load a websight with graphics rotating, spinning flashing or with the # firefox actlike a butthead and I have to restart my system the hard way by turning off the power. I cannot swaer it is because of the # sign but it is in all the pages I have issues with. I am not 100% sold on FIrefox and will use a different one,but sure would like to see this issue resolved.

Thanx.

---

### Post by Trab on 2005-12-12
ok, weird, when i ran firefox with the sudo command, it worked just fine.
example:
[http://froogle.google.com/froogle?q=mitsubishi+spyder+eclipse+green&btnG=Search+Froogle&lmode=unknown#](http://froogle.google.com/froogle?q=mitsubishi+spyder+eclipse+green&btnG=Search+Froogle&lmode=unknown#)
but if i run it in regular firefox.... no dice....

i think it has something to do with one of my tab extension plugins...
i might get rid of hte plugin anyways, its had other issues....

ill try, and let you know how it goes...
latz
-Trab

EDIT: with that extention gone, it works like a charm!
latz!

---

### Post by Sp@z on 2005-12-12
I don't have that ext.I am guessing I am S.O.L since this thread isn't hopping around :( Thanx anayways..................

---

### Post by Trab on 2005-12-12
well, just to isolate the problem, try running sudo firefox from the command line, and see if ur # problem goes away... if so, it should be easily fixable, just find out wats running on ur regular firefox that isnt on ur root one...
just a test :-D

good luck...

Ps. also see if firefox gives any errors when u run it regularly on a terminal, that might be a clue....

---

