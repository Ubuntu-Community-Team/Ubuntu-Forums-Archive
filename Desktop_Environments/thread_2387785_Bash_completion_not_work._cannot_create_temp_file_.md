---
title: "Bash completion not work. cannot create temp file for here-document: Text file busy"
date: 2018-03-23
forum: Desktop Environments
---

### Post by bjmango on 2018-03-23
Ubuntu 16.04

Tab key (bash completion function) does not work in the terminal. Warning looks like: 

```
"bash: cannot create temp file for here-document: [COLOR=#ff0000]Text file busy[/COLOR]"
```

Checked the /etc/bash.bashrc file and it looks good. 
```
# enable bash completion in interactive shells
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi

```

---

### Post by spjackson on 2018-03-23
Welcome to the forums.

Have you done something odd with /tmp such as making it a filesystem that is not native to Linux?

---

