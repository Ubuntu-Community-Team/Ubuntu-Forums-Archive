---
title: "Conky displays boxes at the end of a text file"
date: 2009-04-30
forum: General Help
---

### Post by Reactor5 on 2009-04-30
I have a text file from tracks downloaded with with wget script and displayed using cat in a conky configuration.  The only problem is that there's a box at the end of every line. I'd like to get rid of it, but how?

---

### Post by 987poiuytrewq on 2009-05-01
Instead of using 
```
 cat foo 
```
where foo is your file try using
```
 cat foo | sed 's/£//g' 
```
But replace the £ sign with a box , copied from the output (I can't post one in the code snippet because it doesn't show up on the forum). I'm not sure if that will work, but it should delete all the boxes.

---

### Post by jeezum crow on 2009-05-01
It must be nice to have an Brit keyboard.:)

---

### Post by 987poiuytrewq on 2009-05-02
It is handy for entering prices but the £ character is about the only character not used as a special character in any programming language, so it's really handy for substitution.

---

