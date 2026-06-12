---
title: "compiz no longer works"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by lxowle on 2007-10-08
Hi there, 

I'm using gutsy. Until I installed the latest updates, compiz was working fine on my computer. After installing the updates, it no longer works (the window borders have vanished, and gtk-window-decorator --replace won't replace them, nor will switching to metacity, and then back to compiz)

Could someone tell me how I can move back to an older version of compiz (i.e., the one I was using yesterday)?

Thanks very much.

---

### Post by Mayfairy on 2007-10-09
I'm having just the same problems. I remember having those tuxfamily updates waiting in my update manager for a long time. Finally I gathered enough courage to install them and BAM! they didn't work. 
Just disabled tuxfamily from my sources.list and going to reinstall compiz.

---

### Post by lxowle on 2007-10-09
Sorry, I'm new to linux - what is tuxfamily?

---

### Post by lxowle on 2007-10-09
OK - I just tried rerunning the update manager and it said there was some sort of error and that I had to run "sudo dpkg --configure -a"

So, I did that, then re-ran the update manager and rebooted.

On a restart, my windows were borderless, but on running metacity, and then reactivating compiz using the System | Preferences | Appearance manager, the borders reappeared and compiz is seemingly fixed.

I don't know if the fix was due to a new version of compiz, or because my last update was interrupted. In any event, it works again.

Thanks.

---

