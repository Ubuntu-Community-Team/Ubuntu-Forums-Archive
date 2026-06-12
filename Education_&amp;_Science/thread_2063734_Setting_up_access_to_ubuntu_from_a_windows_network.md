---
title: "Setting up access to ubuntu from a windows network"
date: 2012-09-27
forum: Education &amp; Science
---

### Post by DRF on 2012-09-27
Hi,

I work at a school as a technician and I have been asked to look into providing access to programming resources like the Python interpreter. I'm looking into different ways to provide an environment for the students to program in, where any mistakes won't effect the schools windows based network.

We already use windows deployment services with PXE boot (which I don't want to play with too much) so a standard LTSP setup won't work unfortunately as that would have been a good solution otherwise.

We provide a windows terminal server which allows staff to remote in from home using an RDP client and I was wondering if there are any guides to do something similar in ubuntu. The issue with the standard remote desktop software is that it uses the current session by default rather than create a new session for each user.

If anyone has tried this before and has any advice or suggestions please let me know.

Daniel

---

### Post by mevun on 2012-09-28
Is the only reason you want access to Ubuntu for a python interpreter?  Because you can install a Python interpreter for Windows also.  I don't know much about Windows server software, but I was under the impression that a Windows RDP client can use any installed applications (in this case, the Python interpreter).  I don't know Windows, but maybe you can search for ways to add lots of accounts (for the students) like student1, student2, etc.  So if the work is done in class (and you don't allow password changes), then you could limit the number of Windows accounts needed.

With respect to a GUI session, I am not real knowledgeable, but I think you would have the same problem with Ubuntu as Windows.  Using the same "login" will normally try to connect you to an existing GUI session.  In fact, I think it is worse in that the user on the client side might need some knowledge on how to connect and/or start a GUI session.  However, I haven't used the latest Linux software so there may be solutions out there that I'm not aware of.

Since you haven't got any other responses, I would also suggest that maybe you try to get forums staff to move this thread to the Networking help forum instead.

---

