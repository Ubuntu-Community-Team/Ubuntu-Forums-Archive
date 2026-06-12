---
title: "Sourcing a shell script - what does it mean, how to do it?"
date: 2011-03-28
forum: Desktop Environments
---

### Post by 71GA on 2011-03-28
Hello!

I have to source a script by the shell, but i dont know what this means nor how to do it. Instructions i have are listed below.

```
# This file must be sourced by the shell

export PATH=/usr/local/codesourcery/arm-2010q1/bin:$PATH
export NXPMCU_WINBASE=`pwd`
export NXPMCU_SOFTWARE=`pwd`
export BSP=stick3250_v201
export CSP=lpc32xx
export TOOL=gnu
export GEN=lpc
```

---

### Post by SeijiSensei on 2011-03-28
```
$ . /path/to/the/script
```

---

### Post by 71GA on 2011-03-28
> **SeijiSensei said:**
> ```
$ . /path/to/the/script
```

What does this command do? Can you explain it to a farmer like me :) ? Thank you :)

---

### Post by sisco311 on 2011-03-28
> **71GA said:**
> What does this command do? Can you explain it to a farmer like me :) ? Thank you :)

The **source** or `.' ( a period without the quotes is shorthand for **source** ) bash builtin command reads and executes the commands from a file in the current shell environment.

See:
```
env LESS="$LESS +/^ +\. +filename" man bash
```

So you have to edit the file ~/.bashrc and append it with something like:
```

if [ -f /path/to/file ]; then
    . /path/to/file
fi

```

Where /path/to/file is the path to the file you want to `source'.

The file you posted will initialize and export some environment variables, most likely used by the application you are trying to install. Exported variables will be inherited by any subshell or child process.

See:
[http://en.wikipedia.org/wiki/Environment_variable](http://en.wikipedia.org/wiki/Environment_variable)
[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

Hope this makes sense to you. If not, please feel free to ask any question. :)

---

### Post by 71GA on 2011-03-29
```
env LESS="$LESS +/^ +\. +filename" man bash
```

I am a bit lost here... it seems like i change the value of variable LESS to something that was there before and something new.

---

### Post by sisco311 on 2011-03-30
The command simply opens the manual page of bash at the section where the `source' command is explained.

Bash by default uses less as its pager. The LESS variable stores the options which are passed to less automatically.

env runs a command in a different environment. 

$LESS is the old value of the LESS variable.

+/PATTERN tells less to search for PATTERN in the file.

In our case the pattern is "^ +\. +filename"
"^"  matches the starting position of any line
" +" matches one or more spaces
"\." matches a literal period
and "filename" matches the string "filename" :)

---

