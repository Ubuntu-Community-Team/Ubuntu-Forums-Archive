---
title: "cvscedega registry error"
date: 2006-06-20
forum: Gaming &amp; Leisure
---

### Post by keithjr on 2006-06-20
I'm having a tiny little problem doing the cedega-from-cvs installation using the guides found here and on linux-gamers.  The installation of the cedega profile 1) runs fine, but when I first run cvscedega to get the configuration set up, I get this:

```
keithjr@ubuntu:~/wine$ cvscedega

Enter Path for first Drive (C:) (Default: /home/keithjr/.cvscedega/drive_c)
Newbies, press enter

Making fake C drive...


Edit the /home/keithjr/.cvscedega/config file to fit your system

Installing registry...



Registry Install failed ...
Remove /home/keithjr/.cvscedega .reg files to try again.
```


I have a feeling I can just ignore this error, but I don't know if it'll come back and bite me later.  Is this just happening because I'm running cvscedega without any input arguments?


<edit>

I found this text in a file called reglog in my .cvscedega folder:

```
/usr/lib/cvscedega/bin/regapi: line 51: exec: : not found
```

I think my hunch might have been right.

---

### Post by keithjr on 2006-06-21
[QUOTE=pizaro]LETS ALL POST CARD OOOOOO
[/QUOTE]


Yes that is very nice, but it doesn't quite answer my question...:confused: 

Enjoy being banned.

Now, back to the matter at hand, no I do not think that this registry problem is benign anymore... cvscadega command won't run ANY executables, keeps throwing that same error.  Anybody got any idea what I did wrong?

---

### Post by keithjr on 2006-06-21
ya know, I just noticed something... usually spammers attack multiple threads but this guy only went for mine, it would seem.

guess its just my lucky day

---

### Post by keithjr on 2006-06-23
Meh, I'll bump it one more time, could a mod please cut out those malignant posts?  This can't be that complicated a problem but I'm completely lost...

---

### Post by dphipps on 2006-08-29
I have the same problem, but I do not know what to do about it.

---

### Post by OuTcRy on 2006-10-24
i have the same problem too...
what we can do for this?

---

