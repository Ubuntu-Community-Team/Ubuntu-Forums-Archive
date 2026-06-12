---
title: "Now What?"
date: 2005-09-22
forum: Desktop Environments
---

### Post by Christopher999999 on 2005-09-22
I an error message (see image) when I do anything user related.

---

### Post by jworr on 2005-09-22
When do you get this message specifically?  I'm thinking there might be a problem with your sudoers file. Open a terminal (by right clicking on the desktop) and type

sudo visudo

it should ask for your password if you can open the file and you see this:

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

then we will try something else, but if you can't open visudo or it looks different then reboot and select the "recovery mode" option and run sudo visudo and edit the file to look like this

---

