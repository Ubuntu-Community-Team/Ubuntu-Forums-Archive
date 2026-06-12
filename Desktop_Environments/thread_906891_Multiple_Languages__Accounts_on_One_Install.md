---
title: "Multiple Languages / Accounts on One Install"
date: 2008-08-31
forum: Desktop Environments
---

### Post by Ashocka on 2008-08-31
Hi,

I have Ubuntu 8.04 installed on a machine.  I'm wanting to run my own account with English as the default language and Chinese on my wife's account.  But I find with Ubuntu it seems to only accept one language for all accounts on that machine.  I can't run one language on one account and the other on the other account.  Any suggestions?

Thanks
Geoff

---

### Post by pytheas22 on 2008-08-31
According to this [thread]("http://ubuntuforums.org/showthread.php?t=494685"):

> This can be done by:

1. An administrator enabling support for all required languages (System->Administration->Language Support)
2. Users can then select their language from the login screen (Option->Language Selection)

Note that the login screen itself will be in the system default language.

I've never done that myself so I can't confirm that it works, but let us know if it doesn't and we can look for another way to do it.  I know that Gnome keeps a separate language profile for each user account, so there should be no reason why you can't have different languages on different accounts--I think it's just not as easy to configure that way through the GUIs as you might like.

---

### Post by Ashocka on 2008-09-01
> **pytheas22 said:**
> According to this [thread]("http://ubuntuforums.org/showthread.php?t=494685"):



I've never done that myself so I can't confirm that it works, but let us know if it doesn't and we can look for another way to do it.  I know that Gnome keeps a separate language profile for each user account, so there should be no reason why you can't have different languages on different accounts--I think it's just not as easy to configure that way through the GUIs as you might like.


I'll check this in the next few days, but I'm pretty sure this is exactly what I did, but when you reboot every account is the under the last language chosen.  I think from memory you need to be sudo to change it within each account.

---

### Post by Ashocka on 2008-09-01
Thanks, I found the solution.  Didn't know of the language option to use at the login interface... before logining into the desktop.

Thanks again.
Geoff

---

