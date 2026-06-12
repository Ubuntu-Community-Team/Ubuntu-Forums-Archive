---
title: "CLI: how to store exact regex matches not matched lines (awk, grep)?"
date: 2009-06-04
forum: General Help
---

### Post by dubref on 2009-06-04
Problem: how to store exact matches from regex search

I have a file with the following structure:

Jibberish moreJibberish
Jibberish MyLittlePony(DoNotWant)
Jibberish MyBigHorse(DoNotWant)
Jibberish Mydonotwant again(
Jibberish againJibberish

I want to get an output file with only strings starting with My**** ending with opening parenthesis (that is ( ), where there are no spaces between My**** and opening parentheis,

In other words output file should look like this:
MyLittlePony
MyBigHorse

It appears grep only gives you results line by line, so I turned to awk

current try
```

awk ' /My[^ ]+\(/ { print $2 }' myfile > resultfile

```
This almost works except except $2 gives me the whole second field including (DoNotWant) part....
what I would like to do is this
```

awk ' myvar=/My[^ ]+\(/ { print myvar }' myfile > resultfile

```
however that doesn't work myvar gets assigned value of 1(indicating match is true?) not the matching string .

Any suggestions?

---

### Post by tlacuache on 2009-06-04
$ egrep -o -e "My[^[:space:]]*\(" hey.txt 
MyLittlePony(
MyBigHorse(

If you don't want the ( you could strip it off with sed:

$ egrep -o -e "My[^[:space:]]*\(" hey.txt | sed "s/(//"
MyLittlePony
MyBigHorse

The -o tells grep to output only the matching portion.

---

### Post by dubref on 2009-06-05
Thank you very much!

Worked perfectly. :)

Just a bit embarrassed now, that I didn't read man grep fully, just skimmed it.

---

