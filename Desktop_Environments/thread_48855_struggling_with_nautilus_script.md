---
title: "struggling with nautilus script"
date: 2005-07-14
forum: Desktop Environments
---

### Post by pabc on 2005-07-14
I have the following in as a file in the ~/.gnome2/nautilus-scripts folder

[COLOR=Blue]for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-terminal --command="nzbget -n $uri" &
done[/COLOR]

and it shows up fine in nautilus as a script in the right click menu. It is supposed to open a gnome-terminal then run nzbget -n on the selected file. However gnome-terminal just opens and closes. 

Any idea on what I'm doing wrong?

P

---

### Post by pabc on 2005-07-14
on the off chance someone else has this problem....

the promlem was that the $NAUTILUS_SCRIPT_SELECTED_URIS is of the form file:///filename which nzbget doesnt like hence the openm/close from gnome-terminal I was seeing.

using;
[COLOR=Blue]gnome-terminal -t nzbget -x nzbget -n ${uri:7}[/COLOR]

instead to remove the first 7 characters (file://) and all works fine.

P

---

