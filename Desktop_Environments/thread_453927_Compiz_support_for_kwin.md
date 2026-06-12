---
title: "Compiz support for kwin?"
date: 2007-05-24
forum: Desktop Environments
---

### Post by loathsome on 2007-05-24
Hi there,

Just wondering .. is there any way to make Compiz support Kwin? (KDE's window manager)

Thanks.

---

### Post by loathsome on 2007-05-25
Bumpeh ..

Nobody knows anything?

---

### Post by mannheim on 2007-05-25
Here's a not-very-well-informed answer. Compiz is a composite manager **and** a window manager. Kwin is a window manager. You can't have two window managers running, so you can't have both compiz  and kwin.

There is a separate question about window decoration though (the title bar etc.). Traditional window managers like kwin combine the function of a window decorator. In compiz, the job of decorating the windows is handled by a separate application, and there are choices for this app. Compiz comes with a decorator called kde-window-decorator, and you can use that combination to get kwin themes on your compiz desktop.

But (as far as I know), if you want kwin because of its cusomizable window-managing features, then you can't have those with compiz.

---

### Post by loathsome on 2007-05-25
Great, exactly what I was looking for! Thanks a lot!

---

