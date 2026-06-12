---
title: "SHIFT + BACKSPACE in new compiz"
date: 2006-09-12
forum: Desktop Environments
---

### Post by royg1234 on 2006-09-12
I'm getting really pissed off at the "feature" that restarts gnome when you hit SHIFT + BACKSPACE.  It happened to me while I was writing thist post.  :mad: 

Anyone know how to change this to the more sensible CTRL + ALT + BACKSPACE?

---

### Post by _simon_ on 2006-09-12
stick this in an executable file in /usr/local/bin then place it in session startup

```

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

```

That will stop shift + backpace from restarting.

ctrl alt backspace will work anyway.

---

### Post by Dinerty on 2006-09-12
> **_simon_ said:**
> stick this in an executable file in /usr/local/bin then place it in session startup

```

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

```

That will stop shift + backpace from restarting.

ctrl alt backspace will work anyway.

Works a treat, finally got round to adding it, thanks !

---

### Post by jacrider on 2006-09-13
I see what you are tying to do ... and it makes sense.

Two questions ... because I need to do the same thing.

First, how do I put the command in an executable file.  Sorry for the simple question.

Secondly, couldn't I just put the command in one of the start-up sessions?

Many thanks as the restart drives me crazy.  I would love to get this fixed.

---

### Post by arsenic23 on 2006-09-14
Why not just add it to the script you use to start compiz ?

Mine looks like this:

```
#!/bin/bash
if ps -A | grep -e "compiz.real$" > /dev/null; then
        killall cgwd
        metacity --replace &
else
        cgwd &
        compiz-start --replace &
        xmodmap -e "keycode 22 = BackSpace Delete"
fi
```

---

### Post by PhilippHD on 2006-09-15
Will it work, if I add the additional line right behind the last "fi" ?

Also, which of these lines will work ?
[LIST][*]xmodmap -e "keycode 22 = BackSpace"
[*]xmodmap -e "keycode 22 = BackSpace Delete"
[*]xmodmap -e "keycode 22 = BackSpace BackSpace TerminateServer"
[/LIST]

Will it make a difference that I use german keyboard-layout ?

---

### Post by PhilippHD on 2006-09-16
Here's what I did:
I added all of the 3 lines above at the end of the compiz-start script. Everything worked fine. After the recent compiz-update I had a look at the compiz-start file again.
It was completely changed. The lines I added were gone again. Now it looks like this:
> 
#!/bin/bash

if [ -f /usr/bin/cgwd ]
then
    cgwd --replace > ~/.cgwd.log 2>&1 &
    disown %1
else
    gnome-window-decorator --replace > ~/.gwd.log 2>&1 &
    disown %1
fi

compiz > ~/.compiz.log 2>&1 &
disown %1


---

