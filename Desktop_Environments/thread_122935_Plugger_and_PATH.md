---
title: "Plugger and PATH"
date: 2006-01-28
forum: Desktop Environments
---

### Post by fredsan on 2006-01-28
Please Help,

I have installed plugger 5.1.3 and having a problem with Adobe reader 7.0 and Open Office. At the testing page it says no appropriate application found for Open Office. For Adobe it just sits there. I believe the problem is these programs are not in my Path.

How can i find this out? And how can I fix this?

:-k

---

### Post by cwaldbieser on 2006-01-29
[QUOTE=fredsan]Please Help,

I have installed plugger 5.1.3 and having a problem with Adobe reader 7.0 and Open Office. At the testing page it says no appropriate application found for Open Office. For Adobe it just sits there. I believe the problem is these programs are not in my Path.

How can i find this out? And how can I fix this?

:-k[/QUOTE]
Well, if you got OO from the repositories, it should be in /usr/bin.  Open a terminal and type:
```

$ type oowriter2

```
(This is for Open Office 2 Writer).  It should tell you where the program executable is.

If you type
```

$ echo $PATH

```
That should show you your command path.
If you type 
```

$ oowriter2

```
It should launch if it is in your command path.  If not, you can add it by editing your ~/.bashrc.

I have not worked with plugger, so I am not sure what it does or if the PATH issue suspect is really your problem.

---

