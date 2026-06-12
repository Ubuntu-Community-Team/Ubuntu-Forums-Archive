---
title: "Diffeerent output formats from grep in different folders ?"
date: 2009-04-29
forum: General Help
---

### Post by Tony Flury on 2009-04-29
I have two folders both under my home directory, but with a lot of text files (*.txt) in them (and a few other files)....

When I execute this command : 
```

grep -e photo -f *.txt

```

The results are formatted differently between the two folders : 

In 1 folder I get the filename output before the matching line - exactly as I expect.

In the other folder I get the matching line output - but no file name.

So why are the formats different ?

---

### Post by Tony Flury on 2009-05-21
bump - any answer to this puzzle ?

Why should running the same command in two different folders result in such different formatted outputs ?

---

### Post by Confuseling on 2009-05-21
Just a random thought, but does "ls -lh" report that you have the same permissions on each directory / group of files?

---

### Post by StuartN on 2009-05-21
If there is only one matching file for *.txt then grep will not prefix the output with the filename, same as grep -h. If you always want filenames then use grep -H.

---

### Post by Tony Flury on 2010-05-25
In case anyone is interested - I worked it out - in the second folder - where i don't get the file names, one of the file names started with a "-" character, so that when the *.txt was expanded by the shell it took the file name as an option - and turned off the "-f" option.

---

