---
title: "Script bash shell"
date: 2017-02-22
forum: Education &amp; Science
---

### Post by archeon2 on 2017-02-22
I need make an script to calculate the number of dirs and subdirs for separate


I make this but only calculate the sum of all

#!/bin/bash
find $1 -maxdepth 1 $TIPO | wc -l


TIPO=""
case $2 in
-d)TIPO1="-type d";;
-f)TIPO2="-type f";;
-b)TIPO3="-type f -o -type d"
esac






echo "hay" $TIPO1 "archivos tipo d"
echo "hay" $TIPO2 "archivos tipo f"
echo "hay" $TIPO3 "de d y f"

---

### Post by bonestabone on 2017-03-31
Does that need to be "-mindepth" option in the find command?

[https://serverfault.com/questions/42864/how-to-count-all-subfolders-in-an-directory](https://serverfault.com/questions/42864/how-to-count-all-subfolders-in-an-directory)

---

