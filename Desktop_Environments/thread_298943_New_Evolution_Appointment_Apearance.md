---
title: "New Evolution Appointment Apearance"
date: 2006-11-13
forum: Desktop Environments
---

### Post by lwylie on 2006-11-13
I recently upgraded to Edgy and have been enjoying it so far.  However, the new appearance of appointments in Evolution doesn't work very well for me.  It's a tad bit clunky and doesn't show up as well as the old appearance.  Is there any way that I can switch back to the old appearance without actually having to downgrade back to the older version?

Thanks!

---

### Post by Spin Doctor on 2006-11-28
I never ran Evolution with Dapper, since I upgraded quite right away to Edgy. Can you explain to me how it used to look? Maybe someone with Dapper can submit a screen capture of the "old" Evolution calender? Maybe worth downgrading....

---

### Post by Spin Doctor on 2007-01-25
Ok, I think I have found the solution to this.

The whole idea is to **make the calender in Evolution 2.8.1 run more smoothly**. One of the things that irritates me most is the gradient of events. It looks just extremely tacky in my opinion. 

Working on some other problems, I found a **solution to turn of this gradient** **of events in the calender**. It runs much smoother on my computer, and looks alot more aesthetic.

In your commandline: ```
gconf-editor
```Navigate through the treestructure in the left pane to:
**apps > evolution > calender > display**[B]

Uncheck the property, "events_gradient"[/B]

Exit gconf-editor

Restart Evolution

---

