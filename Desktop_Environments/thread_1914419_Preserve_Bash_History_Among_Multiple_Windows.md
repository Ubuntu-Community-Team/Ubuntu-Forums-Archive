---
title: "Preserve Bash History Among Multiple Windows?"
date: 2012-01-24
forum: Desktop Environments
---

### Post by user2037 on 2012-01-24
When opening multiple windows it seems the last window's latest Bash history appears first when scrolling back through commands with the up arrow. Is it possible to configure Bash and/or Gnome-terminal to mix the recent histories among all the windows (based on input time of the commands)?

---

### Post by erind on 2012-01-24
Add these lines to **.bashrc **file in the home directory, if not already there: 

```
shopt -s histappend 
PROMPT_COMMAND="history -a" 
```There's some good info in this link as well:

[http://groups.google.com/group/comp.unix.shell/browse_thread/thread/90dc883275884edf/d5f01367bd7ccc52?lnk=gst&q=+Bash+History#d5f01367bd7ccc52](http://groups.google.com/group/comp.unix.shell/browse_thread/thread/90dc883275884edf/d5f01367bd7ccc52?lnk=gst&q=+Bash+History#d5f01367bd7ccc52)

---

