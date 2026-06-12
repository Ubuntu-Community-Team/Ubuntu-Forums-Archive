---
title: "Bash script in one line"
date: 2010-01-08
forum: Desktop Environments
---

### Post by xx77aBs on 2010-01-08
Hello ! I'm using ubuntu for some time, and bash scripts are so wonderful :)

So I'm doing very much thing with them, but I don't always want to create new file, write script in it, execute it and then delete it (because I won't need it anymore).

So can you give me link or something where I can find out about writing bash scripts in one line ? Is it possible ?

Let's say I have this :

```
!/bin/bash

for direc in */; do
        mv "$direc"* "./"
        rmdir "$direc"
done


```

and this:

```
!/bin/bash

for f in *.avi; do
    if [ -e "$f.rar" ]; then
        rm -f -v "$f"
    fi
done


```

Can I write these scripts in one line ?? 


Thank you :)

---

### Post by lukjad on 2010-01-08
There probably is something in [here]("http://tldp.org/LDP/abs/html/").
Specifically [here]("http://tldp.org/LDP/abs/html/arrays.html#COPYARRAY").

---

### Post by Zorael on 2010-01-08
If you just want to execute them as single lines in a terminal, sure.
```
!/bin/bash

for direc in */; do
        mv "$direc"* "./"
        rmdir "$direc"
done
```
```
$ for direc in *; do mv "$direc"* "./"; rmdir "$direc"; done
```

```
!/bin/bash

for f in *.avi; do
    if [ -e "$f.rar" ]; then
        rm -f -v "$f"
    fi
done
```
```
$ for f in *.avi; do if [ -e "$f.rar" ]; then rm -f -v "$f"; fi; done
```

---

### Post by Simian Man on 2010-01-08
You can also split up lines by adding a "\" at the end of the line.  This will tell bash the command is continued on the next line:

```

for direc in */; do \
        mv "$direc"* "./" \
        rmdir "$direc" \
done

```

This is a common thing that's also used for C preprocessor macros and Mathematica among others.

---

