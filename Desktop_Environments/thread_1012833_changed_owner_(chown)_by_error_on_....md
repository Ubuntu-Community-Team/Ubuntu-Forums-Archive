---
title: "changed owner (chown) by error on /..."
date: 2008-12-16
forum: Desktop Environments
---

### Post by maraja on 2008-12-16
Hi,

I made a big mistake this morning and executed the following command:

sudo chown maraja /

(or something similar I now forgot)

the result is obviously having most of the files located outside my home owned by my user. I say most of them as the command was blocked while running.

I then looked around and found out that it is possible to get a list of all files with a particular owner and/or group, example:

```
find / -user maraja ! -group maraja
```

gaves me a list of all (I hope) files that were changed my my wrong command.

I then tried to restore the proper owner with a serie of commands like:

```
sudo find / -user maraja -group root -exec chown root {} \;
```

My issue is that it is now impossible to connect to the internet as I guess there is some more files that need to be fixed...

Is there anyone able to help me or I do need to reinstall Ubuntu from scratch?
thank a lot in advance,

---

