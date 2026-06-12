---
title: "Evolution: source doesn't support prompt for credentials"
date: 2022-10-13
forum: Desktop Environments
---

### Post by Soarer on 2022-10-13
Hi,

I have been using Evolution with Office 365 and Gmail for a few weeks, mostly successfully (it is a bit slow, but unlike Outlook PWA it didn't crash).

Yesterday I got a hard error message when (not) accessing my Office 365 account: source doesn't support prompt for credentials. The account is, after a few retries, disabled.

Starting Evolution from a terminal provides no extra information. The account in use is a Gnome Online Account. I replaced it with a normal Exchange email account, but there was no difference.

Evolution is Version 3.44.4-0ubuntu1 and EWS feature is installed. The config files at .config/goa-1.0 seems OK, as does the password in the keyring.

Does anyone else have this problem suddenly, or is it just me? Does any kind person know why this is currently happening?

Thanks.

---

### Post by Soarer on 2022-10-14
So, I solved this by following the instructions at [https://sites.utexas.edu/glenmark/2021/02/01/how-to-setup-your-office-365-email-using-evolution-ews-linux/]("https://sites.utexas.edu/glenmark/2021/02/01/how-to-setup-your-office-365-email-using-evolution-ews-linux/")

I'm pretty sure though that I didn't do it that way when I originally configured it from the Online Accounts settings. I now have my Office 365 email as a separate email account, not managed through Online Accounts.

---

