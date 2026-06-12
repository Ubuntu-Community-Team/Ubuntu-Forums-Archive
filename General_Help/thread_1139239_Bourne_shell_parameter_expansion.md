---
title: "Bourne shell parameter expansion"
date: 2009-04-26
forum: General Help
---

### Post by jwmwalrus on 2009-04-26
Hi,

I am having trouble trying to run about a hundred shell scripts (sh, provided by third parties).  I have noticed that most of the variables defined in those scripts have "//\\//" as part of the substitution, and that seems to be the problem.  When I try to run the test

#!/bin/sh -f
SOMETHING=/home/auser
SOMEOTHER=${SOMETHING//\\//}/this.txt
echo $SOMEOTHER

I get a "Bad substitution" error.  Since those scripts work just fine using gnome-terminal in Red Hat EL, is there any way to make them work in Ubuntu as well?

Thanks in advance for any help provided.

---

