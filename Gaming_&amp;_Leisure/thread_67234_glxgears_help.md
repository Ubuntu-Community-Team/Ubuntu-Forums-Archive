---
title: "glxgears help"
date: 2005-09-19
forum: Gaming &amp; Leisure
---

### Post by jasay on 2005-09-19
I messed over my Hoary installation a week or so ago and decided to try Breezy since it's getting close.  Finally got it all up and running with fglrx from ati (apparently 8.16.20 is in the repos now . . .  :? doh.)  Anyway, when I run glxgears it doesn't output the fps.  Any ideas why it would (not) do this or how to fix it?  I'm curious how the new drivers and breezy stack up to Hoary.

---

### Post by FiggyG on 2005-09-19
glxgears isn't a benchmark, but I'm still curious why it doesn't give the numbers.

---

### Post by mlomker on 2005-09-19
Try **glxgears --help**.  There's a ridiculous command line switch to acknowledge that it isn't a benchmark.

Does **fgl_glxgears** work normally?

---

### Post by acariquara on 2005-09-19
[QUOTE=mlomker]Try **glxgears --help**.  There's a ridiculous command line switch to acknowledge that it isn't a benchmark.

Does **fgl_glxgears** work normally?[/QUOTE]

**glxgears --help** results in nothing but an error message and the program running anyway  ](*,) 

**strings /usr/bin/X11/glxgears** generated some interesting results, though.

```

glxgears -iacknowledgethatthistoolisnotabenchmark
```

 :roll:  :roll:  :roll:  :roll:  :roll: yes, that counts in my book as ridiculous....

---

### Post by jasay on 2005-09-19
I know glxgears is hardly a standardized benchmark but, for a given system, a large jump in fps with a new driver still suggests an improvement, no?  If nothing else, it helps me feel like my work installing the ati drivers was worth the effort.

[QUOTE=mlomker]Try **glxgears --help**.  There's a ridiculous command line switch to acknowledge that it isn't a benchmark.

Does **fgl_glxgears** work normally?[/QUOTE]
glxgears ---help is just running the program, not giving options and fgl_glxgears isn't recognized as a command.  Any packages I might be missing?  

Thanks for the suggestions thus far.

---

### Post by jasay on 2005-09-19
[QUOTE=acariquara]```

glxgears -iacknowledgethatthistoolisnotabenchmark
```
[/QUOTE]
Yikes, this actually works for some reason, weird.  Call me lazy, but I don't really want to type that out every time though. :razz:  ;-)

---

### Post by cutOff on 2005-09-20
[QUOTE=jasay]Yikes, this actually works for some reason, weird.  Call me lazy, but I don't really want to type that out every time though. :razz:  ;-)[/QUOTE]
Make an alias 

```
alias glxgears='glxgears -iacknowledgethatthistoolisnotabenchmark'
```

---

### Post by mlomker on 2005-09-20
> glxgears ---help is just running the program, not giving options and fgl_glxgears isn't recognized as a command.  Any packages I might be missing?  


That might have been installed with the ATI drivers, so won't be there if you're running Nvidia.

---

### Post by jasay on 2005-09-20
[QUOTE=cutOff]Make an alias 

```
alias glxgears='glxgears -iacknowledgethatthistoolisnotabenchmark'
```[/QUOTE]

Have never heard of the alias command.  That could prove useful, thanks. :)

---

### Post by cutOff on 2005-09-20
[QUOTE=jasay]Have never heard of the alias command.  That could prove useful, thanks. :)[/QUOTE]
Have a look to this [HowTo](http://ubuntuforums.org/showthread.php?t=44458&highlight=alias)   :-)

---

