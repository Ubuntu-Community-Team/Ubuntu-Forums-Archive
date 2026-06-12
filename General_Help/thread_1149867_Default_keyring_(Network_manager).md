---
title: "Default keyring (Network manager)"
date: 2009-05-05
forum: General Help
---

### Post by Grynch108 on 2009-05-05
Hi,

When I boot up into Ubuntu I get this message which prompts me for my password.

"The application 'NetworkManager Applet' (usr/bin/nm-applet) wants access to the default keyring, but it is locked."

When I enter the password, it then connects to my network. Is there anyway to get it to remember my password so that I don't have to enter it everytime I log in or boot up?

Cheers.

---

### Post by dcstar on 2009-05-05
> **Grynch108 said:**
> Hi,

When I boot up into Ubuntu I get this message which prompts me for my password.

"The application 'NetworkManager Applet' (usr/bin/nm-applet) wants access to the default keyring, but it is locked."

When I enter the password, it then connects to my network. Is there anyway to get it to remember my password so that I don't have to enter it everytime I log in or boot up?

Cheers.

This has been asked before, a search should provide a solution.

---

### Post by HuckleSmothered on 2009-05-06
In case you can't find it, I believe the problem is that you have auto-login setup. The keyring needs to be set to a blank password to get rid of the login. 

Go to Accessories | Passwords and Encryptions
Select the Passwords tab
Right click on the Passwords folder and Change Password
Set it to be blank
Restart

---

### Post by Grynch108 on 2009-05-07
HuckleSmothered,

Thanks for the tip.

---

