---
title: "'rm' does not prompt w/o --force option"
date: 2009-01-12
forum: General Help
---

### Post by wookaru on 2009-01-12
When I use 'rm' on my Ubuntu install, I have noticed that it does not prompt me by default to approve each file im deleting. From fedora, I am used to the behavior that unless I specify the --force (-f) option, I am prompted for every file.  

I know I can make it prompt me every time if I use the --interactive (-i) flag, but I want this behavior by default. Is there some setting or environment variable I can change to make 'rm' prompt me on each file delete?

---

### Post by squaregoldfish on 2009-01-12
Assuming you're using bash as your shell (it's the default in Ubuntu), you can set up an alias to redirect the rm command.

Edit the .bashrc file in your home directory, and add the following line:

alias rm='rm -i'

Now, whenever you open a new terminal session, all calls to rm will be altered to be rm -i

HTH,
Steve.

---

### Post by wookaru on 2009-01-12
Thanks for the idea Steve. I am using bash, so I might do that. 

I would still like to know why I am not getting prompted though. According to the man page, rm should always be interactive, unless you use the --force option. I wonder why the default behavior being changed...

---

### Post by squaregoldfish on 2009-01-12
I must say I've never known the rm command to be interactive by default. Using my powers of idle speculation, I suspect that most people find it annoying, so by convention it's now set for non-interactive mode by default. Maybe the man page has never been updated.

---

