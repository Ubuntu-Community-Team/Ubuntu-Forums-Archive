---
title: "Screen Resolution"
date: 2009-02-13
forum: General Help
---

### Post by Diverted Income on 2009-02-13
I need to change the screen resolution for a specific user. I can use another user and run terminal to change it but how do I change it for a specific user from another user account?

---

### Post by Bladeforger on 2009-02-13
I'm kind of a newbie, so bear with me...

in terminal, "su" means switch user.  So, if you have another user, you can switch to that user and you can switch to that user with his invironment.  Example: other user is jake.
```

su jake

```This switches to the other user.
```
su -1 jake

```This switches you to jake and gives you his environment variables.  Do what you need to do and then switch back to yourself and your environment.

Anytime you're in doubt about who you are, type "whoami".

Hope this helps.

---

### Post by Diverted Income on 2009-02-13
I'll give it a try. Thanks!

---

