---
title: "link in terminal opens under wrong firefox profile"
date: 2006-10-01
forum: Desktop Environments
---

### Post by mrt on 2006-10-01
When I right click a hyperlink in a terminal window and choose Open Link, it opens, but with a secondary profile that I created.  How can I set it up so any program that uses Firefox to open links opens it with the default firefox profile?  Thanks.

---

### Post by lagagnon on 2006-10-01
Firefox, Edit, Preferences, Tabs - adjust as you like.

---

### Post by mrt on 2006-10-02
Your suggestion didn't help.  I should have mentioned that firefox is not even open when I click the link, so the tab Terminal should use doesn't really matter at this point.  That leads me to believe that I should be looking at how Terminal (or any application) knows how to use firefox as the default browser.

I've had a look in /etc/default and /etc/firefox but didn't see anything that looked like it might help.  If I could pass the "-P default" option to firefox I'm sure that would take care of my problem.  Do you have anymore suggestions?  Thanks.

---

