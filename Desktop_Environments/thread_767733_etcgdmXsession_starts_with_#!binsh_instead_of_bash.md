---
title: "/etc/gdm/Xsession starts with #!/bin/sh instead of bash"
date: 2008-04-25
forum: Desktop Environments
---

### Post by drjimmy42 on 2008-04-25
Every time I upgrade Ubuntu I log into my desktop and get that "Your session lasted less than 10 seconds" message and its always because of a parse error in my ~/.bashrc file where it chokes on a ( or something.  

The answer is to change the first line of /etc/gdm/Xsession from 

```
#!/bin/sh
```

to

```
#!/bin/bash
```

So that the functions and other fun bash stuff in my .bashrc file can be parsed. 

Why don't more people complain about hitting this? Does the entire Ubuntu community have a boring posix sh .bashrc file or do they all know this trick?

---

### Post by Koroviev on 2008-04-26
In Ubuntu, /bin/sh points to dash. If your script requires bash, then it should start with /bin/bash. It is well documented: [https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh).

---

### Post by drjimmy42 on 2008-04-26
Thanks for the pointer, that was a great explanation. 

In do understand that for all of the other startup scripts, but it seems an odd choice for Xsession which is trying to read in the users .bashrc file, a bash specific file.  Even if all the other scripts use sh -> dash, that would would seem to be a good choice for bash.  

Ah well, mystery solved.  Thanks a lot.

---

