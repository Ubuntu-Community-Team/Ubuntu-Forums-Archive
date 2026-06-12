---
title: "UIM problems"
date: 2006-05-11
forum: Desktop Environments
---

### Post by Kashirigi on 2006-05-11
Hi everyone,

I'm having an annoying problem with uim-applet-gnome and (by association) uim-pref-gtk.

It was working perfectly, now it stopped. Now my uim-applet-gnome just has a small x instead of it's usual functioning interface, it can't be removed from the panel, and configuring it results in a perpetual lockup.

When I run uim-pref-gtk (which I assume the applet is trying to do as well), I get this endless loop:
>>(custom-group-desc (quote preedit))
>>(custom-group-desc (quote preedit))
>>(custom-group-desc (quote preedit))
>>(custom-group-desc (quote preedit))
>>(custom-group-desc (quote preedit))
>>(custom-group-desc (quote preedit))
>>(custom-group-desc (quote preedit))
>>etc.

Unsurprisingly, I suspect it's related to this:
[http://lists.freedesktop.org/archives/uim-bugs/2005-August/000456.html](http://lists.freedesktop.org/archives/uim-bugs/2005-August/000456.html)

Sadly, being less than completely adept at linux,  I don't have the slightest idea where  LIBUIM_VERBOSE is, or how I would go about setting it to be something else, (like LIBUIM_VERBOSE = NotQuiteSoVerbose or LIBUIM_VERBOSE = QuietUntilAfterAFewDrinks) ostensibly fixing my problem.

That, and if I use the ubuntu repository version of libuim0, it causes a segfault in glGo. I theoretically solved that by using the Debian unstable version of libuim0. Everything was fine for a while, and then, pff.

Thanks for any help you can provide.

---

