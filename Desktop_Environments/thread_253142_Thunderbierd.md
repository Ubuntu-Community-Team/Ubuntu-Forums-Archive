---
title: "Thunderbierd"
date: 2006-09-07
forum: Desktop Environments
---

### Post by DougieFresh4U on 2006-09-07
I am trying to set  up 2 accounts in thunderbird when I try to send mail, it keeps asking me for my password. I enter password then ok, then it asks for password again and so on the same over and over, also my AOL e-mail does not hav ethe same password as my default account and I am not asked to put it in when setting up the account so how can it recieve? I don't think I quite understood the set-up. I may need a real simple explanation:confused:also, I would like to set-up aol aim and no nadda about doingt it:confused:

---

### Post by Uncle Spellbinder on 2006-09-07
I had a similar problem about a year ago. To be honest, I've no idea what the solution was. I can tell you, though, I found the answer [***_HERE_***](http://forums.mozillazine.org/viewforum.php?f=39)

---

### Post by crossedout on 2006-09-08
Are you setting up 2 accounts from the same provider (ie. 2 earthlink accounts)?  If so, then that is the problem.  The outgoing takes the smtp of whichever account is setup.  So if, Account-A is setup with smtp and Account-B tries to send an email, smtp will ask for Account-A pw.  It will send it if you punch in the right pw but the sent address will be listed as Account-A even though you may have done everything from Account-B.

To work around it, I believe if you setup a second profile and move Account-B to there then the smtp will not conflict.  Good Luck!

-Xout

---

