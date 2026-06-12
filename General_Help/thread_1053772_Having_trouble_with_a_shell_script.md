---
title: "Having trouble with a shell script"
date: 2009-01-29
forum: General Help
---

### Post by tabor on 2009-01-29
Basically what I am making is a script that will just allow me to move multiple images to another folder.  I know I could just cut/paste but I want some practice with shell scripts and so I wrote this up. 

```

#!/bin/sh

cd ~/Pictures

ls *.jpg -1 > number.txt

x=`grep jpg number.txt -c`

echo "Where would you like these to go?"
read name
mkdir $name

y=1
while [ $y -le $x ]
    do
      head -1 number.txt > filename.txt
      n=`cat filename.txt` 
      mv $n $name/$n
      echo "$n has been moved"
      y=`expr $y+1`  
done
rm filename.txt
rm number.txt
cd

```

It moves the first file no problem, but then quits out with an error:

```

[: 21: Illegal number: 1+1

```

Which leads me to believe it has something to do with my y=`expr $y+1`


Any ideas?

---

### Post by kidders on 2009-01-30
Hi there,

> **tabor said:**
> ```
Illegal number: 1+1
```

You probably want to write **y=`expr $y + 1`**, not **y=`expr $y+1`**.

Even with that correction though, your script won't work. As far as I can tell, it will try to move the same file over and over, and would break if that file were called "1 2 3.jpg". It would do nothing at all if ~/Pictures contained a single file called "123.Jpg".

What you're trying to do can be achieved with **mv ~/Pictures/*.jpg /path/to/target**, but since you're going to the trouble of writing a script, I would suggest using **find**. That will help you circumvent some of the limitations of a simple **mv** (eg case sensitivity, argument length restrictions), and cut out the use of temporary files.

I would also suggest changing **mkdir $name** to **mkdir -p $name**, so you can specify paths like ~/a/b where neither "a" nor "b" exists, and avoid producing error messages if the target path doesn't need to be created.

I hope that helps.

---

### Post by kpatz on 2009-01-30
Here's a simpler way to do it:

```

#!/bin/sh

echo -n "Where would you like these to go? "
read name
mkdir -p "$name"

cd ~/Pictures

for n in *.jpg
do
  mv "$n" "$name"
  echo "$n has been moved"
done

```

Or, an even simpler way, if you don't care about how the "$n has been moved" lines look:

```

#!/bin/sh

echo -n "Where would you like these to go? "
read name
mkdir -p "$name"

mv -v ~/Pictures/*.jpg "$name"

```

A couple things I did that you didn't have in your script:[list][*]The -p option on the mkdir, to create an entire path even if it doesn't exist.  Say you specify my/full/path, if my doesn't exist, it will create it, then create full, then path.[*]I also put "$name" inside quotes, so that paths with spaces will work.  In the first version of the script (using the loop to move files individually), I put $n in quotes as well so that filenames with spaces don't break things.[*]The -n on the initial prompt, so that the cursor stays on the same line after the question mark.[/list]

---

### Post by sedawk on 2009-01-30
There is an easier way for counting lines:
```

x=$(ls *jpg|wc -l)

```

I would also recommend to copy stuff instead of moving it.
(At least until you tested it works as suggested! Errors
 during moving (renaming) files can be fatal!)

Short solution would be
```

cp -t $name ~/Pictures/*.jpg

```

Do not write interactive scripts where not needed, e.g.
pass the target directory as an argument to your script!
```

target_dir=$1
...

```

---

