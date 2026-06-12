---
title: "edit series of files usind a script (.sh)"
date: 2009-06-01
forum: General Help
---

### Post by ysricharan on 2009-06-01
Hello,
              I'm working on a series of gerris gfs simulation files. I need to add a line 
"Save t?.ppm { width = 500 height = 344 }" in a series of files named half-cylinder-?.0.gfs. I think the best way to do is to write a script and run it in the terminal. Could someone help me out with the script?. I'm not a very good programmer myself!. thanks in advance!!

Sri

---

### Post by expelledboy on 2009-06-02
You are abit unclear as to what you want..:-k something like this?

-move to the directory with all the files
```
touch script.sh
chmod +x script.sh
gksudo gedit script.sh
```
-paste the following code 
```
#!/bin/bash

echo 'Edited:'
for FILE in $( ls half-cylinder* ); do
    echo "   $FILE"
    CROP=${FILE#ha*r-}; NUM=${CROP%.0*fs}
    echo "Save t$NUM.ppm { width = 500 height = 344 }" >> $FILE
    done
echo 'Bash just looks weird.. hail python!'

```
-run the script
```
./script.sh
```

That will append that line to the end of every file. Dont ask me to do anything more complicated though.. my bash is up to sh*t. :P

---

