---
title: "Changing W:ET resolution?"
date: 2012-04-15
forum: Gaming &amp; Leisure
---

### Post by hanghell on 2012-04-15
How do I change the resolution of Wolfenstein: Enemy territory? I can not run the game since my monitor does not support the default resolution, so I do not have access to the console.



Thanks.

---

### Post by dmn_clown on 2012-04-17
> **hanghell said:**
> How do I change the resolution of Wolfenstein: Enemy territory? I can not run the game since my monitor does not support the default resolution, so I do not have access to the console.



Thanks.

It's not your monitor, it's X.org showing how user friendly it really is, anyway:

```
./et +set r_fullscreen 0
```

Set the resolution you want in windowed mode then go back to fullscreen.

---

