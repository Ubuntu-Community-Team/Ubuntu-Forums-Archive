---
title: "Ubuntu 9.04 install cd splash.pcx + my logo ?"
date: 2009-05-31
forum: General Help
---

### Post by shaft on 2009-05-31
Hey!

I need to make my own install cd iso image with custom logo in install menu screen...
What i need to edit and how to do it?

I have edited splash.pcx and splash.png but nothing... It shows me black background only... how can i do it and after that how to create an iso image? 

Thanks a lot!

Regards,
Shaft 

P.S.: I already made edited it with GIMP on my slackware, but i will do it on ubuntu if it is necesary :) 
Sorry if this is not the right forum!

---

### Post by wanchai on 2009-05-31
Here is a guide to produce your own live CD:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

And this post has some instructions on how to create your own boot splash (Items 6 - 8):
[http://ubuntuforums.org/showthread.php?t=622018](http://ubuntuforums.org/showthread.php?t=622018)
But that's the logo that shows when you boot an installed Ubuntu.

I do not know how to change the logo that is shown while the CD boots. Maybe replacing the files you found is enough, maybe you also need to rebuild the initrd that's used when the CD boots. Either way, the images need to be indexed with a maximum of 256 colors.

---

### Post by jonathanysp on 2009-05-31
mm im not sure if this works in slackware but startup-manager can help you change your usplash screen

---

### Post by shaft on 2009-05-31
Yeah! I did it by replacing the files with others with indexed colors 256 max... 
Thank you so much! :)

Regards

---

