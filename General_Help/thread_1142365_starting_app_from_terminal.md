---
title: "starting app from terminal"
date: 2009-04-29
forum: General Help
---

### Post by davidx300 on 2009-04-29
Hi!

When i start an application from terminal example: firefox &, the application closes when i close the terminal. The & character at the end of the app's name is not working. This happens with all app's.

But it did work a while a ago. I think i didn't changed any settings.

Any help would be appreciated.

---

### Post by kpkeerthi on 2009-04-29
Thats how it always worked. To stop that from happening, you should **disown** the application from the shell
```

firefox&
disown

```

---

### Post by 3rdalbum on 2009-04-29
Some programs will disconnect from the terminal, some will not. That's always been how it works; but the disown trick is useful to know.

---

### Post by davidx300 on 2009-04-29
OK, thanks guys.

---

