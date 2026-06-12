---
title: "Do i need mozback up?"
date: 2005-08-15
forum: Desktop Environments
---

### Post by mit on 2005-08-15
Hi,
Always been a Windows user  [-X  and have now found a new friend in Ubuntu  :) 
I always used Mozback-up for backing up Firefox. Do i still need that program with Ubuntu?

---

### Post by buldir on 2005-08-15
The FAQ [http://mozbackup.jasnapaka.com/faq.html](http://mozbackup.jasnapaka.com/faq.html) states there is no *nix version of Mozbackup yet.  I recommend using tar or zip in a cron job to automatically backup your /home/"user name"/.mozilla directory.  Personally, I only backup my bookmarks.  In the command line, type:

```
man tar
man zip
man cron
```

for more information on using these wonderful tools.

---

### Post by mit on 2005-08-15
Hi,
Thanks for the reply. The problem I have then is that I have loads of stuff on Firefox but on a Windows platform  :???:

---

### Post by buldir on 2005-08-15
I think you're SOL.  By lots of stuff, I assume you're talking about extensions?  Because of the large difference between the the Linux and Windows file structure, you could easily create problems by transferring all the Windows Firefox profile files over to your Linux box.  The best solution for a clean, working Firefox on your Linux box is to copy your bookmarks over and reinstall your extensions.  I save my extensions (*.xpi) to my hard drive, so if I bork my Firefox install, I can easily get it up and running again.

---

### Post by mit on 2005-08-17
I should have made myself more clear in the first post  :-# 
I want to back up bookmarks and all my saved passwords for the sites i visit.

---

### Post by strikeforce on 2005-08-17
[QUOTE=mit]I should have made myself more clear in the first post  :-# 
I want to back up bookmarks and all my saved passwords for the sites i visit.[/QUOTE]

You will have to mount your winxp partition and cp your bookmarks.  The place to put them is under your ~/.mozilla/firefox and then whatever your account is called under there.

---

