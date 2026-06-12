---
title: "Evolution crashes on startup"
date: 2006-08-25
forum: Desktop Environments
---

### Post by pinkunicorn on 2006-08-25
A little while ago, my mailbox was flooded with a couple of thousand emails due to a misconfiguration. I started to move them away while Evolution was filtering them, and somehow it didn't like that. Evolution crashed. This was on breezy, by the way.

After that, Evolution started to crash consistently on startup (just after showing the password dialog for my email account). I suspect that some kind of cache file got screwed up in the crash.

I have just now upgraded to dapper, and the Evolution version in there also crashes in the same way.

What can I do to fix this? 

All my mail (a couple of accounts) is stored on the servers and read via IMAP. What files in the Evolution settings are cache files and can be removed, and what are important settings files?

---

### Post by ash211 on 2006-08-25
Since your data is stored outside of your local system, you could easily uninstall and reinstall Evolution and see if that clears up your problems.  That's probably the first step you should take here.

---

### Post by pinkunicorn on 2006-08-26
> **ash211 said:**
> Since your data is stored outside of your local system, you could easily uninstall and reinstall Evolution and see if that clears up your problems.  That's probably the first step you should take here.

My mail should be safe, but I guess that my addressbook is stored locally and I would like to keep that. I haven't used the calendar.

---

### Post by ash211 on 2006-08-26
> **pinkunicorn said:**
> My mail should be safe, but I guess that my addressbook is stored locally and I would like to keep that.

(from [http://wiki.mozilla.org/Thunderbird:Help_Documentation:Migrating_to_Mozilla_Thunderbird#Importing_addressbooks](http://wiki.mozilla.org/Thunderbird:Help_Documentation:Migrating_to_Mozilla_Thunderbird#Importing_addressbooks))
> To import address book from evolution 2.4, first select all the contacts by pressing Ctrl+A. This shall select all the contacts. Now, right click and click on Save As VCard. Save the file with a .vcf extension.

Save that .vcf file to your home directory, and then you should be able to uninstall and reinstall evolution.  I personally use Kubuntu, so I haven't used Evolution before.  Hopefully this will work for you!

---

