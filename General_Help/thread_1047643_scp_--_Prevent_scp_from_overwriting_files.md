---
title: "scp -- Prevent scp from overwriting files?"
date: 2009-01-22
forum: General Help
---

### Post by kyleflan on 2009-01-22
I'm writing a batch file to automatically create a directory on a server and then copy a few template files to that directory. However, if there is already a file in that folder that I'm trying to transfer (i.e. template1.html) then I don't want to overwrite that file. 

Is there an argument I can pass to scp to prevent scp from overwriting a file? The code is shown below, if that helps.

```

#!/bin/sh
#This program creates a directory on a foreign machine using SSH
#It copies templates to the directroy using scp
 
if [ ! -n "$1" ]; then
	echo Enter directory
	read vari
else 
	vari=$1
fi
`ssh user@123.123.123.123 mkdir /dir/dir2/dir3/$vari`
echo "Made directory $vari"
`scp /home/user/* user@123.123.123.123:/dir/dir2/dir3/$vari/`
echo "done"


```

---

### Post by spiderbatdad on 2009-01-22
scp will overwrite if file owner has write permissions. Perhaps scp as another user.
There is also a script found here:[http://www.unix.com/shell-programming-scripting/27312-scp-without-writting.html](http://www.unix.com/shell-programming-scripting/27312-scp-without-writting.html)

---

