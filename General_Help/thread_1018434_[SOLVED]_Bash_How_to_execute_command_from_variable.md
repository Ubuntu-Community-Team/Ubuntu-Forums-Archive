---
title: "[SOLVED] Bash: How to execute command from variable?"
date: 2008-12-22
forum: General Help
---

### Post by abcuser on 2008-12-22
Hi,
on Ubuntu 8.10 I would like to write bash script. From complex transformation I get variable command1 filled. I would like to execute command that is in variable command1.
```

#!/bin/bash
command1=$(echo ls -l)   # Variable where some command is defined
"$command1"              # Execute command

```
But the last command returns error:
line 3: ls -l: command not found

How to execute command that I already have in variable command1?
Regards

---

### Post by joehte on 2008-12-22
Use eval.

```

MYCMD='ls -l'
eval $MYCMD

```

---

### Post by capscrew on 2008-12-22
> command1=$(echo ls -l)   # Variable where some command is defined

The above should be:```
command='ls -l
```

When it is used as:```
$command
```
It will return```
ls -l
```

---

### Post by abcuser on 2008-12-22
joehte,
Just a note. I can have one or multiple commands in command1 variable, so I need to add quotation marks around varialbe.

```

#!/bin/bash
command1=$(echo ls -l)   # Variable where some command is defined
eval "$command1"              # Execute command
```

Problems solved. Thanks a lot.
Regards

---

