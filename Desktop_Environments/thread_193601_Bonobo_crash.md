---
title: "Bonobo crash"
date: 2006-06-10
forum: Desktop Environments
---

### Post by fonsv on 2006-06-10
After a lengthy ;) upgrade to dapper, I now have most things working. When logging in my theme gets swapped back and forth between default and my preferred one. After a while I get the following message:

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

When trying to access the theme manager I get the same, and Firefox crashes then as well.
I tried reinstalling everything Bonobo I could find. Also, I tried starting gnome-settings-daemon manually, which only results in more swapping of themes and finally in the following error (preceeded by some strange characters):

'OIL: ERROR liboiltest.c 359: oil_test_check_impl(): illegal instruction in mt19937_i386_mmx_3
Illegal instruction.

Also, I found on some other, French forum that this last error is also related to a problem in which ALSA refuses to work. I did not get ALSA running at first, as I compiled from source it worked.

Okay... Anybody any idea what to do next? How can I get bonobo to work?

I am using an Pentium 2, 400 with 392 ram.

Thanks,

Fons

Okay, I just fixed my problem, with a work around. Hopefully someone can find a nicer solution...
I figured out the problem was with the liboil0.3 library. I went to synaptic and downloaded liboil0.2, of course it was not possible to deinstall liboil0.3 due to dependencies... This did not work.
I renamed my two liboil0.3 files (found in /usr/lib), and made a link to with the original name to the liboil0.2 files... Now it works. Of course, it is totally insane to do this. But for now I am happy with this 'solution'. If anybody figures out how it might be working with liboil0.3 please tell me.

Thanks alot.

Fons

---

