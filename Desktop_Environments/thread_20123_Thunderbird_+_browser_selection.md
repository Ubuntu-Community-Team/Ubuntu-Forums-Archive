---
title: "Thunderbird + browser selection"
date: 2005-03-15
forum: Desktop Environments
---

### Post by mirtux on 2005-03-15
Hi,
  i'm using thunderbird as my mail client. By default when in a mail I click on a hyperlink it opens with konqueror and not with my default browser which is Firefox. How is possible to teach Thunderbird to use Firefox instead of konqueror?

Thanks,
MC

---

### Post by mirtux on 2005-03-24
Ok, i've managed to get this running inserting the following two lines in **prefs.js **file in the .mozilla-thunderbird directory on your home dir:

 ```

user_pref("network.protocol-handler.app.http","mozilla-firefox");
user_pref("network.protocol-handler.app.https","mozilla-firefox");

```

Hope this will be useful for somebody....

Regards,
MC

PS: there must be a switch inside Thunderbird to do this! :!:

---

