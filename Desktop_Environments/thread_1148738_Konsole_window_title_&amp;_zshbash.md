---
title: "Konsole window title &amp; zsh/bash"
date: 2009-05-04
forum: Desktop Environments
---

### Post by Holy Cheater on 2009-05-04
I have a problem with console. It doesn't update window caption.

I have a couple of functions defined in zshrc (bash does its magic out of the box)
```

precmd() { print -Pn "\e]0;%~\a" }                        
preexec() { print -Pn "\e]0;$1\a" }

```
This works in xterm: it shows current directory or command being executed in window title.
Konsole ignores this and only updates caption to the currently running program with a big delay (so most time i see "zsh") and it doesn't matter if I have these functions defined in zsh or not.

I wonder if there's a way to fix this behaviour?

---

