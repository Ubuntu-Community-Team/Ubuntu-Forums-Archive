---
title: "Syntax error near unexpected token &quot;fi&quot; in my 6 line bash script"
date: 2009-01-20
forum: General Help
---

### Post by The Notorious VLG on 2009-01-20
Understandable since this is the first script of this sort that I've ever written. This script is supposed to run a program that I've just written in C to manage/update the playlist for my radio show in an HTML file. After updating the playlist, unless the init argument was used (to set up the page), it should run scp to publish the page to my webspace.

Here's the code:

```
#!/bin/bash
./playlist $@
if [ "$1" != "init" ]
scp CC/* user@host.edu:~/www
fi
exit 0
```

What's producing this error? By the way, I'm expecting to have to enter my password for scp every time I run the script. Also, it's just now becoming clear to me that copying all of the files in that directory might be unnecessary (though it doesn't matter much since there's not much there yet).

---

### Post by heindsight on 2009-01-20
the syntax of your if statement is wrong. the correct syntax would be:

```
if [ "$1" != "init" ]; then
    scp CC/* user@host.edu:~/www
fi

```

---

