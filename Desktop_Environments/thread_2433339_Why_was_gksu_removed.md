---
title: "Why was gksu removed?"
date: 2019-12-17
forum: Desktop Environments
---

### Post by steven43 on 2019-12-17
Was there any particular reason why gksu was removed, other than just because?

I know most people used gksu and sudo to elevate to the root user.  I actually used it to run a series of FireFox browsers as different users within the same X session.

Removing gksu has made this a bit difficult.  And, as far as I know, there isn't an alternative (other than opening a terminal and doing a [FONT=courier new]sudo -H -u otheruser /usr/bin/firefox[/FONT]).

Was there a particular reason why gksu was removed?  And what is the alternative for running applications as other users within the same X session?

---

### Post by deadflowr on 2019-12-17
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=892768]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=892768")
>  I actually used it to run a series of FireFox browsers as different users within the same X session.
There should safer and better options to do that.
like this: [https://unix.stackexchange.com/questions/108784/running-gui-application-as-another-non-root-user]("https://unix.stackexchange.com/questions/108784/running-gui-application-as-another-non-root-user")

---

### Post by steven43 on 2019-12-24
Many thanks!  I had not thought about passing SUDO_ASKPASS to sudo and setting it as /usr/bin/ssh-askpass  I think this might work.

---

