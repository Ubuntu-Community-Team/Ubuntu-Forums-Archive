---
title: "gksudo prompt"
date: 2007-02-25
forum: Desktop Environments
---

### Post by Patrick-Ruff on 2007-02-25
hey all, I was wondering if there was any way to make the gksudo prompt not make the rest of your screen grey and unusable, it reminds me too much of vista. I'd rather use the whole OSX concept as  far as that goes.

thanks to those who reply.

---

### Post by v8YKxgHe on 2007-02-25
I don't think there is, unless you edit the source code for where ever it is ... but I have no idea. Maybe when you're on Vista it should remind you of Ubuntu as Ubuntu had it first :P

---

### Post by Patrick-Ruff on 2007-02-25
look, I don't care about anything vista has.

I mentioned before that I like the OSX concept of requiring premission.   it is NOT a good thing to lock up the entire screen to prompt for sudo privilages, that is not an innovative feature . . .

---

### Post by v8YKxgHe on 2007-02-25
> **Patrick-Ruff said:**
> look, I don't care about anything vista has.

I mentioned before that I like the OSX concept of requiring premission.   it is NOT a good thing to lock up the entire screen to prompt for sudo privilages, that is not an innovative feature . . .

I have no idea how OSX does it, so I can't help.

---

### Post by Patrick-Ruff on 2007-02-25
OSX has a small prompt that forms at the top of the window for the requesting application, it doesn't grey out your screen or require you answer it before you can do anything else on your system. 

it looks like [this]("http://www.more.net/technical/mac/images/osxauthenticate.jpg").

---

### Post by ardchoille42 on 2007-02-26
> **Patrick-Ruff said:**
> hey all, I was wondering if there was any way to make the gksudo prompt not make the rest of your screen grey and unusable, it reminds me too much of vista. I'd rather use the whole OSX concept as  far as that goes.

thanks to those who reply.

That's actually a safety feature. Making the screen dim and grabbing the keyboard input is preventing other apps from "listening" to keyboard input events, thus making it possible to shield from malicious applications which may be running.

---

### Post by 23meg on 2007-02-26
There's a practical way, it's just in somewhere people rightly don't think of looking; check this out:

[http://www.ubuntuforums.org/showthread.php?t=326017](http://www.ubuntuforums.org/showthread.php?t=326017)

---

### Post by bobosity on 2007-02-26
This may work for you though it seems to be just as annoying:

gksudo -P <command>

---

