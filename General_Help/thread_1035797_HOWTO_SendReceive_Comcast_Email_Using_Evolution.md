---
title: "HOWTO: Send/Receive Comcast Email Using Evolution"
date: 2009-01-10
forum: General Help
---

### Post by Apesbrain on 2009-01-10
It can be done!  Tried a number of settings and here is what worked:

1. In Evolution mail client, go to "Edit > Preferences" and ADD new account or EDIT your existing Comcast settings
2. On the "Identity" tab, enter a descriptive ACCOUNT/NAME, e.g. "Comcast Mail", your FULL NAME is just that, e.g. "John Smith", then enter and make sure your Comcast email address is correct and complete, e.g. "john.smith@comcast.net"
3. On the "Receiving Email" tab: SERVER TYPE = POP, SERVER = mail.comcast.net, USERNAME = your Comcast username, e.g. "john.smith", USE SECURE CONNECTION = SSL encryption, AUTHENTICATION TYPE = Password, and check "Remember password" at your option
4. On the "Sending Email" tab: SERVER TYPE = SMTP, SERVER = smtp.comcast.net:465, check the box on "Server requires authentication", USE SECURE CONNECTION = SSL encryption, AUTHENTICATION TYPE = Plain, USERNAME = your Comcast username, e.g. "john.smith", and check "Remember password" at your option.
5. Click OK to save.

First time you "Send/Receive" you will be prompted for your Comcast password.  Be patient as it may take a few seconds to make the connection.

Good luck.

---

