---
title: "Indicator area configuration (Unity)"
date: 2011-05-21
forum: Desktop Environments
---

### Post by pepribal on 2011-05-21
Hi all,

I just wanted to know if it's possible to remove icons from the indicator area in the Unity bar (specifically the one with the envelope and the one with your user name).

Thanks.

---

### Post by Copper Bezel on 2011-05-21
The indicator area itself is passive and will display any service that wants to be displayed, so long as it uses the right indicator spec. However, you can remove the services themselves.

```
sudo apt-get remove indicator-messages indicator-session
```

---

### Post by pepribal on 2011-05-21
Ok, thanks.

---

