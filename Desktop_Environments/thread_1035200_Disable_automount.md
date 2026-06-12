---
title: "Disable automount"
date: 2009-01-09
forum: Desktop Environments
---

### Post by mesc on 2009-01-09
I would like to disable automount for USB sticks or reconfigure some automount settings. xfc4. It is not Thunar which manages automount.

Any help? No luck with google...

Thank you

---

### Post by Monteaup on 2009-01-27
Also looking for a solution...

I found this...

[http://ubuntuforums.org/showthread.php?t=13692&page=2]("http://ubuntuforums.org/showthread.php?t=13692&page=2")

But it is not working any more. I also removes the gnome-volume-manager but the automount is still active?!

---

### Post by Monteaup on 2009-01-28
This works for me....

You need to edit the /etc/hal/fdi/policy/preferences.fdi

and add this...

  <device>
    <match key="storage.hotpluggable" bool="true">
      <match key="storage.removable" bool="true">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>

---

