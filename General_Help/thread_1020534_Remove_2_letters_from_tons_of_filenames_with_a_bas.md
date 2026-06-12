---
title: "Remove 2 letters from tons of filenames with a bash script?"
date: 2008-12-24
forum: General Help
---

### Post by crazyfuturamanoob on 2008-12-24
I got many files, and there is ";1" after their filenames. Don't ask why, because I don't know.

They are like: "file.txt;1", "picture.bmp;1" and so on. Too many files to rename by hand, 
so I wish that could be done automatically. So I want to rename them to like this: "file.txt", "picture.bmp".

But unfortunately I don't know bash at all. Maybe someone helpful member of ubuntuforums could do this?

Could you at least make me a program chunk which I could edit?

---

### Post by kevdog on 2008-12-24
How about using sed.

Make a copy of the file (so you can test the solution below) and then try something like this:

cat <file name> | sed 's/;1//g'

---

### Post by crazyfuturamanoob on 2008-12-24
> **kevdog said:**
> How about using sed.

Make a copy of the file (so you can test the solution below) and then try something like this:

cat <file name> | sed 's/;1//g'

But I don't want to be typing 500 filenames. Can that <file name> be replaced with a variable or something?

And I can't give the file extension because there are many different files with different extensions, all with that ;1 after their names.


Edit: Tried it. Doesn't work, obviously because I didn't change <file name>:
```

arho@ohra-laptop:~/Työpöytä/test$ chmod +x rename.sh
arho@ohra-laptop:~/Työpöytä/test$ ./rename.sh 
./rename.sh: line 1: syntax error near unexpected token `|'
./rename.sh: line 1: `cat <file name> | sed 's/;1//g''
arho@ohra-laptop:~/Työpöytä/test$ 

```

---

### Post by kaibob on 2008-12-24
Have a look at this thread--it addresses the identical issue:

[http://ubuntuforums.org/showthread.php?t=1012353](http://ubuntuforums.org/showthread.php?t=1012353)

My suggestion in that thread was:

```
find /directory/name -name '*;1' -type f -exec rename -n 's/;1$//' '{}' ';'
```

Change /directory/name and then run the command in a terminal window. The -n option directs rename to do a dry run and report proposed changes. If all appears well, change -n to -v and rerun the command to actually rename the files.

The above command-line works recursively on all files in the target directory and subdirectories. If all of the files are located in one directory, then you only need to run the rename command:

```
rename -n 's/;1$//' *.\;1
```

Be sure to run these commands on test files.

---

### Post by djbushido on 2008-12-24
an easier script might be:
```
mv "*;1" "*"
```
or
```
mv *;1 *
```

but I would also recommend a Gui, and especially doing this on a test batch.
Good Luck!

---

### Post by sisco311 on 2008-12-24
1.) backup your files
2.) backup your files
3.) repeat step 1 and 2
4.)

```
rename -n 's/;1$//' "*;1"
```should do the trick.

(remove the -n (noaction) flag to actually rename the files)

or

5.)

```
for FILE in *; do echo mv $FILE ${FILE/;1/}; done
```

(remove the echo command to rename the files)

---

### Post by crazyfuturamanoob on 2008-12-24
> **kaibob said:**
> Have a look at this thread--it addresses the identical issue:

[http://ubuntuforums.org/showthread.php?t=1012353](http://ubuntuforums.org/showthread.php?t=1012353)

My suggestion in that thread was:

```
find /directory/name -name '*;1' -type f -exec rename -n 's/;1$//' '{}' ';'
```

Change /directory/name and then run the command in a terminal window. The -n option directs rename to do a dry run and report proposed changes. If all appears well, change -n to -v and rerun the command to actually rename the files.

The above command-line works recursively on all files in the target directory and subdirectories. If all of the files are located in one directory, then you only need to run the rename command:

```
rename -n 's/;1$//' *.\;1
```

Be sure to run these commands on test files.

Why GUI? That's just a lot extra work.

That worked fine, thanks :D

> **djbushido said:**
> an easier script might be:
```
mv "*;1" "*"
```
or
```
mv *;1 *
```

but I would also recommend a Gui, and especially doing this on a test batch.
Good Luck!

I tried that too, didn't work. Error: "blahblahblah isn't a file or direcory".

---

### Post by kaibob on 2008-12-24
> **crazyfuturamanoob said:**
> Why GUI? That's just a lot extra work...
I agree--the command line is so much better. :P 

But, some of these commands can do a lot of harm with just a few mistakenly-typed letters, and the experience level of a user is pretty much an unknown. This is especially a concern with command-lines that recursively rename files. Just makes me a bit nervous, which is why I sometimes suggest a GUI when one is available. That's also why I like the use of the rename command with the -n option.

---

### Post by thisperishedmin on 2008-12-24
> **kaibob said:**
> I agree--the command line is so much better. :P 

But, some of these commands can do a lot of harm with just a few mistakenly-typed letters, and the experience level of a user is pretty much an unknown. This is especially a concern with command-lines that recursively rename files. Just makes me a bit nervous, which is why I sometimes suggest a GUI when one is available. That's also why I like the use of the rename command with the -n option.

sed can make one a bit nervous...

but I get a slight palm sweat everytime I key in the good ole "rm -rf", even after all these years :)

rm -rf . typo is the worst...assuming you missed your /<folder name> somehow lol

---

