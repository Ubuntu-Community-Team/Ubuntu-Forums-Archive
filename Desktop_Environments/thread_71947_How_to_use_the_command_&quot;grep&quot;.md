---
title: "How to use the command &quot;grep&quot;"
date: 2005-10-04
forum: Desktop Environments
---

### Post by thtan on 2005-10-04
Hi all. I assume u know what the command grep is used for, Basically, it is used to search for a certain pattern in a file (correct me if i'm wrong).

Here's my question:

Suppose i have a file out.txt that has many lines that goes like this:

+ 1 2 good xxx --- 1.02 5
- 1 3 good xxx --- 1.07 6
d 2 4 drop yyy --- 1.08 7
r 5 6 reply rrr --- 1.09 8
.....

i would like to search the file for any line that contains the "letter d" AND the "word drop" and count the number of such occurence.

I've got some clue of figuring the counting part of just a single occurence
(by using $grep d out.txt -c), 
but no clue for counting both AND parts. 

Please help. Thanks.

---

### Post by Zelut on 2005-10-04
find any tips using the man pages?  #man grep should give you some pretty good ideas if you haven't already looked there.

---

### Post by UbuWu on 2005-10-04
grep d out.txt | grep drop -c

Although this will be the same as just grepping for drop, as drop contains a d. Maybe you could change d to 'd '.

So that would be:

grep 'd ' out.txt | grep drop -c

---

### Post by circussideshow on 2005-10-05
some googling (i'm working with awk/grep as well):

[http://es-sun2.fernuni-hagen.de/cgi-bin/info2html?(grep)Usage]("http://es-sun2.fernuni-hagen.de/cgi-bin/info2html?(grep)Usage")

[http://pegasus.rutgers.edu/~elflord/unix/grep.html]("http://pegasus.rutgers.edu/~elflord/unix/grep.html")

---

### Post by jworr on 2005-10-05
Here I hope this helps

egrep ^d out.txt | grep drop /dev/stdin -c

This assumes the letter d is at the begining of a line in the text file which looked like it was the case from the example you gave if not remove the ^ from the statement above

---

