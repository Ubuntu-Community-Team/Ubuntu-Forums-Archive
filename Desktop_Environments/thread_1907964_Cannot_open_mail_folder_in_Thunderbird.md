---
title: "Cannot open mail folder in Thunderbird"
date: 2012-01-12
forum: Desktop Environments
---

### Post by agentguerry on 2012-01-12
Hi,

I seem to be not be able to open two folders in Thunderbird mail client.
I can access them when I log into the Exchange webmail though.

In thunderbird, i'm using imap, all folders work (are accessible) except two.

I get an error that states:

***[COLOR="Red"]The current command did not succeed.  The mail server responded:  Not enough server storage is available to process this command.[/COLOR]***

I looked around online, and didn't really find anything that could guide me in the right direction.

thanks for the help.

AG

---

### Post by BC59 on 2012-01-12
A solution could be to export the mail and Address book (if you can) and delete the account-deleting the .thunderbird folder in home.
If you cannot export the mail, you could rename .thunderbird to force the application to create a new account and then copy the .msf files of the mail folder to the new account.

---

### Post by agentguerry on 2012-02-01
That did fix my problem.  Thanks !

---

### Post by BC59 on 2012-02-01
So finally you copied the inbox.msf etc files or just exported the mail?

---

