---
title: "Nautilus 2.22 Unable to successfully navigate directory tree"
date: 2008-04-26
forum: Desktop Environments
---

### Post by briareos on 2008-04-26
I've been experiencing this problem since upgradign to Hardy yesterday. Nautilus is failing to successfully display contents / change directory in location bar , whenever i try to navigate to subfolders of a certain directory (with about a gig of image files) while nautilus is still generating thumbnails. 

Suppose there is a Directory A with sub directory B containing subdirectoriey C
A and C are containing large number of images / (thumnailable files)

[     ~     ]      
      |
[Directory A]*
      |
[Directory B]
      |
[Directory C]*

i enter A and while nautilus is busy thumbnailing the large number of images in A, i doubleclick and navigate to B. Now nautilus navigates to B but fails to change entry in location bar(ie it reads ~/A). Also clicking on [UP] navigates to parent directory of A.

now i navigate to C from B and while the thumbnails are still loading i click on the [UP] icon in the main toolbar. Here again nautilus navigates(apparently) to directory B, but the entry in teh location bar remains unchanged (i.e it still reads ~/A/B/C). Now if i click on icon of folder C nothing happens. Clicking on [UP] again navigates again to folder B this time changing the entry in the location bar to ~/A/B. 

Is there any way to fix this ? Is this a nautilus bug ?
Thanks in advance :)

---

### Post by briareos on 2008-05-04
Bump! does anyone else have this problem ?

---

