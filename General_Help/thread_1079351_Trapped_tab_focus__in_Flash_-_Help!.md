---
title: "Trapped tab focus  in Flash - Help!"
date: 2009-02-24
forum: General Help
---

### Post by joejubee on 2009-02-24
Hey all!

I have several flash movies embedded in html pages, and for whatever reason, when you tab through the page, when you get into the flash movie, you can't tab out. The tab just goes in a loop through the tabindex of the swf.

Is there a way that you can add a button or a little script in the swf, set it to the last in the taborder, and then make it set the focus on the page to a link/div/id/anchor in the html, (outside the swf)

I would think this would be an issue that people would have experienced/addressed before - especially for anyone who is developing flash for government sites, where it needs to be all nice and accessible and Section 508 compliant.

Thanks!

Joe

---

### Post by joejubee on 2009-03-03
After a bunch of testing and research, it appears that one of the core issues that is causing flash focus getting trapped is when you use components. The minute I removed the components (TextArea Component) focus was no longer trapped. 

So, rule of thumb - don't use components, just build them yourself.

Joe

---

### Post by Sef on 2009-03-03
Moved to General Help.

---

