---
title: "Problem on GNOME startup"
date: 2006-07-25
forum: Desktop Environments
---

### Post by FrederikVds on 2006-07-25
When booting up, between the point where I press enter after giving my password, and the screen becomes brown, and the point where it show the dialog with metacity, etc loading, Ubuntu (seems to) do nothing for about a minute.

I can't find the reason.
I guess a good start would be logs. Is that part of bootup logged anywhere?

---

### Post by FrederikVds on 2006-07-26
I found the problem.
I accidentally removed
auto lo
from /etc/network/interfaces

---

