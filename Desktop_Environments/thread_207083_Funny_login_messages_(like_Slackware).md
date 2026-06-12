---
title: "Funny login messages (like Slackware) ?"
date: 2006-07-01
forum: Desktop Environments
---

### Post by miuen4o on 2006-07-01
Many of you have tried Slackware. You know at login there are funny messages. Sometimes they're not so funny, but there are definitely spot-ons sometimes. I wanted to ask. Is there such a package for ubuntu?? Thanks in advance!

---

### Post by matthew on 2006-07-01
It sounds like you are talking about "fortune." If so, this is how you would install it.

sudo apt-get install fortune

To test, type "fortune" at the command line. If it is what you are looking for, you can make it print a saying each time you open a terminal by adding this to the end of your /etc/bash.bashrc file
```
# just for fun, fortune at bash startup
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
fortune

```
I like to go a step further and add the "cowsay" program (sudo apt-get install cowsay) and then have a cow say whatever the fortune is.

To test: at a command prompt type fortune | cowsay

To make it come up every time you start a terminal add this to the end of /etc/bash.bashrc
```
# just for fun, for cowsay & fortune at bash startup
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
fortune | cowsay

```

---

### Post by miuen4o on 2006-07-01
Thanks, mate. It's exactly fortune. I'll give it a go when I go home later.

---

