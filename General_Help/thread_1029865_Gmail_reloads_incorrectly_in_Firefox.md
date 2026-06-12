---
title: "Gmail reloads incorrectly in Firefox"
date: 2009-01-03
forum: General Help
---

### Post by euchrid33 on 2009-01-03
I'm having a strange problem with Gmail, using Firefox 3.0.5 under Ubuntu 8.10.  I'm pretty sure that it occured in previous Firefoxes, but not under 8.04.

When I log into Gmail, everything is fine.  If I close that tab or the browser without logging out, however, and then reload Gmail, the page loads with no background, all the text in blue, with very limited features - no chat, no Reader or Calender (I'm using the Integrated Gmail plugin), nothing.  It's similar to the basic HTML view in terms of functionality, but it looks a little different.

I've tried disabling all my plugins, without any change.  The problem doesn't occur in Epiphany, so I know that it's Firefox related.  I haven't tried any previous versions, but I'm willing to if someone tells me how.  Firefox 2 used to be in the standard repositories but I can't find it now.

Any suggestions at all?

---

### Post by ralf57 on 2009-01-21
I have the same problem.
I've disabled all extensions with no luck.

---

### Post by halovivek on 2009-01-21
The problem may be with the cache used by firefox. try to allocate more space for firefox and give a try.

---

### Post by ralf57 on 2009-01-21
> **halovivek said:**
> The problem may be with the cache used by firefox. try to allocate more space for firefox and give a try.

I've allocated 100MB but the the problem still occurs

---

### Post by ralf57 on 2009-02-06
I solved my problems by setting the "Browser.cache.memory.enable" to "true"
in firefox configurations (about:config in address bar)

---

