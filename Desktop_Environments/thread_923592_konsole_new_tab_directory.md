---
title: "konsole new tab directory"
date: 2008-09-18
forum: Desktop Environments
---

### Post by H4rm0ny on 2008-09-18
Hi,

I much prefer KDE as a desktop environment, but have one extremely irritating problem with it.

On Gnome, when using the default terminal window, a Ctrl+Shift+T opens a new tab which begins in the same directory as the tab you launched it from. This is extremely useful if you work in the same way I do, from the command line, with very deep directory structures.

The equivalent shortcut in Konsole is Ctrl+Shift+N but this always starts the new tab session in the home directory.

Very irritating! Does anyone know how to configure this to work the same way that the Gnome terminal does?

Thanks,

Harmony.

---

### Post by awakatanka on 2008-09-18
ctrl-shift-n does what you describe for me in konsole. Maybe you need to mark that option in settings > edit current profile

---

### Post by H4rm0ny on 2008-09-18
> **awakatanka said:**
> ctrl-shift-n does what you describe for me in konsole. Maybe you need to mark that option in settings > edit current profile

Thanks. It's good to know that at least this is possible. However, I can't find an option to enable this on mine. I don't even actually have an option for "Edit Current Profile" under the Settings menu (I'm assuming Settings -> Configure Konsole).

If it's not too much trouble, would you be able to post the contents of
```
.kde/share/config/konsolerc
``` here? Then I can grab it and do a diff and see if there's anything you have set that I don't or vice versa. I'm looking through it now but I really can't see anything that would change this behaviour. :(

---

### Post by Denestria on 2008-09-18
I think Awakatanka must be using KDE4?  because KDE3 Konsole does what you describe, ctrl-shift-n opens to home and there is no such option as edit profile.  As far as I know the only way to open a tab to the current directory is to bookmark it and then New Session > Shell At Bookmark.

---

### Post by awakatanka on 2008-09-18
Hmmm sorry i do use kde 4, i'm so used to it that i forget there are people that use kde3.

---

### Post by H4rm0ny on 2008-09-18
> **Denestria said:**
> I think Awakatanka must be using KDE4?  because KDE3 Konsole does what you describe, ctrl-shift-n opens to home and there is no such option as edit profile.  As far as I know the only way to open a tab to the current directory is to bookmark it and then New Session > Shell At Bookmark.

Ah, I did cross my mind as to whether a different version might be in use. I guess it's time to upgrade. I'll do it this weekend.

I had found the Bookmark option. It's sometimes useful, but not sufficient for my needs.

Thanks a lot to you both,

Harmony.

---

### Post by awakatanka on 2008-09-18
> **H4rm0ny said:**
> Ah, I did cross my mind as to whether a different version might be in use. I guess it's time to upgrade. I'll do it this weekend.

I had found the Bookmark option. It's sometimes useful, but not sufficient for my needs.

Thanks a lot to you both,

Harmony.
Becarefull it isn't future complete like kde 3 is.

---

