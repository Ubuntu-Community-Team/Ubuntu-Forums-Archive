---
title: "Empathy Keyring passwords"
date: 2010-07-07
forum: Desktop Environments
---

### Post by chocodum on 2010-07-07
I changed my ubuntu account password recently because my brother was fooling around in it, and now I have to enter my keyring password every time log in because my ubuntu account password is different from my keyring password. I have looked just about everywhere, but I can't find a way to change my keyring password. Does anyone know how?

---

### Post by mcduck on 2010-07-07
Go to Applications/Accessories/Passwords and Encryption Keys. Then right-click on the "Passwords:login"-keyring and select "Change password". Type in the old password and set the new one to same as your login password.

Next time you log in your keyring will unlock automatically again.

..and in the future you might want to create a separate user account for your brother (or really anybody else than you) to use. 

Or use the Guest Session, accessible from the shutdown menu in top right screen corner. The Guest session will create a temporarily user account which gets destroyed when the guest logs out, so it's a great way to let other people securely use your machine without you having to worry about the system's security or them having to worry about their network browsing history or other stuff staying on your computer.

---

### Post by chocodum on 2010-07-08
... He does have his own account, it's just that he wanted to tamper with mine.

---

