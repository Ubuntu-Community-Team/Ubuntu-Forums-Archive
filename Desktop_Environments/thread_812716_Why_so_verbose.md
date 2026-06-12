---
title: "Why so verbose?"
date: 2008-05-30
forum: Desktop Environments
---

### Post by figgles on 2008-05-30
I notice that, from the terminal where I launch a kde app, like kdiff3, spills an endless stream of information related to kdiff3 running. That's all nice but quite a lot of it is merely info or warnings, not worth looking at. 

How do I turn that noise off?

---

### Post by joninkrakow on 2008-05-30
> **figgles said:**
> I notice that, from the terminal where I launch a kde app, like kdiff3, spills an endless stream of information related to kdiff3 running. That's all nice but quite a lot of it is merely info or warnings, not worth looking at. 

How do I turn that noise off?

I can think of a couple things to do.

First is to send the output to /dev/null:
```

kdiff3 >/dev/null

```

Second is to throw the ampersand after it, which will give you back your command line, too. However, don't close your terminal, because that will kill kdiff3:

```

kdiff3 &

```

Now, there may be unintended consequences from doing either of these. I wouldn't know. I only know that these work for me. :-)

-Jon

---

### Post by figgles on 2008-05-30
> **joninkrakow said:**
> I can think of a couple things to do.

```

kdiff3 >/dev/null

```

```

kdiff3 &

```
-Jon

Jon; much thanks. Neither do the trick. Frustrating with the ampersand, too, which is what I usually do anyhow. /dev/null; same problem. What's the command in zsh to pipe both standard out and sterr to /dev/null? 

But I'm wondering if this isn't a KDE setting I can change?

---

### Post by figgles on 2008-05-30
Feh; kdiff3 2>&1 /dev/null doesn't stop it, either

---

### Post by sdennie on 2008-05-30
I don't know how to redirect STDOUT and STDERR to null with zsh but, in, bash, I believe it is:

```

some_program > /dev/null 2>&1

```

---

### Post by figgles on 2008-05-30
I just checked man zshall; zsh supports 2>&1 and a shorthand |& version. Neither helped stop the terminal logorrhea. Thanks, though!

---

### Post by sdennie on 2008-05-30
That's quite odd.  Another thing you could try would be to start the process with nohup (and possibly redirect it to null).

```

nohup some_program > /dev/null

```

I don't know if that will do you any better though.  If you aren't already aware, it won't stop the process when the parent shell exits.

---

### Post by figgles on 2008-05-30
Fascinating -- you guys are good. nohup kdiff3 > /dev/null & works great. If I don't redirect, I'll get a nohup.out file in the current directory.

So, I'm guessing that nohup 'pushes' the output to background; it's still being written, I just don't see it.

Best regards and thanks!

---

### Post by sdennie on 2008-05-30
I'm glad that worked.  My next recommendation was to do a:

```

echo "shutup" > /proc/kde

```

;)

---

### Post by joninkrakow on 2008-05-30
> **figgles said:**
> Jon; much thanks. Neither do the trick. Frustrating with the ampersand, too, which is what I usually do anyhow. /dev/null; same problem. What's the command in zsh to pipe both standard out and sterr to /dev/null? 

But I'm wondering if this isn't a KDE setting I can change?

Weird... because I tried it on my own computer before I wrote my post. Are you in KDE? I'm using LXDE and bash in xterm, so maybe that makes a difference? Maybe bash alone?

I know there is a way to reduce the verbosity of KDE, but I don't remember how to do it. I was kind of hoping my efforts would be a stop-gap measure until somebody who knows more than I came along to _really_ help.... Sorry!

-Jon

---

### Post by joninkrakow on 2008-05-30
Wow, you guys were fast! While I was composing my reply, you went and solved it! (granted, I had a few interruptions while writing it, but still!)

-Jon

---

### Post by sdennie on 2008-05-30
My:

```

echo "shutup" > /proc/kde

```

Post probably didn't work but, it would be really entertaining if it had.  ;)

---

