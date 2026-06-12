---
title: "Cups printing to windows server requires authentication for each document"
date: 2013-04-30
forum: Desktop Environments
---

### Post by raydawg on 2013-04-30
Hi,

We have a secured windows print server that we're trying to get our Ubuntu 12.04 desktops to print to; we can connect to the server/print queues using CUPS, however, it prompts the users for their AD login each time they print a document.

We use winbind to authenticate to the domain when logging on to Ubuntu, and are using pam-mount to mount their home directories as well, so winbind is functional.

Is there any way to get CUPS to automatically authenticate without pestering the users?  Checking the "Remember credentials" checkbox doesn't seem to be doing anything.

---

