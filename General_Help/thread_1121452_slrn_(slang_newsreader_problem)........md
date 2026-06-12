---
title: "slrn (slang newsreader problem)......."
date: 2009-04-10
forum: General Help
---

### Post by abhilashm86 on 2009-04-10
i just set up slrn using in home directory, i just gave my e-mail id, so in order to respond,
when i launch slrn i get errors, i don't have an idea of what errors as i haven't used slrn before.........
abhilash@abhi:~$ slrn -d
slrn 0.9.8.1pl1 [2005-02-17]

Reading startup file /etc/news/slrn.rc.
Reading startup file /home/abhilash/.slrnrc.slrn fatal error:
Unable to find a valid hostname for constructing your e-mail address.
You probably want to specify a hostname in your .slrnrc file.
Please see the "slrn reference manual" for full details.

how to set right these errors?

---

### Post by andrew.46 on 2009-04-12
Hi abhilashm86,

You need to have a few details in your $HOME/.slrnrc file. Somehing similar to the following:
```

set username "abhilashm"
set hostname "abhilashm.invalid"
set realname "abhilashm"
```

I would suggest if you are happy to use '.invalid' in the hostname section you should specify a *real* address using something similar to the following:

```
% Reply to a different but real email address:
set replyto  "abhilashm@gmail.com"
```

This will spare you some grief on some newsgroups where it is frowned upon to use .invalid in this way.

All the best,

Andrew

---

