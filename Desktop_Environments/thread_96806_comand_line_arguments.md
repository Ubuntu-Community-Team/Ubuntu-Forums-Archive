---
title: "comand line arguments"
date: 2005-11-29
forum: Desktop Environments
---

### Post by kook44 on 2005-11-29
on the command line-
what are the differences between the single-dash and double-dash options
ie:
```

>ls -l -h -a --color

```

seems like the single-dashes often have a more verbose equivalent double-dash.

Are the single-dahses being phased out in favor of the double dashes?  Left around for the old schoolers?

---

### Post by HermanAB on 2005-11-29
Yes :)

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=kook44]on the command line-
what are the differences between the single-dash and double-dash options
ie:
```

>ls -l -h -a --color

```

seems like the single-dashes often have a more verbose equivalent double-dash.

Are the single-dahses being phased out in favor of the double dashes?  Left around for the old schoolers?[/QUOTE]

The double dash is a way for the computer to know that the option that follows is a word rather than a bunch of option.  For example:
```

$ tar -xvvf foo.tar

```
If the single dash was always used, the computer could't tell iff this was 4 options (x,v,v,f) or one option (xvvf).  The double dash basically means that a more human readable word will follow.  The shorties are still useful for common commands where you don't want to type a lot.  Who wants to type "ls --almost-all"?

---

