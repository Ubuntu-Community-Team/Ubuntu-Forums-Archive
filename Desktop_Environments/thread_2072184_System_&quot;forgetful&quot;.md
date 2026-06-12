---
title: "System &quot;forgetful&quot;"
date: 2012-10-17
forum: Desktop Environments
---

### Post by aevora on 2012-10-17
Dear members:
When I open the mail from some file browser asks me to open it, and when you open the browser (chromium) qeu tells me is not the default browser. Answer these questions over and over again every time I restart the system but the system seems forgetful.

Any solution?

Best regards and thanks in advance.

---

### Post by LewisTM on 2012-10-17
In my experience with Google Chrome, it seems to think it is not the default browser even though it has been selected in the Xfce settings. You can safely ignore that warning.

One way to ensure that the right browser is selected as the default is to execute that command in a terminal
```
sudo update-alternatives --config x-www-browser
```
Cheers!

---

### Post by aevora on 2012-10-18
Hi LewisTM,
Already tried with that statement but did not solve the problem. Anyway today the problem no longer occurs you commented (magic?)

If it will happen again reported.

Best regards.

---

