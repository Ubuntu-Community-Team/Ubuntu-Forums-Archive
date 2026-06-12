---
title: "Force certain packages to never update?"
date: 2006-06-01
forum: Desktop Environments
---

### Post by evilhomer on 2006-06-01
Just used the font patches from this thread: 

[http://www.ubuntuforums.org/showthread.php?t=178737&highlight=dramatically](http://www.ubuntuforums.org/showthread.php?t=178737&highlight=dramatically)

I don't want libcairo, libxft and their -devs to update, but I'm not sure how to keep adept-updater from prompting me each time.

Can this be done?

Thanks.

---

### Post by panurge77 on 2006-06-01
You can use 'lock version' in Synaptic, but that will only work for synaptic.

---

### Post by bjc on 2006-06-02
[QUOTE=evilhomer]Just used the font patches from this thread: 

[http://www.ubuntuforums.org/showthread.php?t=178737&highlight=dramatically](http://www.ubuntuforums.org/showthread.php?t=178737&highlight=dramatically)

I don't want libcairo, libxft and their -devs to update, but I'm not sure how to keep adept-updater from prompting me each time.

Can this be done?

Thanks.[/QUOTE]

I haven't used it myself, but take a look at ```
man apt_preferences
``` or section 3.10 of [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html) . :-)

---

### Post by evilhomer on 2006-06-06
ah, that did it.  excellent!  thanks.

---

### Post by evilhomer on 2006-06-06
actually, adept-updater still prompts to change.  it just doesn't actually do it, unless i change the package status.  which is great of itself, buuuut -

this doesn't let me know when i have updates, because adept-updater still sits in the tray either way.  i have to mouse over and know how many packages i've blocked.  i'm hoping there's a way to have adept-updater not be in the tray when i've blocked packages from updating.

---

