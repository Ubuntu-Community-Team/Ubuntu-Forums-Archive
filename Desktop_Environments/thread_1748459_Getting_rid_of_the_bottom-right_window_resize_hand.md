---
title: "Getting rid of the bottom-right window resize handle"
date: 2011-05-03
forum: Desktop Environments
---

### Post by mpacula on 2011-05-03
Is there a way to make bottom-right window resize handles disappear in Ubuntu 11.04? I run a tiling window manager and thus have no use for them, especially since they can distract and cover information. How do I make them permanently go away? 

Any help will be greatly appreciated :)

---

### Post by mpacula on 2011-05-03
I'll help myself :-)

Put this in ~/.gtkrc-2.0:

```
style "default-style"
{
  GtkWindow::resize-grip-height = 0
  GtkWindow::resize-grip-width = 0
}

class "GtkWidget" style "default-style"
```

---

### Post by WyleECoyote on 2011-08-14
Thank you very much mpacula

this fixed my issue as well :) I am so glad you spent the time to post the fix instead of leaving it open

---

### Post by satyanash on 2012-01-14
Thanks!
It works!
For me, the file did not already exist, so I had to create it. :D
The triangular resize handle at the bottom right didn't really fit well with my Xmonad or Fvwm2 Configs... ;)

Satyajeet

---

