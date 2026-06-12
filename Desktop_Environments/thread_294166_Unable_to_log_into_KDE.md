---
title: "Unable to log into KDE"
date: 2006-11-06
forum: Desktop Environments
---

### Post by Slace on 2006-11-06
Today I booted my Kubuntu Edgy Eft machine, went to log into KDE but nothing happens.
Well, the screen goes black with a white line down the side and then refreshes back to the log in dialog.

I've tried my different kernels but to no availe (which isn't really supprising).

I haven't done any installed receintly, I did try and install ndiswrapper from source, but I've uninstalled it, with no change.

Any idea as to why I can't log in?

---

### Post by wieman01 on 2006-11-06
Perhaps the harddisk is full. You could try deleting everthing that's in "/tmp":
> cd /tmp
sudo rm -r *
Not sure if that helps.

---

### Post by Slace on 2006-11-06
nope didn't help :(

---

### Post by Slace on 2006-11-06
I've just tried a re-install of KDE (removed kubuntu-desktop, kde and kde-core and reinstalled those three) all to no avail, I still have the same problem


*edit - no it was a problem with my hard drive being full...

---

### Post by wieman01 on 2006-11-07
Was your harddriver full after all? Just saw your "edit"...

---

