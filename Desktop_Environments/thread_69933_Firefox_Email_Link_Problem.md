---
title: "Firefox Email Link Problem"
date: 2005-09-28
forum: Desktop Environments
---

### Post by elder68 on 2005-09-28
I am using Kubuntu with Firefox and Thunderbird. When I am logged on to a site and want to contact them via email, when I click on the email link on the site, Thunderbird does not come up. I have tested it on more than one site. I have read through both programmes preferences but can't seem to find where to set up the default email client.

Thank you,

Bill.

---

### Post by mlomker on 2005-09-28
Check in Control Center, KDE Components, then Component Chooser.  There are settings for defaults in there.

---

### Post by randcoop on 2005-09-28
In Firefox, you can set the email link response this way:

Enter about:config in the URL address line.

Right click on the about:config page and select New/string.

The first entry is: network.protocol-handler.app.mailto

Then in the next window, enter thunderbird (or mozilla-thunderbird...depends on what the progam runs under).

Next time you start up Firefox and click on a mailto: link, it should work.

---

### Post by elder68 on 2005-09-28
[QUOTE=mlomker]Check in Control Center, KDE Components, then Component Chooser.  There are settings for defaults in there.[/QUOTE]

Thank you for the above, I tried it but I could not get it to work.

Bill.

---

### Post by elder68 on 2005-09-28
[QUOTE=randcoop]In Firefox, you can set the email link response this way:
Enter about:config in the URL address line.
Right click on the about:config page and select New/string.
The first entry is: network.protocol-handler.app.mailto
Then in the next window, enter thunderbird (or mozilla-thunderbird...depends on what the progam runs under).
Next time you start up Firefox and click on a mailto: link, it should work.[/QUOTE]

Thank you for the above. Followed your directions and it worked just fine.

Bill.

---

