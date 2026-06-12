---
title: "sudo forgets password quickly in a single terminal"
date: 2009-02-03
forum: General Help
---

### Post by sumanc on 2009-02-03
My question is: how long a terminal remembers the sudo password before it asks for it again? I am asking for the same terminal here.

I need to use certain login software to access my broadband and I need issue the command "sudo sifyconnect", then it asks for sudo password and everything goes find, until I find after sometime internet is not working. Initially I was thinking that my ISP (Sify) is doing some kind of auto-logout. But later when I issue the same command, it asks for sudo passowrd again in the same terminal.

I would like to know how to increase the lifetime of sudo password memory in a single terminal. Thanks.

---

### Post by taurus on 2009-02-03
Hope this is what you are looking for.

[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

---

### Post by mcduck on 2009-02-03
changing sudo timeout should not have any effect on your issue.

You only need to give the password to confirm at the time you run the command, after that the command will continue running with root permissions until you stop it. sudo timeout will not stop your network, it only tells how long after giving the password youa re able to run additional comamnds with sudo without having to retype your password.

For example, if I start a file manager as root with "gksudo nautilus" the file manager will stay open, and with root permissions, for days, or years, until the window is closed or the computer restarted.

---

