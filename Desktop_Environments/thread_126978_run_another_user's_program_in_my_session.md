---
title: "run another user's program in my session"
date: 2006-02-07
forum: Desktop Environments
---

### Post by towsonu2003 on 2006-02-07
In windows, I believe you do "run as". How do u do it in gnome?

I want to run firefox 1.5.0.1 (just untarred to the user's home) as another user (myself). This is what I do in my own gnome session from the terminal: 
(*user1* is me, *user2* is the other user)
```

user1@UBUNTU:~$ su user2
Password:
user2@UBUNTU:/home/user1$ cd
user2@UBUNTU:~$ cd firefox
user2@UBUNTU:~/firefox$ ./firefox
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:9770): Gtk-WARNING **: cannot open display:
user2@UBUNTU:~/firefox$

```
It seems I need to tell the X server something (*temporary* to allow this, but what?? any how-tos, pointers appreciated... this should be easy? is it?

---

### Post by towsonu2003 on 2006-02-18
bump -any pointers? anything? pls

---

### Post by cwaldbieser on 2006-02-18
[QUOTE=towsonu2003]bump -any pointers? anything? pls[/QUOTE]
You could try using xhost.  I am not sure it will work, but it is supposed to let you tell X what users or hosts are allowed.

---

### Post by towsonu2003 on 2006-02-18
hey thanks! great pointer. I found a script by searching howto xhost, and now I'm using firefox using my sandbox user! I have no idea whether this is more secure, but it sure feels weird! 

I got the script here:
[http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html](http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html)

And the script is:
```

#!/bin/sh
# usage is: chmod +x script than ./xsu deneme 'firefox &'

if [ $# -lt 2 ]
then echo "usage: `basename $0` clientuser command" >&2
     exit 2
fi

CLIENTUSER="$1"
shift

# FD 4 becomes stdin too
exec 4>&0

xauth list "$DISPLAY" | sed -e 's/^/add /' | {

    # FD 3 becomes xauth output
    # FD 0 becomes stdin again
    # FD 4 is closed
    exec 3>&0 0>&4 4>&-

    exec su - "$CLIENTUSER" -c \
         "xauth -q <&3
          exec env DISPLAY='$DISPLAY' "'"$SHELL"'" -c '$*' 3>&-"

}

```

for anyone interested. also, if anyone has any ideas about how secure this is, let me know ;)

---

### Post by graingert on 2008-01-31
did you Try the package sux it works very well!

sudo apt-get install sux

then use "sux user" as you would use su

---

