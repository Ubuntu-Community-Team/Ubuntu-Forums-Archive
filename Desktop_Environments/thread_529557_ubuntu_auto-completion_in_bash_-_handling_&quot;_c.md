---
title: "ubuntu auto-completion in bash - handling \&quot; characters"
date: 2007-08-19
forum: Desktop Environments
---

### Post by jf/ on 2007-08-19
hi guys, as per subject. I have handled (and still use) many other distros, and it seems to me that the behaviour of bash in ubuntu with regards to the \" character is different. 

For eg., let's say i have a directory (or filename) starting with the \" character...

```

$ ls -l ~
drwxr-xr-x 4 jf jf 4096 2007-08-20 00:26 "SOURCE"

```

if i were to type in '[SIZE="3"][COLOR="Red"]**ls -l \"**[/color][/size]' at my home directory, i would have to press <tab> twice to be able to get autocompletion to the correct name. The first tab will transform '[SIZE="3"][COLOR="Red"]**ls -l \"**[/color][/size]', to [SIZE="3"]'[COLOR="red"]**ls -l \\\"**[/color][/size]', and then the second tab will fill in the name of the directory. Compared to the other distros, one tab does it. I'm just wondering, why is this so?

In addition, with ubuntu, this \" autocompletion does **not** work if i prefix the \" with any other characters. eg.s:
```

ls ~/\"

ls /home/jf/\"

```

a <tab> here will then get rid of the \" characters that i type.

Is there any way to get rid of this, or fix this?

---

### Post by jf/ on 2007-08-20
up...

---

### Post by jf/ on 2007-08-21
nobody?

---

### Post by mannheim on 2007-08-21
I don't know if this is it, or not:

There are two varieties of completion in bash. By default (I think), bash is installed with the "less smart" completion. Smarter, programmed completion features are enabled by sourcing the file /etc/bash_completion from your .bashrc file. The smart completion can do things like auto-complete the long arguments of many commands. But smart completion also has quirks.

The behavior you describe (needing to hit tab twice after \") occurs (for me) when using the "smart" completion (even though this seems less smart). If I comment out the line
```
 . /etc/bash_completion
```
in my .bashrc, then I get the other behavior: only one tab is needed.

---

### Post by jf/ on 2007-08-21
:) ah, ok, thanks for the quick fix...

---

