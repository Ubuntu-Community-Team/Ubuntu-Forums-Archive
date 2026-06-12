---
title: "Wine issue"
date: 2009-02-12
forum: General Help
---

### Post by shak3800 on 2009-02-12
Hi ! I've recently uninstalled wine by removing it through add/remove and by deleting the .wine folder . Also because some programs could not disappear from the wine menu , i manually removed them through System > Preferences > Main Menu . When i decided to reinstall Wine , i noticed that the programs (name of the programs) wouldn't show up on the Wine menu , and i had to go through drive_c find the folder of the installed application and run it from there . I know it's not a big issue but is there a way to make the programs name show up like it used to on the Wine menu ?

Thanks a lot for your help ! :guitar:

---

### Post by mc4man on 2009-02-12
Depending on what you actually did and have done since it may be very easy, simply deleting ~/.config/menus/applications.menu, and then clicking on Applications can in many instances restore the menu items.

You may want to take a look inside first with cat. (If you edit wrong in there you'll have to delete it in any case.

```
cat ~/.config/menus/applications.menu
```

If you see wine programs listed with a deleted in the listing then you can either carefully edit out the <Deleted/> only or just delete the whole file itself.

Post it if you wish, but if the entries are there then you can just browse to ~/.config/menus/ and delete the applications.menu file.

---

### Post by shak3800 on 2009-02-12
Wow it worked ! :) The wine programs menu had <Deleted/> in the listing ,i edit it and it worked . Thanks a lot for your help !! :)

---

