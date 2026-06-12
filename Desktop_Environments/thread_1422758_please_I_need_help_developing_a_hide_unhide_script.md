---
title: "please I need help developing a hide/ unhide script"
date: 2010-03-05
forum: Desktop Environments
---

### Post by drvista on 2010-03-05
[B]Hi all I am not a programmer but i like computers and i am an amateur coder just some random codes here and there 
I am trying to create a new nautilus action that will hide a file and another one to unhide a file
I read somewhere if I created a file named *.hidden* in a folder and put in each line filenames i want to hide it will be hidden from nautilus
so i did it and created an action that will run a script that will add the file name to that file and it works but I need Help of the community to make a loop or something so when a user select multiple files all are unhidden as i succeeded to make it hide one file only[/B]
here is HIDE code
> #!/bin/bash

dname=`dirname $1`
fname=`basename $1`

`echo $fname >> $dname/.hidden `
done
and here is UNHIDE code

> #!/bin/bash
fname=`basename "$1"`
dname=`dirname "$1"`
sed -i '/"$fname"/d' "$dname"/.hidden > "$dname"/.hidden 

---

### Post by fbianconi on 2010-03-05
for i in "$@"; do
  dname=`dirname "$i"`
  fname=`basename "$i"`
  echo "$fname" >> "$dname"/.hidden
done

---

### Post by drvista on 2010-03-05
please help me with this code
it doesn't work for more than one file

#!/bin/bash
for i in "$@"; do
dname=`dirname "$i"`
fname=`basename "$i"`
`sed -i '/"$fname"/d' "$dname"/.hidden > "$dname"/.hidden`
done

---

