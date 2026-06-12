---
title: "gnome-terminal character encoding?"
date: 2009-05-18
forum: Desktop Environments
---

### Post by orsenthil on 2009-05-18
This a problem I am facing after upgrade to Ubuntu 9.04;
I have in my bashrc, the following


export PS1="[\[\033[1;34m\w\[\033[0m]\n[\t \u]$"

It shows time; and the current directory above my prompt.
But I am facing an encoding issue now.
It shows a Square at the end now.

export LANG=en_IN.UTF-8
gnome-terminal --disable-factory does not solve this problem.

How do I set encoding in the gnome-terminal?

---

### Post by orsenthil on 2009-05-18
Well, to simply my problem;
export PS1="[\033]" 
\033 is a special character in BASH. It takes the cursor up.
Now, I don't know what has happened that it is displaying it as [.0]  (Invalid character without the knowledge of encoding). 

I have set the encoding to en_IN.UTF-8; but does not help.
The problem does not occur in xterm.

---

### Post by loomsen on 2009-05-18
You seem to be missing an escape character there. A screenshot would clearly clarify what you want and what you have tho...

export PS1="[\[\033[1;34m\w\[\033[0m]\n[\t \u]$"

Well, maybe even more than one ^^
\[\033[1;34m

There for instance, 
another one there:
[0m[color=red]\[/color]]

Post a shot, it will be easier to see what you want and what you have.
You might want to define functions for your colors too.

Thats mine:
[[img]http://www.ubuntu-pics.de/thumb/14580/shot_076__hEMSON.png[/img]](http://www.ubuntu-pics.de/bild/14580/shot_076__hEMSON.png)

```

## Set some fancy reasonable prompt
WHITE="\[\033[37;0m\]"
RED="\[\033[0;31m\]"
FONTCOLOR="$WHITE"
USERCOLOR="$RED"
export PS1="$USERCOLOR\u@\H$FONTCOLOR        \$(date +%d).\$(date +%m).   \$(date +%I:%M%P) \
\n$USERCOLOR\$(truncpwd) $FONTCOLOR$ "

```

Another example, depending on the exit status of your last command, if it exits 0 you get a smiley, any other exit a frowny:
```
export PS1="\`if [ \$? = 0 ]; then echo \\\^\\\_\\\^; else echo \\\-\\\_\\\-; fi\`*\u \w:\h$ "
```

[[img]http://www.ubuntu-pics.de/thumb/14581/shot_077__31tmhV.png[/img]](http://www.ubuntu-pics.de/bild/14581/shot_077__31tmhV.png)

*edit*
[Check this](http://slashdot.org/comments.pl?sid=108424&cid=9219400)

---

