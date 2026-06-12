---
title: "Strange Wildcards in Console"
date: 2005-04-24
forum: Desktop Environments
---

### Post by dafrabbit on 2005-04-24
Recently started learning shell script and did some playing with wildcards tonight. Unless I'm mistaken, shouldn't this command:

ls | grep [a]*

Return all filenames in the directory that begin with a lower case "a"? For some reason it's not. It's returning the full directory list instead. Also,

ls | grep [o,O]*

Should return all filenames in the directory that begin with either a lower or upper case "o" right? It's not, it just sits there for a long time using the CPU until I have to kill it with ctrl-c.

I haven't touched my bashrc at all except to add an Alias command and I can't for the life of me understand this...shouldn't console wildcards be perfect?  :?

---

### Post by cwaldbieser on 2005-04-24
You're patterns are not correct for what you want to match.  to match all file names that start with the letter 'a', try:

```
$ ls | grep '^a.*'
```

The '^' means match the begining of the line.
Next match a lowercase 'a'.
Next, the '.*' construct means match zero or more repetitions of any character.
I enclosed the entire argument in single quotes so the shell wouldn't try to interpret any of the pattern characters as special.  In this case, it may not have been necessary.

Your second example suffers from the same problems as the first.  Ina addition, your character class shouldn't have a comma in it.  Try:

```
$ ls | grep '^[dD].*'
```

Also, just doing a quick '$ man grep' can save you the trouble of having to post your question and then wait for a reply.  I know man pages are somewhat terse, but I have found that a couple minutes study usually is faster than hunting down the local guru.

---

### Post by dafrabbit on 2005-04-24
Hrmm I see, thanks for the quick reply! I didn't think to look in the man pages as I've been following the shell tutorials at: [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php). My bad. Thanks anyways!

---

