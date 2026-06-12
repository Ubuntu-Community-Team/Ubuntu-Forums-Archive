---
title: "fake transparency with cairo dock??"
date: 2008-12-02
forum: General Help
---

### Post by rixtr66 on 2008-12-02
I am currently running ubuntu studio 8.04,and for some reason it doesnt
get along with compiz.compiz also messes up blender!
any way,im wondering if there is a way to fake the transparency of the 
black background without using compiz?
any input is welcome and appreciated!
Rick):P

---

### Post by kawaji on 2008-12-02
Is Gnome Metacity a default window manger for Ubuntu Studio desktop ?
then, run the following command to use real transparency.
```
$ gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```
for disabling the compositing option
```
$ gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```

If you feel a desktop operaton performance is slower when the compositing-manager is enabled, you can find a fake transparecy option in System tab of cairo-dock setting panel, but the option makes cairo-dock to keep below other windows.

---

### Post by rixtr66 on 2008-12-03
excellent!!it works fine.still interferes with blender though?
Thanks for the tip!
Rick:D
ps;yes metacity is the default wm!

---

