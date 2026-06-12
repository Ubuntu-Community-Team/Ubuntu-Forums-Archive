---
title: "&quot;Open as root&quot; script fails since upgrade"
date: 2006-07-08
forum: Desktop Environments
---

### Post by maxweld on 2006-07-08
Since upgrading to Ubuntu 6.06 from 5.10 my "Open as root" script no longer works??

I have the file "Open\ as\ root" still in my nautilus-scripts folder, with the following contents and permissions set to execute:

[FONT="Courier New"]for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done[/FONT]

Any thoughts?

---

### Post by scxtt on 2006-07-08
it's possible that either $NAUTILUS_SCRIPT_SELECTED_URIS or $uri aren't valid variables anymore, gnome-sudo has been replaced, or gnome-open has been replaced ...

---

### Post by maxweld on 2006-07-08
Ok Thanks

gnome-sudo seems to have been replaced by gksudo. New script should be:

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
   gksudo "gnome-open $uri" &
done

Works a treat. Do not forget to make it executable.

---

