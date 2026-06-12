---
title: "[Script] Get Random File from current dir"
date: 2009-03-07
forum: General Help
---

### Post by ekaqu on 2009-03-07
I am trying to write a script for myself that will get a random file or dir from the current dirrectory and echos it out so that it can be used in other commands like  randomFile | xargs cd  or randomFile | xargs vlc

I watch a lot of videos from my computer and rather than flipping a coin (which is what i do now) to find a random file or dir, I would rather use a script.

My script so far (dont really care what shell I am using)

```

#!/bin/ksh
set +A files ./*    # create an array of the files.
N=${#files[@]}           # Number of members in the array
((N=RANDOM%N))
randomfile=${files[$N]}
echo "$randomfile"

```

This code was found and modified from [http://www.unix.com/shell-programming-scripting/34109-getting-random-file.html](http://www.unix.com/shell-programming-scripting/34109-getting-random-file.html)

My issue at the moment is that the script breaks when there are files with spaces in them.

If anyone is able to help, I would very much appreciate it.

---

### Post by dcstar on 2009-03-07
> **ekaqu said:**
> I am trying to write a script for myself that will get a random file or dir from the current dirrectory and echos it out so that it can be used in other commands like  randomFile | xargs cd  or randomFile | xargs vlc

I watch a lot of videos from my computer and rather than flipping a coin (which is what i do now) to find a random file or dir, I would rather use a script.

My script so far (dont really care what shell I am using)

```

#!/bin/ksh
set +A files ./*    # create an array of the files.
N=${#files[@]}           # Number of members in the array
((N=RANDOM%N))
randomfile=${files[$N]}
echo "$randomfile"

```

This code was found and modified from [http://www.unix.com/shell-programming-scripting/34109-getting-random-file.html](http://www.unix.com/shell-programming-scripting/34109-getting-random-file.html)

**My issue at the moment is that the script breaks when there are files with spaces in them.**

If anyone is able to help, I would very much appreciate it.

Put single quotes around any file descriptor.

---

### Post by ekaqu on 2009-03-07
Alright, the script now returns a file with spaces
```
$ randomFile
./3X3 Eyes - Worlds Collide.avi
```

but if I do 
```
randomFile | xargs -0 vlc
```

I get something like this
> [00000408] main input error: open of `./Mahoromatic - As Mahoro Sleeps.avi
' failed: could not create access: no suitable access module

Any ideas at what I can do?

---

