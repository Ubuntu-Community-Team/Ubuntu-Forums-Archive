---
title: "Simple little script doesnt work"
date: 2006-03-31
forum: Desktop Environments
---

### Post by christhemonkey on 2006-03-31
I have written a simple little bash script so that i can enable 3D with my nvidia card on startup.  Unfortunately it doesnt work.

As i have 2 different kernels one of them doesnt work with the nvidia driver so i use the nv driver.
But i got annoyed at switching them round manually so decided to *try* and automate it.
It always says "just using the computer", which leaves me with no Xserver if i am in my multimedia kernel.
I have added it to the appropriate run levels to run on startup for if it does decide to work.

Any help/ideas why it doesnt work?

```

#! /bin/sh
#
set -e
DESC="checkxserver"
NAME=xorgsetup
SCRIPTNAME=/etc/init.d/$NAME
UU='uname -r'

if UU="*multimedia"
then cp /etc/X11/xorg.conf.music /etc/X11/xorg.conf
echo ""Music editing i see..."
else cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
echo "Just using the computer"
fi

exit 0


```

---

### Post by kabus on 2006-03-31
That if statement doesn't do what you intend it to do.
Use something like :

```
if uname -r | grep -q 'multimedia'; then
...
else
...
fi
```

---

### Post by christhemonkey on 2006-03-31
Cheers will try that now.

---

### Post by christhemonkey on 2006-03-31
That worked perfectly thankyou very much!

Would it be possible to explain why it wasnt working?

---

### Post by kabus on 2006-03-31
Basically you have to put a test command that returns either true or false after the if. You put a variable assigment there which returns nothing at all. 
(to the best of my knowledge, I'm far from being an expert myself.)

This site here explains it a lot better than I can :

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)

---

### Post by christhemonkey on 2006-03-31
Cheers very much.
That explained perfectly.

---

