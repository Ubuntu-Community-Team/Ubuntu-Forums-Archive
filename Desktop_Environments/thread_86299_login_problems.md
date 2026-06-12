---
title: "login problems"
date: 2005-11-04
forum: Desktop Environments
---

### Post by chubsmalone on 2005-11-04
I have been running breezy badger 5.10 on my Dell Inspiron 1200 laptop for a couple days now with very few problems.  Today I booted up the computer, logged in and immediately got an error message that said:

Your session only lasted 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see of you can fix this problem.

I can view the details of the !/.xsession-errors file, but I am on another machine and I don't want to type it all out.  

I have no idea how to fix this problem...can anybody help me before I reinstall?

---

### Post by kvidell on 2005-11-04
Check the permissions on .ICEAuthority and .Xauthority.
If they're not set for your user, do so.

chown chubsmalone:chubsmalone ~/.*authority

See if that fixes it, if not, rm the files and try again.
- K

---

