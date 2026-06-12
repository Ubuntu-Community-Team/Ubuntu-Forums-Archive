---
title: "Possible to execute pwd in bash terminal once when it idles for more than X seconds?"
date: 2008-12-27
forum: General Help
---

### Post by tnek on 2008-12-27
I like my prompt to be just a simple $ sign, as I find a prompt which includes my current working directory often becomes too long. When I'm actively working in a terminal I usually remember which directory I'm in anyway.

It works fine having a $ symbol for prompt as long as I don't switch between too many terminals. To make things a bit easier it would be nice if I could have pwd execute once after a certain time of idling (a certain time when no command has been executed and no commend is executing).

Is it possible using bash? Any tips?

PS. I don't want to use a multi line prompt, I just want a $ .DS

---

### Post by dagnabit dang doohickey on 2008-12-27
This will echo PWD if the interval between subsequent commands exceeds ten minutes.
```

PROMPT_COMMAND="${PROMPT_COMMAND}; "'(( $SECONDS > 600 )) && echo "PWD: $PWD"; SECONDS=0'

```

---

### Post by tnek on 2009-01-15
Thanks and nice idea, but it's not what I was looking for. I want to execute a command after X minutes if no one touches the command prompt. The very best would be if I could poll the current command line and see if something has been written but not yet executed. I don't think bash allows that kind of low lever interaction/hooking. But if there is a solution, I'm very interested in finding it. :-)

---

