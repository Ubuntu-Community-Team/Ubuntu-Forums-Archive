---
title: "Wine menu on MATE desktop messed up"
date: 2012-02-23
forum: Desktop Environments
---

### Post by iip on 2012-02-23
Hi All,

Just install MATE desktop and found that Wine menu was gone, and all Wine menu has been moved to 'Other' menu, with no submenu, anyone know how to fix it?

Thanks,

-iip-

---

### Post by iip on 2012-05-18
it works now, edited /etc/xdg/menus/mate-applications.menu, and add <MergeDir> after <DefaultMergeDirs/> as below:

<DefaultMergeDirs/>
<MergeDir>applications-merged</MergeDir>

and then do 

ln -s ~/.config/menus/applications-merged ~/.config/menus/mate-applications-merged
 

it solved for now, all installed wine menu now inside wine-programs.

---

