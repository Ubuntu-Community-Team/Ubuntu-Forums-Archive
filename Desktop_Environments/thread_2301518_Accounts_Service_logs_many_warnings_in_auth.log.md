---
title: "Accounts Service logs many warnings in auth.log"
date: 2015-11-02
forum: Desktop Environments
---

### Post by lister171254 on 2015-11-02
I'm getting many if the following errors after upgrading to 15.10

[HTML]
Nov  3 14:17:26 LeosLinux dbus[1101]: [system] Rejected send message, 9 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1098 comm="/usr/lib/accountsservice/accounts-daemon ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.65" (uid=1000 pid=2820 comm="/usr/lib/x86_64-linux-gnu/indicator-messages/indic")
Nov  3 14:17:51 LeosLinux dbus[1101]: message repeated 3 times: [ [system] Rejected send message, 9 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1098 comm="/usr/lib/accountsservice/accounts-daemon ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.65" (uid=1000 pid=2820 comm="/usr/lib/x86_64-linux-gnu/indicator-messages/indic")]
Nov  3 14:18:43 LeosLinux dbus[1101]: [system] Rejected send message, 9 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1098 comm="/usr/lib/accountsservice/accounts-daemon ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.65" (uid=1000 pid=2820 comm="/usr/lib/x86_64-linux-gnu/indicator-messages/indic")
Nov  3 14:19:11 LeosLinux dbus[1101]: message repeated 3 times: [ [system] Rejected send message, 9 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1098 comm="/usr/lib/accountsservice/accounts-daemon ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.65" (uid=1000 pid=2820 comm="/usr/lib/x86_64-linux-gnu/indicator-messages/indic")]
Nov  3 14:22:16 LeosLinux dbus[1101]: [system] Rejected send message, 9 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1098 comm="/usr/lib/accountsservice/accounts-daemon ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.65" (uid=1000 pid=2820 comm="/usr/lib/x86_64-linux-gnu/indicator-messages/indic")
Nov  3 14:24:32 LeosLinux dbus[1101]: message repeated 5 times: [ [system] Rejected send message, 9 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1098 comm="/usr/lib/accountsservice/accounts-daemon ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.65" (uid=1000 pid=2820 comm="/usr/lib/x86_64-linux-gnu/indicator-messages/indic")]
Nov  3 14:28:24 LeosLinux sudo: pam_unix(sudo:session): session closed for user root
Nov  3 14:28:51 LeosLinux dbus[1101]: [system] Rejected send message, 9 matched rules; type="method_return", sender=":1.3" (uid=0 pid=1098 comm="/usr/lib/accountsservice/accounts-daemon ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.65" (uid=1000 pid=2820 comm="/usr/lib/x86_64-linux-gnu/indicator-messages/indic")
[/HTML]

As I'm running ossec, these errors generate emails, so I would like to find out what error error means and how to stop it from occuring.

Thanks

---

