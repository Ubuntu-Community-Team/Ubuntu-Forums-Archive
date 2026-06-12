---
title: "Matlab license manager"
date: 2010-03-24
forum: Education &amp; Science
---

### Post by cpgos on 2010-03-24
Is it possible to run a program as another user, something similar to the Windows facility "Run as"?

The reason that I think I need to do this is that I can get the Matlab license manager to work only when I am logged in as the user that I originally used to install Matlab. If I log in as
a different user I cannot get the license manager to start.

However, if I log in as the original user, start the license manager and then change to a different user I can then start Matlab as normal.

The solution that I think might work would be to run the license manager as the original user and then to continue with Matlab itself as a different user.

Best regards,
cpgos

---

### Post by gunksta on 2010-03-24
Open a terminal and enter

```
su $user_name $program_name
```

It will ask you for that user's password.

---

### Post by cpgos on 2010-03-24
Thank you for your response.

I have done as you suggest and Matlab now works as required.

Best regards,
cpgos

---

