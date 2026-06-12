---
title: "Custom keyboard shortcut environment has different SSH_AUTH_SOCK than launcher"
date: 2010-12-15
forum: Desktop Environments
---

### Post by skarab13 on 2010-12-15
Hello,

If I launch "Terminal" from the Main Menu under Accessories, the environment includes the correct SSH_AUTH_SOCK variable:

```
declare -x SSH_AUTH_SOCK="/tmp/keyring-M9jm0W/ssh"
```

The same is true if I launch a terminal from the default keyboard shortcut ("Run a terminal").  However, if I create a custom keyboard shortcut (System->Preferences->Keyboard Shortcuts) which simply executes 'gnome-terminal' the SSH_AUTH_SOCK variable is quite different:

```
declare -x SSH_AUTH_SOCK="/tmp/ssh-QmxIEa1830/agent.1830"
```

This causes my shortcut to ssh to a remote host to prompt for a passphrase (thus defeating the purpose of gnome-keyring in this case).

Any ideas?

Thanks!

---

### Post by sensille on 2011-04-03
I ran into the same problem. Have you been able to solve it?

---

### Post by alan-74 on 2011-05-08
> **sensille said:**
> I ran into the same problem. Have you been able to solve it?

I solved this by adding the following line to my .bash_profile:

```

SSH_AUTH_SOCK=`netstat -xl | grep -o '/tmp/keyring-.*/ssh$'`
[ -z "$SSH_AUTH_SOCK" ] || export SSH_AUTH_SOCK
```

---

