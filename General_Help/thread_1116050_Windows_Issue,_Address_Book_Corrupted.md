---
title: "Windows Issue, Address Book Corrupted"
date: 2009-04-04
forum: General Help
---

### Post by ShinHadoken on 2009-04-04
Hey guys, sorry that this is not in any way related to Linux, but I'm having a serious Windows problem here, and I don't have anywhere else to turn (Microsoft was no help as usual) but the faithful Linux community that has always helped me in the past.

The Windows Address Book has been corrupted. When I try to access the Address Book in Outlook Express, I get the error, "Unable to open Address Book, the Address Book may not be installed properly." So, I set a System Restore to a month ago, and when it boots back up, I access the Address Book directly from Start > Programs > Accessories > Address Book. I get the following error, on a fresh boot no less:

"The Address Book file has been locked by another application. Please close the other application and try again later."

Can someone please give me some insight on this? Thanks a ton.


-SH

---

### Post by ShinHadoken on 2009-04-04
Nevermind guys, discovered that the WAB file in Docs & Sets/User/App Data/Microsoft/Address Book was set to read-only. Unchecked that setting, and now she works like a charm. Thanks for the would-be help, though! Hehe.

-SH

---

### Post by fabricator4 on 2009-04-04
Uh huh.

Boot in safe mode as adinistrator, copy the address book file out, then delete the locked file.  If you can't delete the file in safe mode, boot a live CD and see if you can do it that way (or through dual boot if you have it)

Boot windows again, run some virus scans, just in case.

If the system is clean import your address book data from the file you copied.  Hopefully it will be fine.

Chris

---

