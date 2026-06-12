---
title: "xrdp remote login help"
date: 2011-07-06
forum: Desktop Environments
---

### Post by maxxjr on 2011-07-06
I am started on the path to getting remote access from a windows pc running mstsc to my ubuntu 11.04 pc running xrdp.

I am able to ssh in with my user account, start a vncserver instance, and then connect with mstsc.

I have enhancements that I want to do, and so far had little luck finding details on how to do it.  Any pointers/resources are appreciated!

My goals:

Have the first screen come up be the username/password screen the same as if I were logging in locally.  (Could be a different login manager...the main goal is that once I connect via mstsc, I could then log in to any user's desktop.)

To do this, I would need to start vncserver automatically...I don't think this should be too difficult.

I also will need to work on understanding password management for the xrdp connection (from mstsc)...at least to allow the connection and then get "out of the way".  

Having a new mstsc connection start with the login screen vs. a user's desktop is another thing to figure out.

Logging out, and then re-connecting with mstsc causes a problem with the display, which to this point I have worked around by restarting the vncserver session.  Automating this restart after a logout is something else that I need to figure out.


Again...this is my plan, and if anyone has a link that might get me through some of the above faster, thanks!

---

