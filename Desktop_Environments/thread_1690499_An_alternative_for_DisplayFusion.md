---
title: "An alternative for DisplayFusion"
date: 2011-02-18
forum: Desktop Environments
---

### Post by Viper92Z on 2011-02-18
I use dual monitors and it's extremely important to me to arrange them and keep 'em reliable. So I have been looking for an alternative for DisplayFusion on ubuntu since 1 year but I couldn't find any good result, if you know any sort of good drivers or programs to arrange the desktop and scale backgrounds perfectly, post them and thanks in advance.

---

### Post by sean.nautica09 on 2011-02-25
Same here. Any help with this area??

---

### Post by Rebootkid on 2011-03-26
Never used DisplayFusion in Windows, but a quick look at their website doesn't seem to be that much different than using Twinview.

I've got an NVidia card, and use the Nvidia specific tool. To accomplish what I think it does, do the following:
run 'gksu nvidia-settings' 
You'll need your password as we're modifying X-Window stuff.
Click on 'XServer Display Configuration' in the left hand navigation pane.
In the right hand pane, click your secondary monitor and click the "configure" button. Choose the "Twinview" radial button.
Click "OK"
Click "Save to X Configuration File"
Click "Save"
Log out of your system. When you log back in, your two desktops will be separate. Now just add in the toolbars at the locations you want, on the appropriate desktop.

If I've misunderstood what you're trying to accomplish with the tool, I apologize. Let me know what you're trying to do, and maybe I can help more.

---

