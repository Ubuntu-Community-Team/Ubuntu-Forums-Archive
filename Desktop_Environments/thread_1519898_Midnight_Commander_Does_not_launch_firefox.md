---
title: "Midnight Commander Does not launch firefox"
date: 2010-06-28
forum: Desktop Environments
---

### Post by tim042849 on 2010-06-28
Using ubuntu 10.04.
On previous ubuntus, with the following entry in .mailcap ::
```

ext/html;  firefox '%s';   nametemplate=%s.html;   test=test "$DISPLAY" != ""

```
Would result in the following action.
When selecting an .html document in MC and pressing [ENTER], firefox
would load with the document as content (if firefox not running) or if
firefox not running, would open a new tab with the content.
Now, all that happens is that the source of the document is read to
stdout. This is highly inconvenient, given how handy this feature is when
working correctly.
I hope someone has a solution or can point me to URLs on this or similar
topics.
Thanks
tim

---

