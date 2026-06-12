---
title: "Editing config files with a shell script"
date: 2007-10-11
forum: Desktop Environments
---

### Post by dizwell on 2007-10-11
Apologies if this is not the right place: I've tried the programming forum, too, but I doubt this counts as programming! 

I have a configuration file which already contains some lines of data. Suppose it looks like this:

Command1
Command2
Command3
End-of-file

I can write a shell script that does this:
cat >> /etc/config << EOF
Command4
Command5
EOF

...and when I run the shell script, it appends its two lines to the original file, so it ends up looking like this:

Command1
Command2
Command3
End-of-file
Command4
Command5

But what I actually need it to do is to insert the new lines before the line which says End-of-File so that I end up with:

Command1
Command2
Command3
Command4
Command5
End-of-file

Is there a relatively easy way of doing this, please? I've generalised the example because I need to use this technique in several different places. But it is always the last line of the config file that I need to insert stuff before.

Any tips, pointers or code snippets gratefully received!

---

### Post by milosz.galazka on 2007-10-11
What about using temporary file?

```
cat /etc/config | sed /End-of-file/d > /tmp/config.wrk
```

Put new commands in config.wrk. 
Put  "End-of-line" after inserted commands.
Replace /etc/config file.

There is a command *tempfile* that will help creating unique temporary file name.
```
$ tempfile
/tmp/file7C6I6u

```

---

### Post by dizwell on 2007-10-11
Thank you so much. That works a treat (and my first dabbling with sed!), and it's nice and simple -easy to read, so anyone following me can make sense of it.

Thanks a lot.

---

### Post by milosz.galazka on 2007-10-11
Writing scripts is very fun :) I see that you enjoy it too :)

---

