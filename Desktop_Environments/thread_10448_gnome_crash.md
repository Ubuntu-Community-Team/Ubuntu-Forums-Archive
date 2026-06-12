---
title: "gnome crash"
date: 2005-01-07
forum: Desktop Environments
---

### Post by techn9ne on 2005-01-07
I can get to login screen but whenever I login it gives me this error:

gnome-session: 5772: **Warning** Unable to read ICE authority file /home/jeremy/.ICEauthority

and logs back out. What is this file can I tell it to make a new default one somehow?

---

### Post by rider343 on 2005-01-07
log em terminal mode e enter this:

sudo chown user:user .ICEauthority

it's a k3b bug...

---

