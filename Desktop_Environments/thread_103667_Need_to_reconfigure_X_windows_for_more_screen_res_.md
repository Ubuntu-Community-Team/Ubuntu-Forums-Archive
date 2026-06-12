---
title: "Need to reconfigure X windows for more screen res options"
date: 2005-12-14
forum: Desktop Environments
---

### Post by tagg3rx on 2005-12-14
Hi all,
    Hopefully this is a quick easy one.
    When i first installed ubuntu i chose only to have a few screen res options - now i want to go back and add more options.  How do I do this.

Thanks,

---

### Post by Qrk on 2005-12-14
You probably need to change the driver for more options... the gnome app lists all the avaible options for your driver. Use

sudo dpkg-reconfigure xserver-xorg

to choose between drivers. Best bets are the propietary ones supplied by the maker of your graphics cards. Ati and nvidia both have drivers avaible, and at least nvidia's are easy to get to work. There is a lot of documentation avaible for them as well.

---

### Post by tagg3rx on 2005-12-14
"the gnome app lists all the avaible options for your driver. Use"

Yes thats the case on my 2nd pc i installed it on becayse during the install I didnt specificaly choose what resouloutions i wanted visible.  However on my 1st run through I didnt realize if i didnt check any resouloutions xwindows would show all avialable.

I'll try reconfiguring xserver

Thx

---

### Post by tagg3rx on 2005-12-14
yup that did the trick thx

---

