---
title: "$ sign in $PATH"
date: 2011-12-01
forum: Desktop Environments
---

### Post by 71GA on 2011-12-01
Hello, can anyone explain to me what does ```
$
``` mean if i use it like this: ```
$PATH
```


Ty

---

### Post by nothingspecial on 2011-12-01
It signifies a variable. You can assign one or more values to a variable

```
nothingspecial@magik:~$ var=1
nothingspecial@magik:~$ echo $var
1
nothingspecial@magik:~$ var=*
nothingspecial@magik:~$ echo $var
Documents Music Videos

```



$PATH is an environment variable. To see yours type

```
env
```

---

### Post by 71GA on 2011-12-01
Ty :)

---

