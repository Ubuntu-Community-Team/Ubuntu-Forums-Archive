---
title: "why does my user agent say 3.0.8 and &quot;ant.com toolbar&quot;"
date: 2009-04-29
forum: General Help
---

### Post by scarf on 2009-04-29
i am using firefox-3.0.10, as is shown in the about firefox dialog, and:

```

$ apt-cache policy firefox
firefox:
  Installed: 3.0.10+nobinonly-0ubuntu0.9.04.1
  Candidate: 3.0.10+nobinonly-0ubuntu0.9.04.1
  Version table:
 *** 3.0.10+nobinonly-0ubuntu0.9.04.1 0
        500 http://mirrors.us.kernel.org jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
        100 /var/lib/dpkg/status
     3.0.8+nobinonly-0ubuntu3 0
        500 http://mirrors.us.kernel.org jaunty/main Packages

```

but, my useragent is "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.10) Gecko/2009042523 Ubuntu/9.04 (jaunty) Firefox/3.0.8, Ant.com Toolbar 1.3"

wtf?

---

### Post by scarf on 2009-05-11
somehow my general.useragent.extra.firefox preference was set to "Firefox/3.0.8, Ant.com Toolbar 1.3".  how that happened, who knows?

---

### Post by glotz on 2009-05-11
That would happen if you installed the ant.com toolbar extension.

Some extensions do that and mess up your user agent.

---

### Post by scarf on 2009-05-12
that is strange part because i have never installed that extension!

---

### Post by glotz on 2009-05-12
Were you using that Firefox profile on windoze?

---

### Post by scarf on 2009-05-12
i did migrate it from windows about 6 months ago, but i have checked my user-agent regularly and didn't notice this discrepancy until now.

---

