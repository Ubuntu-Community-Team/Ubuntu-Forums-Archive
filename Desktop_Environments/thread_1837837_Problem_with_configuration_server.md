---
title: "Problem with configuration server"
date: 2011-09-02
forum: Desktop Environments
---

### Post by kozhi on 2011-09-02
I am using Ubuntu 11.04 on my desktop. Everything was fine till this morning when I tried to boot. Instead of going to the log in screen, a message comes up:
"There is a problem with the configuration server.
(/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)"

There is a "close" button. When I click on that button, I am taken to the login screen, although it now looks different. There is an additional message in one corner which says:
"Install problem! The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator."

As I said, this version of Ubuntu is running since it was released. I had upgraded it from the previous version. So why all of a sudden this error should come? When I try logging in, I get the same message  as mentioned above "There is a problem with the configuration ..."

On checking, I found some discussion here:
[http://ubuntuforums.org/showthread.php?t=1574542](http://ubuntuforums.org/showthread.php?t=1574542)
and here [http://ubuntuforums.org/showthread.php?t=917306](http://ubuntuforums.org/showthread.php?t=917306)
and [http://ubuntuforums.org/showthread.php?t=1587918](http://ubuntuforums.org/showthread.php?t=1587918)

But I am unable understand what is to be done. How do go I to a terminal when I can't log in? Is there any alternative to reinstalling Ubuntu?

Thanks.

---

### Post by 2F4U on 2011-09-02
Can you press Ctrl-Alt-F1 (or F2, ...)? This should open a virtual console which allows you to login.

---

### Post by kozhi on 2011-09-02
> **2F4U said:**
> Can you press Ctrl-Alt-F1 (or F2, ...)? This should open a virtual console which allows you to login.
Thank you very much for your quick reply. Yes, Ctrl+Alt+F1 does open up a command line interface that asks for login and password. However, now the problem is that it is not taking my (administrator) login password, although I can login to the other (non-administrator) account.

---

