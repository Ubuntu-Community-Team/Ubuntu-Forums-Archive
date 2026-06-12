---
title: "Firefox errors (GLib-GObject-CRITICAL)"
date: 2006-02-17
forum: Desktop Environments
---

### Post by palomar on 2006-02-17
My firefox install looks a bit broken. The scrollbar and some toolbars are a little buggy (but still usable). I've checked the following:

- Deleted my Firefox-profile (~/.mozilla). No results.
- Changed to other KDE-themes/settings. No results.
- Created new user account and logged into KDE. Firefox looks actually fine with this account. No buggy scrollbars/toolbars.
- Started Firefox from my own account from console. FF starts as usual, but giving the follwing messages in console:

```

(Gecko:10244): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(Gecko:10244): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(Gecko:10244): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(Gecko:10244): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```
And a few more errors like that... 

When I start firefox with the newly created account I get NO errors in console. And Firefox looks good. No buggy scrollbars etc.

My question: what causes this errors and buggy scrollbars/toolbars? I think it has something to do with my user account, because with the other account it works fine.  A quick and dirty way to solve it is to trash my original KDE account and create a new one, but that's not a real sollution ;)

Maybe it's worth to say I have recently upgraded Firefox 1.0.7 to 1.5.0.1 using [this](https://wiki.ubuntu.com/FirefoxNewVersion) tutorial. But I don't think that caused the problem, because of the fine working other account.

What to do?

Specs:
- firefox 1.5.0.1
- Kubuntu 5.10

---

### Post by palomar on 2006-02-18
pls help ...

---

### Post by palomar on 2006-02-18
I think I have found a sollution.

If I delete the file ~/.gtkrc-2.0 Firefox actually runs fine again without scrollbar bugs and errors in console :)
When I go to KDE system settings -> appearance -> GTK styles & fonts and change something (font or style) the error comes back again.

Is this a bug?

I have upgraded my kubuntu 5.04 to 5.10 some time ago. Maybe this has to do with it?

---

