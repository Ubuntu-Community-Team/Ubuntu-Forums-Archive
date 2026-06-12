---
title: "Can't Open Any Folders"
date: 2007-07-06
forum: Desktop Environments
---

### Post by WieboJJ on 2007-07-06
I am Using Ubuntu 7.04 and all things where fine, but now suddenly I do not seem to be able to open any folders.

 Running $ nautilus in terminal just hangs with no error messages

      Before this had happened I was trying to get the mouse-over preview of mp3s to work, and so had installed mpg321 and vorbis-tools. Removing both of these did not fix anything. 

      Any Ideas? I can still access my files, but only through the terminal or software...


Thanks allot,

---

### Post by Lolicon on 2007-07-06
Reinstall Nautilus?

---

### Post by WieboJJ on 2007-07-06
Did an apt-get remove nautilus

than reinstalled after reboot

nothing changed, still no response when trying to open any folder. 

     Trying to open the "home" folder results in a tab on my task bar saying that it is starting my Home Folder, but than after 15-20 seconds the tab dissapears, and nothing is started.

Only other thing Updated today other than installing the packages mentioned above was and update to compiz. I have compiz fusion installed with packages from trevinos repository...But i Just logged in in a non xgl session and had the same problems, so I do not think my problem has anything to do with compiz.....

Any one ever heard of this happening before?

---

### Post by WieboJJ on 2007-07-06
My solution to this was to install thunar.

I than made it my default manager with the script on this page:

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

Still have no idea why this happend, but I wasnt all that attached to Nautilus anyway, and Thunar seems run a tad bit faster on my system anyway.

This was still odd. Have no clue why Nautilus bummed out on me. Weird.

---

