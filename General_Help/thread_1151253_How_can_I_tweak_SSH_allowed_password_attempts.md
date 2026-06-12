---
title: "How can I tweak SSH allowed password attempts?"
date: 2009-05-06
forum: General Help
---

### Post by Vunutus on 2009-05-06
I don't want to disable password authentication because sometimes I need to use it on systems where I don't have key encryption set up (like "oh hey I forgot X file on my home machine let me use your computer"). I realise that this opens me up to brute force attacks, but I'd like to set it up something like this:

Remote clients have three attempts to guess the password (to give me leeway for typos). If they go over that they get banned for a period of oh say 24 hours or so.

I read somewhere that there was a PAM module or something to do this, but I don't remember the name or anything abut it so I can't search. Does anyone have any sort of guides for this?

---

### Post by unutbu on 2009-05-06
Try editing /etc/ssh/sshd_config with
```

LoginGraceTime 24h
MaxAuthTries 3
```

I'm not sure if "24h" is the right syntax. If that does not work (test it!), 
```

LoginGraceTime 1440m 

```
should.

See [http://aymanh.com/tips-to-secure-linux-workstation](http://aymanh.com/tips-to-secure-linux-workstation) and "man sshd_config"

---

