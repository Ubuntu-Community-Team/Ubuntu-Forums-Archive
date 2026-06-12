---
title: "Update ruined &quot;look&quot;?"
date: 2005-07-27
forum: Desktop Environments
---

### Post by LokeDK on 2005-07-27
[http://loke.linux.dk/menu.jpg](http://loke.linux.dk/menu.jpg) (My menu)
Compared to 
[http://www.palmbavardages.net/images/ubuntu/cf_003.png](http://www.palmbavardages.net/images/ubuntu/cf_003.png) (How it should look)

I hope you see the difference?
This happened after the latest update, which also included gtk i think? Now gnome is ugly.
I've tried to delete the gnome settings (rm -rf ~/.gnome2 && rm -rf ~/.gconf) But it's still the same. This happened to all themes. They got weird after the update.
Is there a way to undo the update? Perhaps the updates weren't tested?
Please help.

---

### Post by Perfect Storm on 2005-07-27
How exactly weird are we talking about?

---

### Post by DancingSun on 2005-07-27
Looks like it's just yours is displaying English as the locale.  My GNOME desktop looks just like yours.  The other screenshot has the "windows list" added to the top GNOME panel, but this isn't the default setting.  The default has the "windows list" on a separate GNOME panel at the bottom.

Edit:
OK, I see that your highlight is different than mine, it doesn't have that 3D effect...hmm...that's odd.  What kind of update did you do?  I don't recall a system update that has to do with GTK...

---

### Post by LokeDK on 2005-07-27
Yes it's the 3D/highlighted look. I didn't saw all the updates, because there was 24.

But perhaps there was a gtk update, not sure at all.
Would be really nice to have it back  :roll:

---

### Post by man.life on 2005-07-27
sudo apt-get install gtk2-engines-clearlooks/hoary  :)

---

### Post by varunus on 2005-07-27
As man.life said, this is due to an update to the new Clearlooks Engine from backports, which has some new ways of drawing things.  I personally like the new engine, but you can always downgrade the gtk2-engines-clearlooks package from Synaptic.

I think the new clearlooks allows you to have the old menu style, but it requires changes to the theme files...which hopefully the Ubuntu developers will have done by Breezy.

---

### Post by DancingSun on 2005-07-27
[QUOTE=varunus]As man.life said, this is due to an update to the new Clearlooks Engine from backports, which has some new ways of drawing things.  I personally like the new engine, but you can always downgrade the gtk2-engines-clearlooks package from Synaptic.

I think the new clearlooks allows you to have the old menu style, but it requires changes to the theme files...which hopefully the Ubuntu developers will have done by Breezy.[/QUOTE]
Ah, no wonder I don't remember any updates to GTK, it's because I'm on Ubuntu AMD64 and we don't have backports :(

---

### Post by LokeDK on 2005-07-27
Well the gtk2-engines-clearlooks package is installed, and has been installed for a while. Also tried to reinstall it, but no changes.

Don't understand why it stopped working then hmm?

---

### Post by varunus on 2005-07-27
You need to install the original hoary version, not the updated backports version.  To do this, select the package in synaptic, and choose "Package->Force version."  Choose the 0.5 version from the list (the original hoary one).

---

### Post by LokeDK on 2005-07-27
Thank you so much, it worked!  :) 
I've locked the version now.
Thanks again!

---

