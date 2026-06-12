---
title: "unsetting histfilesize in bashrc is ignored?"
date: 2009-02-09
forum: General Help
---

### Post by Patsoe on 2009-02-09
Hi all, 

I'm on Ubuntu 8.04 (amd64), and trying hard to stop my bash histfile from getting truncated. I have a plain vanilla .bashrc (ie whatever is created in a fresh user account) other than the following three added bits (diff output):

```
=== modified file '.bashrc'
--- .bashrc	2009-02-09 22:50:27 +0000
+++ .bashrc	2009-02-09 22:58:01 +0000
@@ -91,3 +91,8 @@
 if [ -f /etc/bash_completion ]; then
     . /etc/bash_completion
 fi
+
+# no histfile truncating and store timestamps
+export HISTTIMEFORMAT='%c$ '
+shopt -s histappend
+unset HISTFILESIZE

```

Now when I open a new terminal:
```
user@host:~$ echo $HISTFILESIZE 
500

```

...?? What am I doing wrong? Indeed, .bash_history gets truncated (I had it line-counted with wc -l) as if I didn't unset $HISTFILESIZE. 

I know that .bashrc does get read, seeing that when I invoke 'history', this obeys the $HISTTIMEFORMAT setting properly.

Is this a bug perhaps?
Thanks for thinking with me...

edit: oh yes, forgot to mention why I'm doing it this way. From the man page bash(1): "If HISTFILESIZE is not set, no truncation is performed." Also, the unset trick works on my Red Hat 5.3 machine at work...

---

