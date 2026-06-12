---
title: "Loki istaller(.run) problems"
date: 2006-01-20
forum: Gaming &amp; Leisure
---

### Post by dube.on.bass on 2006-01-20
when i try and run my .run files for CoD i get a error message stating that i need libgtk1.2, but from what i can see it is not an available package. what is the problem i am following the proper procedure to install hese files, yet i keep getting this error.HELP ME!

ps..i ahve installed libgtk1.2-doc, but it has not fied the problem.

---

### Post by stoffe on 2006-01-20
libgtk1.2 is most definitely available as a package, otherwise there is something very strange going on. :)

If you do have it installed and it doesn't work, maybe you could paste the error message for people to see?

---

### Post by dube.on.bass on 2006-01-20
for sure...gotta wait till i arrive at my homely confine though...
ill paste them
but theyre diffrent every time, alyts new and ascending numbers...and...i used he code sudo apt-et install libgtk1.2 , but it didnt work, told me there was no pakcgae found...

---

### Post by bartbes on 2006-01-20
I used:
apt-cache search libgtk1.2
and what I saw is that the package is called:
libgtk1.2-common
to get it do:
sudo apt-get install libgtk1.2**-common**
(don't really make -common bold, it's to make the change clearer..)

---

