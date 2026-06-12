---
title: "Alias with '"
date: 2009-02-19
forum: General Help
---

### Post by cdmike2k8 on 2009-02-19
I am trying to create an alias for a rsync command that uses the -e flag.  So far, I have 
```

alias serveget='rsync --partial -e 'ssh -p 1337''

```
and it doesn't work because it interprets the ' in -e 'ssh -p... as the end to the alias.  Is there a different way to enter the ' in the -e flag so that alias does not end the alias?  Also, is there a way to reload this file without logging out and back in?
Thanks

---

### Post by jocko on 2009-02-19
I can't help you with the main problem, but to reload .bashrc without logging out, run this:
```
source .bashrc
```

---

### Post by mikewu on 2009-02-19
You might want to try making one set of quotes double quotes(") and the other ones single quotes. 

If that doesn't work try escaping the quotes with a backslash(\).

Also, you don't need to make the alias in the .bashrc file. You can just type the alias into the command line and play around with it. Then once you have it working, put it in the .bashrc.

---

### Post by cdmike2k8 on 2009-02-19
Great, I got it to work.  Double quotes did it.  Thanks to both of you!

---

