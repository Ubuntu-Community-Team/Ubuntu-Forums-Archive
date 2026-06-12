---
title: "firefox 3.0.7 saves HTML as plain text - fix"
date: 2009-03-11
forum: General Help
---

### Post by jcoles on 2009-03-11
Has anyone else noticed that Firefox 3.0.7 saves HTML as plain text? Previous versions do not have this problem, nor does the Windows version. In about:config I reset browser.download.save_converter_index and that fixed the problem.

After doing some more saves, browser.download.save_converter_index displays as "user set integer 0", instead of default, but saving continues to work.

I have Ubuntu 8.04.

---

