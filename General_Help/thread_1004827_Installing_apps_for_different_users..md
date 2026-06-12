---
title: "Installing apps for different users."
date: 2008-12-07
forum: General Help
---

### Post by Grolsche on 2008-12-07
Hi,

I want to install an application on my user. If I install it on my user will it also be accessible to my wife who has a user on the same comp? 

If it does, how do I install it so it is only on mine?

---

### Post by snova on 2008-12-07
Applications are installed globally.

Through the package manager, there is no way that I know of (I doubt there is a way at all) to install to a home directory.

The only method I can think of is to build it from source...

---

### Post by aysiu on 2008-12-07
What's the application? You might be able to modify the launcher for it so that it's owned by you and executable by only you.

---

### Post by Grolsche on 2008-12-14
I want to install apache and php, but only provide access to me.

---

### Post by adaptr on 2008-12-14
Apache is a web server, and hence a system service.
Normal users cannot start or stop or generally influence system services.
PHP is a scripting language, and as such there is nothing inherently good or bad about being able to "access" it.
As long as your wife does not have sudo permission, she cannot influence these services.

---

