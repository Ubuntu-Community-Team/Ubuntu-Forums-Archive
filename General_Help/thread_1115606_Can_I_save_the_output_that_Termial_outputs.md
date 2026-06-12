---
title: "Can I save the output that Termial outputs?"
date: 2009-04-04
forum: General Help
---

### Post by tonyW303 on 2009-04-04
So say I type some command that gives me a massive output. Is there anyway to have Terminal to write the output to a separate file, in addition to the Terminal... The wording is really bad but you know what I mean. Thanx!

---

### Post by firefly2442 on 2009-04-04
Sure, just add > filename.txt to the end of the command.  For example, when you open up the terminal you could type this:

```
ifconfig > output.txt
```

And it will save a file (in the current directory) with the output. 

ifconfig is just an example, replace this with whatever command you are using.

 HTH. :)

---

### Post by joshrobinson on 2009-04-04
```
command > textfilename.txt
```
so an example would be
```
lsmod > output.txt
```

and the output of the command will be written to the text file in the directory you are currently in.

---

### Post by joshrobinson on 2009-04-04
> **firefly2442 said:**
> Sure, just add > filename.txt to the end of the command.  For example, when you open up the terminal you could type this:

```
ifconfig > output.txt
```

And it will save a file (in the current directory) with the output. 

ifconfig is just an example, replace this with whatever command you are using.

 HTH. :)

You beat me by seconds!

---

### Post by kanikilu on 2009-04-04
Simply redirecting it to a file using ">" won't show it on STDOUT as well.

You can use tee to do that. Say you want to list a directory called "dir" and show it on the display and write it to a file called dir.txt:```
ls dir | tee dir.txt
```

---

