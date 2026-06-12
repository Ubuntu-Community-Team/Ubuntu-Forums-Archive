---
title: "Fedora Postfix Forwarding Issue"
date: 2018-11-29
forum: Fedora/RedHat and derivatives
---

### Post by gbenge on 2018-11-29
Hello guys,


gbenge is my name and I'm new here, I'm also new to postfix, I will appreciate if you can help with this issue.


we just upgraded the MTA (mail transfer agent) of our email server from sendmail to postfix. Before the upgrade, there is this special email account created for all the staffs' email - i.e. whenever any email is coming in, a copy goes to this email account and also whenever anyone is sending email out, a copy is automatically sent to it. So after the upgrade, this changed - instead of a copy dropping in this account, we have multiple copies dropping in the account especially when an email drops on any group email account, multiple copies equivalent to the number of users in the group get forwarded to this special email account instead of just a copy.


Can anyone please give me idea of how this can be sorted out?


Thanks in anticipation.

---

