---
title: "Installed with passwordless account, how to do updates?"
date: 2009-03-19
forum: General Help
---

### Post by riahmatic on 2009-03-19
I installed Intrepid with a passwordless account, but when you try to do updates it asks for a password!

Is there a way around this? It would be strange to allow installing with such an account if there's no way to administer the system.

Thanks

---

### Post by mcla0203 on 2009-03-19
If there is really no password, then just don't type anything and push enter?

---

### Post by kryptikos on 2009-03-19
What do you mean by passwordless account? A user has a password set up at creation when you install. Are you meaning to say you have auto-login enabled so it doesn't prompt you when the box boots up? If it is auto-login the password would be the same one you entered when the install created the hostname and user account.

---

### Post by Therion on 2009-03-19
How were you able to get past the Administrator Password section of the install without entering anything?  
I didn't think the installer would let you continue without setting up a password for sudo...

Anyway, assuming it's possible... Open a Terminal and: ```
passwd
```
And follow the prompts.  This is how you would go about changing your own password, so I'm hoping this will work.  Not sure what else to suggest.

---

### Post by riahmatic on 2009-03-20
Okay, so there actually was a password used during installation which I totally forgot about. Wow, I feel like such a nub. I reinstalled, but curious, is there a way to reset passwords without knowing the admin? I tried for a friend once, using the install CD and a special boot param, but no luck.

---

