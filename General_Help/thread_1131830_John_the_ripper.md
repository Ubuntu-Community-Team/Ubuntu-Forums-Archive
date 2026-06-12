---
title: "John the ripper"
date: 2009-04-21
forum: General Help
---

### Post by danuk88 on 2009-04-21
I am trying to use john to crack my password.

My password is 8 characters long and is all upper case letters A-Z

I know you can use the -incremental=alpha command but how can I just scan upper case characters ?

Thanks

Dan

---

### Post by spiderbatdad on 2009-04-21
The john directory should contain a sub-directory called "doc." It has all the info on how to configure john. For example the config file tells you to edit john.conf, and the options file tells you ?U is the character class for uppercase A-Z. So, I'm not sure you can do what you want simply as a command line argument. I could be wrong, but it looks like you either create your own wordlist file with rules, or edit john.conf to do the type of scan you want.

---

### Post by danuk88 on 2009-04-21
Thanks for your response I will have a look at the john.conf file later tonight.

Cheers

Dan

---

