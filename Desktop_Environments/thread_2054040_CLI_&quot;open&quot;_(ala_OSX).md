---
title: "CLI &quot;open&quot; (ala OSX)"
date: 2012-09-06
forum: Desktop Environments
---

### Post by iaw4 on 2012-09-06
(I am switching from OSX to ubuntu.)

under OSX, I can type in a Terminal "open file.xls" and file is opened by the desktop with the system app.  is there an equivalent ubuntu 12.04 CLI command?

---

### Post by sisco311 on 2012-09-06
xdg-open or gnome-open

---

### Post by iaw4 on 2012-09-19
is there an easy way to also specify the application?

  open -a "Emacs" hello.html

(the advantage is that the errors and warnings don't go to the terminal, and an accidental C-C on the launch terminal won't abort the program.)

/iaw

---

### Post by vexorian on 2012-09-19
well, if what you want is not to let closing the terminal kill the app then you can use disown

```

emacs hello.html & disown

```

If you want to disable messages, then you can redirect output to /dev/null

```
emacs hello.html 1> /dev/null 2> /dev/null
```

Combining them you got:

```
emacs hello.html 1> /dev/null 2> /dev/null  & disown
```

Which is awful, but you can turn it into a .sh script:

```

#!/bin/sh
$@ 1> /dev/null 2> /dev/null  & disown
```
[/code]

Then just run it:
scriptname.sh emacs file.html

---

### Post by iaw4 on 2012-09-21
thanks for the help.  I went with defining this special for emacs, and using a bash function in .bashrc:

function emacs() { /usr/bin/emacs "$@" 1> /dev/null 2> /dev/null & disown ;}

---

