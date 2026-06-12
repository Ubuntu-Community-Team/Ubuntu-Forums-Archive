---
title: "Shell script would not copy my files"
date: 2009-01-28
forum: General Help
---

### Post by nvmedhekar on 2009-01-28
Bash refuses to copy my files, I am dumbfounded!

#!/bin/bash

echo 'Executing for i=1'
# executing a script that run a large computation and creates an output file myout, the script exe runs fine from the prompt
exe
echo "Execution complete"
cp myout myout.1
cat myout >> myout.all

# rerun the script
echo 'Executing for i=2'
exe
echo "Execution complete"
cp myout myout.2
cat myout >>  myout.all
----------

This script never creates myout.1 nor it redirects myout.1 into myout.all. However, it does create myout.2 correctly and puts its content in myout.all.

I am very perplexed, please help!

---

### Post by cmnorton on 2009-01-30
1) What does exe do?

2) How are you running this script? What does your command line look like?

3) Enter pwd. What is the result of running the command and do you have permissions to write files there?

4) Enter ls -ld /home/your-home-directory Is it write-protected?

5) Could it be that exe cannot create myout and the copy fails, because there is nothing to copy?

---

