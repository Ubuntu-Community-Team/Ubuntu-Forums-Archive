---
title: "Monitor Power Save"
date: 2008-06-19
forum: Desktop Environments
---

### Post by cowsong on 2008-06-19
I am running xubuntu and have found that my monitor goes into power-save mode after approximately 10 minutes of inactivity.

Can someone please tell me where I can find the setting to extend this value?

I am quite comfortable with the command line, so am happy to edit files if necessary :)

Thanks!

---

### Post by mali2297 on 2008-06-19
Do you use a screen saver? If so, check its settings first.

In addition, X itself is set to blank the screen after 10 minutes. You can edit this behavior in xorg.conf. 
See [http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html)

---

### Post by cowsong on 2008-07-20
Thanks for the info, Martin.

Sorry for taking so long to reply. I tried several variations on the information you linked to and now have it working.

For anyone else interested in this thread, as far as I can work out, the trick appeared to be that I needed the entire ServerFlags section in my xorg.conf:

Section "ServerFlags"
    Option "BlankTime" "30"
    Option "StandbyTime" "90"
    Option "SuspendTime" "120"
    Option "OffTime" "180"
EndSection

My earlier attempts excluded OffTime and/or some other values, but it did not appear to work until I included all the options as above.

---

