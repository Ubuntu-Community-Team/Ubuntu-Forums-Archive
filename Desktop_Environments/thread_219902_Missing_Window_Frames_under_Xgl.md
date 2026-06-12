---
title: "Missing Window Frames under Xgl?"
date: 2006-07-20
forum: Desktop Environments
---

### Post by LordMau on 2006-07-20
While fiddling around with the slab, I noticed that my windows now don't have their translucent frames. Worse I'm unable to grab the sides or corners of the windows for resizing. Only the title bars remain, and the windows look squarish.

checking at compiz forum this occured after the last update of compiz, and was a side effect of new settings for the decoration plug-in. However it would seem that certain schemas had needed to be installed for the update to take effect. This were in gconf-editor located at: 

```

/apps/compiz/plugins/decoration/allscreens/options/
```

and the schemas were:

```

corner_radius
win_extents_bottom
win_extents_left
win_extents_right
win_extents_top
```

These weren't in my system after the update. I tried to reinstall the update via synaptic but this was to no avail. 

So in my case I had to drop down to CLI, stopped GDM, did a apt-get purge of compiz + compiz-gnome + gset-compiz, then a apt-get install of the same. Finally the schemas stuck, I was able to adjust my frames and see them once again.

Hope this helps.

Read more [here.]("http://www.compiz.net/viewtopic.php?id=1927")

---

