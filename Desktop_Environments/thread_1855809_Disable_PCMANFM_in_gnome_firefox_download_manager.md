---
title: "Disable PCMANFM in gnome firefox download manager"
date: 2011-10-07
forum: Desktop Environments
---

### Post by Jack Brown on 2011-10-07
Hi I'm using 10.04 lucid.

installed lxde (not lubuntu-desktop) from repos a while back.  good stuff.

But now, in firefox, right clicking file on download list on gnome default and choosing 'open containing folder'  uses pcmanfm.  And firefox/pcmanfm, doesnt use some of the default programs in gnome default.

(firefox version: 6.0)

Can anyone tell me how to disable pcmanfm in gnome / firefox?
edit: so nautilus will be the preferred file manager when opening containing folder from firefox downloads list.


thanks.

---

### Post by kemtnbkr on 2011-10-08
Hi, I'm running LXDE too, but I haven't the foggiest how to change the default file manager.  I hunted around in the preferences, but of course found nothing.  My only suggestion would be to remove pcmanfm, so the default would then be nautilus (no other option).  However, seeing as I'm almost a total n00b, I'm sure this is a terrible idea, and you'd probably do better to wait for someone who actually knows what they're doing to come along haha.

---

### Post by lovinglinux on 2011-10-10
I don't think you can configure Firefox to use a different file manager. It uses the system default or the built-in file picker.

To make Firefox use the built in file picker, type *about:config* in the address bar, then type *ui.allow_platform_file_picker* in the search field, then double-click the preference to turn it off.

---

### Post by Jack Brown on 2011-10-11
kemtnbkr, thanks for replying.  I just might try uninstalling pcmanfm.  (although i like using it in lxde though, just want nautilus on gnome for other users.)



lovinglinux, i tried your suggestion.  didnt work, firefox still opens folders using pcmanfm.  i just want to use nautilus when im in gnome.  pcmanfm when im in lxde.   EDIT: the ui.allow_platform_file_picker setting is for the window firefox uses to save files, not the one for opening the folder of files already downloaded.

but firefox download list "open containing folder" seems to want to use pcmanfm, although my default in gnome is nautilus.

guess i could probably just use nautilus in lxde? (and remove pcmanfm altogether.)

Anyway, thanks.  This is a minor problem anyway. more like an irritation.

I'll mark the thread as solved.


__

Waiting for final oneiric.  Hopefully it's better/more efficient (than 11.04 <- sluggish, high battery consumer), less bugs, and still works on slightly older hardware...

also have a Pentium4 that would like to try out that oneiric.

---

