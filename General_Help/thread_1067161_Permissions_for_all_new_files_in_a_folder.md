---
title: "Permissions for all new files in a folder"
date: 2009-02-11
forum: General Help
---

### Post by cOmOneO on 2009-02-11
Hi
I am sure that this is either not possible or very obvious, but can I set do something to a folder so that all new files (even created as by root) will have a certain set of permissions? 

The reason I am asking is that, I have just installed an app that uses Rails, and somewhere, one part of the app is being run as root. When it runs, it writes to the log. If the log is old enough it creates a new one (every part of the app does this), but if this one part creates the log, it is created by root and with only read access for anyone but root.

But I think that just because its the default way when root creates a file.

I have been trying to figure out what part is running as root, but with no luck since it is not running all the time. And I have no idea what triggers it.
But if there is some way to make all new files in a folder, writeable to all, then it would solve it.

Or maybe a way to monitor a folder to see when the owner of a file changes. That way it should be clear from the log itself, what part is being run as root.

Many thanks in advance

---

### Post by geirha on 2009-02-11
It may be logrotate that is rotating the log, and if that is the case you can tell it to create the log file with a certain ownership and permission. Look inside /etc/logrotate.d/ and see if there are any files relating to rails.

logrotate's manual page explains the syntax of the file:
```
man logrotate
```

---

### Post by cOmOneO on 2009-02-11
geirha:
Unfortunately there was no file in the folder /etc/logrotate.d/ that contained any reference to the folder where I have a problem, so I assume that it is not handled by logrotate, but by the app itself.

But a good suggestion none the less... I didn't know that there was a central service to handle such a thing, and I now have another thing to check, next time I run in to some logrotation-trouble, to thx :)

---

### Post by geirha on 2009-02-12
Searching for "rails logrotate" on google shows many pages explaining how to set up logrotating with either logrotate or rails itself. Might give you a clue on where to look for rails's logrotating configuration.

---

### Post by cOmOneO on 2009-02-21
Hi, I found a way to solve the problem. Just thought I would put it here for others to find.

I simply altered the umask for the folder.

The folder contains nothing but logs... so it should be okay.

This only work because the process does not create the files with a specific permission set, but instead uses the deafult (a note for anyone else reading this)

Thanks for the help anyway.

PS: Should I mark this as solved? Looked for the button to do so, but didn't find it.

---

