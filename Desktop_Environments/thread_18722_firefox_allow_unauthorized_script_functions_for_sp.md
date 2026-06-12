---
title: "firefox: allow unauthorized script functions for spesific server"
date: 2005-03-08
forum: Desktop Environments
---

### Post by mtron on 2005-03-08
Hi! 

I am using a php based CMS, and need the ablility of allowing scripts the copy / paste function. I get the following security warning (using ubuntu 4.10 & firefox 1.0 backport)

[I]You'll have to quit Mozilla/Netscape before you do this!

Find the files "prefs.js" and "user.js" on your local computer. Open them up with a texteditor and add the following lines:

user_pref("capability.policy.allowclipboard.Clipboard.cutcopy", "allAccess");
user_pref("capability.policy.allowclipboard.Clipboard.paste", "allAccess");
user_pref("capability.policy.policynames", "allowclipboard");
user_pref("capability.policy.allowclipboard.sites", "http://www.YOUR SERVER HERE.com");[/I]

I found the file "Prefs.js" in /etc/mozilla & ~homedir/.mozilla/firefox/~profilename/prefs.js, but could not find user.js file.

Where is it?

---

### Post by ember on 2005-03-08
There is no user.js in the beginning, yet it should work this way. At least for me it worked only entering it into prefs.js (it simply ignored my user.js entries).

---

### Post by mtron on 2005-03-09
Thanks. It worked for me as well

---

### Post by wernst on 2005-03-10
You're using HTMLArea in Drupal, aren't you?

There's a fix also listed in the Drupal forums. Search for it.

-Warr

---

