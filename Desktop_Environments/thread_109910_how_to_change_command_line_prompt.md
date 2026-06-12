---
title: "how to change command line prompt ?"
date: 2005-12-29
forum: Desktop Environments
---

### Post by rfruth on 2005-12-29
Using the SET command on my stock Breezy box reveils that my prompt is 
> PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"' how can I change this for good :rolleyes:

---

### Post by cstudent on 2005-12-29
Found this doing a quick Google search:

[http://www.northernjourney.com/opensource/newbies/newb015.html](http://www.northernjourney.com/opensource/newbies/newb015.html)


And just a quote from the page concerning the prompt:

This prompt has three Bash-shell variables set: user name ("genew"); host name ("755cx"); and current working directory ("newbies") minus the full path. This format is configured system wide in the file /etc/bashrc:

      PS1="[\u@\h \W]\\$ "

In the primary command-line prompt string (PS1), the \u indicates user, \h is host and \W is current directory. If you prefer a different command-line prompt, you can change your individual profile by adjusting .bashrc in your home directory or adjusting the /etc/bashrc file to set the string globally for all users. Some system admininstrators prefer to include the entire path, which you can achieve by changing \W to \w (lower case). I personally find that the full pathname gets tiresome once you get deep into a file system so I prefer the Red Hat default. The actual default for Bash without any tweaking is:

      PS1="bash\$"

Which produces the very spare:

      bash$

---

### Post by rfruth on 2005-12-29
Thanks CS, I checked the Wiki but not the web :oops: anyway changed my prompt to a simple  ```
PS1="\w "
``` and all is well :D

---

