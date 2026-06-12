---
title: "Bash Script Help"
date: 2009-06-14
forum: General Help
---

### Post by digthis86 on 2009-06-14
Hello everyone, I have looked everywhere for a solution to my problem, but I cannot find anything. I am trying to write a bash script that will read other filenames in a directory and then it will add 1 to each new file. It will go like this.

Read file names in exampleDIR:

1.jpg 2.jpg 3.jpg 4.jpg

Finds out that the last filename is 4.jpg. Then new file name will be:

5.jpg

Read files in exampleDIR:

1.jpg 2.jpg 3.jpg 4.jpg 5.jpg

So basically, I am trying to save a file by reading the other filenames and "adding" 1 to the filename. (if 4.jpg, 1 + 4 = 5, newFilename = 5.jpg)

I hope I explained this well.
THANKS

---

### Post by kaibob on 2009-06-14
Message removed by Kaibob.

---

### Post by loomsen on 2009-06-14
Configure <foobar> to save the file as 
filename_%NNN.jpg 
This will cause your desired behavior, no need for a script.

---

### Post by kaibob on 2009-06-14
Message removed by Kaibob.

---

### Post by leandromartinez98 on 2009-06-14
> **digthis86 said:**
> Hello everyone, I have looked everywhere for a solution to my problem, but I cannot find anything. I am trying to write a bash script that will read other filenames in a directory and then it will add 1 to each new file. It will go like this.

Read file names in exampleDIR:

1.jpg 2.jpg 3.jpg 4.jpg

Finds out that the last filename is 4.jpg. Then new file name will be:

5.jpg

Read files in exampleDIR:

1.jpg 2.jpg 3.jpg 4.jpg 5.jpg

So basically, I am trying to save a file by reading the other filenames and "adding" 1 to the filename. (if 4.jpg, 1 + 4 = 5, newFilename = 5.jpg)

I hope I explained this well.
THANKS


```

# This gets the last file
file=`ls *.jpg | grep tail -n 1"
# This removes the .jpg (probably there is something more inteligent)
number=${file/.jpg//}
# This makes the addition
number=`expr $number + 1`
# This moves the file to the new filename
mv $file $number.jpg

```

Always test before using it... I've not tested myself.

---

### Post by ghostdog74 on 2009-06-15
> **leandromartinez98 said:**
> ```

# This gets the last file
[code
file=`ls *.jpg | grep tail -n 1"

```

why "grep"?? . anyway, this method doesn't sort numerically, so if you have 10.jpg, it will come after 1.jpg , which is wrong.

@OP
```

ls *.jpg | sort -n| awk 'BEGIN{  FS="." }
END{
  newfile = $1+1".jpg"
  cmd="cp "$0" "newfile
  system(cmd)
}'

```

---

### Post by loomsen on 2009-06-15
And why not use built ins?

---

### Post by ghostdog74 on 2009-06-15
> **loomsen said:**
> And why not use built ins?

then show an example.

---

### Post by geirha on 2009-06-15
How about counting up to the first available?
```

i=1
while [ -e "$i.jpg" ]; do
  i=$((i+1))
done
echo "$i.jpg is available"

```

If the dir contains *1.jpg 2.jpg 4.jpg*, it will choose *3.jpg* instead of *5.jpg*, so it may not be exactly what you want.

---

### Post by leandromartinez98 on 2009-06-15
> **ghostdog74 said:**
> why "grep"?? . anyway, this method doesn't sort numerically, so if you have 10.jpg, it will come after 1.jpg , which is wrong.

Sorry, the grep was a typo and true, that will not sort correctly.

---

### Post by digthis86 on 2009-06-15
Thanks everyone.

loomsen, I like your idea of using build ins. However, I am writing a script for postprocessing in the cups-pdf. I am printing documents to pdf, however I have change the name after each print. And yes, I know about the "Print to PDF" in Firefox, but i am printing documents from a flash viewer, which does not allow that.

leandromartinez98, I think that is what I am looking for

```

# This gets the last file
file=`ls *.jpg | grep tail -n 1"
# This removes the .jpg (probably there is something more inteligent)
number=${file/.jpg//}
# This makes the addition
number=`expr $number + 1`
# This moves the file to the new filename
mv $file $number.jpg

```

However, I am worried about the grep. It seems that it will check the tail end of file contents, not the tail end of the filename. I could be wrong!

geirha, this will have to do for now. 

I know the logics behind programming, but I need to read a little more about using system variables and built ins. Do you guys know of any good "Linux Programming" books that will show skills such as these?

Thanks

---

### Post by leandromartinez98 on 2009-06-15
The "grep" is wrong!

should be

```

file=`ls *.jpg | tail -n 1`

```

but, as pointed out above, this will not work either, because the
file 10.jpg will come before the file 2.jpg. You must use a sorting
algorithm.

By the way, if the file to be moved is the last file that was modified,
you can use:

```

file=`ls -t | head -n 1`

```

instead, and that will be easier than sorting out the numbers.

---

### Post by leandromartinez98 on 2009-06-15
For learning, put "bash scripting tutorial" on google, it will be a good start. And try out these commands people are suggesting, one by one, and see the outcome, so you will get used to what they do.

---

### Post by kaibob on 2009-06-15
> **geirha said:**
> If the dir contains *1.jpg 2.jpg 4.jpg*, it will choose *3.jpg* instead of *5.jpg*, so it may not be exactly what you want.

The following will generate 5.jpg in the situation described by geirha. I'm not sure if that's what the OP wants but....

```
#!/bin/bash

FILENUMBER=0

for FILE in [[:digit:]].jpg ; do
   FILEBASE=${FILE%\.*}
   [ $FILEBASE -gt $FILENUMBER ] && FILENUMBER=$FILEBASE
done

echo "$((FILENUMBER+1)).jpg is available"
```

---

