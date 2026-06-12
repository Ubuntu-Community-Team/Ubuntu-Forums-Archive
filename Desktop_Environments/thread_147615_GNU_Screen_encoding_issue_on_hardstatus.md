---
title: "GNU Screen encoding issue on hardstatus"
date: 2006-03-20
forum: Desktop Environments
---

### Post by engla on 2006-03-20
Hey there.
I really like GNU Screen, it's the coolest commandline tool of them all, and I use it a lot.

I have one nagging issue with encodings though, a minor one. The "content" encoding works fine (utf8 ), I can type and read as I want in irssi, emacs and the shell, but:
My hardstatus line looks like this:

```
hardstatus alwayslastline "%{+r} %-w%{+bu I}%n-%t%{-}%+w %= %{+ b}| %D %d %LM, %{+b I}%c "
```
It gives me a nice list of open windows, highlights the current one, and shows the **date and time **in the right corner. However, the date and weekday is localized, and sadly all the days with scandinavian letters in their names come out in the wrong encoding. Today, on a monday it says "0 bash  1-bash                                           |** mÃ¥n 20 mars**, 21:05";  mÃ¥n should really be "mån" [for måndag]

I can't seem to get the hang of this, there is no way to change this encoding:
It doesn't matter if I run screen or screen -U (unicode)
changing utf8 on|off and/or defutf8 on|off doesn't affect this.

So basically, I want to solve that; either by fixing the encoding issue, or forcing screen to display day names in english

---

### Post by colo on 2006-03-20
I'm pretty sure you could acchieve the latter by starting screen in a shell with your locale set to en_US, and having screen's subshells sourcing a file reverting the locale to your local, nordic one.

---

### Post by engla on 2006-03-20
[QUOTE=colo]I'm pretty sure you could acchieve the latter by starting screen in a shell with your locale set to en_US, and having screen's subshells sourcing a file reverting the locale to your local, nordic one.[/QUOTE]
Ooh that actually works. Thanks! I already have some aliases, this is what I had to do:
modify
alias sc=screen
to
alias sc="LANG=en_US screen"

and then add
setenv LANG sv_SE.UTF-8
in .screenrc

It's the boring solution though, but it doesn't matter much since the rest of screen's interface is not localized.

---

