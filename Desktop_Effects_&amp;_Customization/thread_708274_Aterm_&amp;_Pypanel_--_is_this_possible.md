---
title: "Aterm &amp; Pypanel -- is this possible?"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by HangukMiguk on 2008-02-26
I have been running Openbox with Aterm & pypanel, which has been a great setup so far.  I have a transparent borderless aterm, one for terminal work, one for irssi.

One gripe though, and I don't know if this is possible to fix, and have yet to find anything googling: is it possible to make my aterm windows not show up in my task list in pypanel?  if so, how would i go about setting that up?  if not, is there any other panels for *box that i could use to do this, that would also provide transparency?

---

### Post by lidholm on 2008-02-29
Hi,

In the config file for pypanel there is a section where you can specify which programs shouldn't show up in the task bar. I'm not at linux right now so I can't check exactly what it says, but I think you should find the WM_CLASS for aterm and then add that to the list and that should work.

Hope this helps, otherwise I can post another reply on Monday or so, with more specific instructions.

// lidholm

---

