---
title: "[SOLVED] Evolution - remove account from command line"
date: 2008-12-11
forum: General Help
---

### Post by buddywilliams on 2008-12-11
How do you remove an evolution account with the command line? I created a IMAP connection yesterday and it won't startup correctly. Thanks.

---

### Post by buddywilliams on 2008-12-11
I am not sure why this worked but I did the following:

```

rm -rf ~/.evolution/exchange/*
rm -rf ~/.evolution/mail/exchange/*
rm -rf ~/.evolution/mail/imap/*
evolution --offline

```

I tried the offline mode before but it would just hang. After delete the Exchange and IMAP subfolders evolution would at least start. From there I went to preferences and removed the IMAP account.

---

