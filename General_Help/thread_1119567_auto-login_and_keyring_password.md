---
title: "auto-login and keyring password"
date: 2009-04-08
forum: General Help
---

### Post by tornadof3 on 2009-04-08
So, because I have whole-drive encryption via the alternate CD, I figure autologin is a safe bet (I already have to enter a password at first boot!). Problem is, when I load evolution, the first thing it does is pop up asking for a password to unlock the passwords & encryption keys keyring that stores the passwords for the mail server etc. How can I disable this?

I've read about changing passwords in the Passwords & Encryption Keys dialog box to no avail, and it is set to automatically unlock when the user logs in. With auto login turned off, this all works exactly as I want it to, but with autologin enabled, it clearly doesn't register and so asks for the password again. Any ideas?

---

### Post by mcduck on 2009-04-08
If you want to use autologin, and not  to have to input  the keyring password manually, your only option is to remove the keyring password.

Go to Applications/Accessories/Passwords and Encryption Keys. Then go to edit/Preferences, and on the Password Keyrings-tab select the "login"-keyring, and click "Change Unlock Password"-button. Now type your old keyring password but leave the fields for new password empty and click "Change".

---

### Post by tornadof3 on 2009-04-08
Wow, what an obvious solution - clearly I was too dumb to think of that.

It appears to have worked, thank you very much :p

---

