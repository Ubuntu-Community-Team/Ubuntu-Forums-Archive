---
title: "Master password automatically &quot;on&quot; in firefox-3.0 and firefox-3.5"
date: 2009-06-19
forum: General Help
---

### Post by cforceleritas on 2009-06-19
Hello,  I have recently posted this problem to the firefox support forum, but it hasn't been resolved.  I'm going to re-post it here in hopes that someone may have a piece of advice, or in case the problem is not firefox related.

I have never set a "Master Password" and suddenly firefox is asking for the password to the "software security device." In Preferences > Security "Use a master Password" is checked even though I've never set a master password. I can not "Change Master Password" because I do not know what it is.

I try to reset master password with:
firefox -chrome chrome://pippki/content/resetpassword.xul
The next time I start firefox "Use a master password" is still checked.

I've tried to uninstall firefox with:
sudo apt-get remove firefox
and reinstalling with:
sudo apt-get install firefox
and the same problem occurs.

I've tried the beta with:
sudo apt-get install firefox-3.5
and the same problem occurs

I've tried creating a new profile, and the same problem occurs. 

Any suggestions? Are there other services/apps that integrate with firefox in a default ubuntu installation?  I'm at a loss of what could be the problem after completely removing and re-installing firefox with the same problem.

Thanks for amy help you all may provide.

---

### Post by paperplate9 on 2009-06-19
You did not mention if you tried unchecking the 'use a master password' checkbox.

Try rm -rf ~/.mozilla/firefox to remove all profiles/settings

---

### Post by cforceleritas on 2009-06-19
> **paperplate9 said:**
> You did not mention if you tried unchecking the 'use a master password' checkbox.

Sorry I wasn't very clear, I guess that is what I meant by

> **cforceleritas]I can not "Change Master Password" because I do not know what it is.
[/QUOTE]

Basically, I have to enter the masterpassword to disable the master password, and I mever set it to anything.  I can't input a blank password, my ubuntu user password, etc.

[QUOTE=paperplate9 said:**
> Try rm -rf ~/.mozilla/firefox to remove all profiles/settings

After uninstalling firefox, I deleted every file containing "mozilla" or "firefox" on my machine (~/.mozilla/ was included in that list).  That one, I thought for sure, should fix it.

This is a very strange problem.  I appreciate the suggestions paperplate9

---

