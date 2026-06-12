---
title: "Adding a new screensaver"
date: 2010-05-01
forum: Desktop Environments
---

### Post by CharlieMe on 2010-05-01
I was trying to add new screensaver to Ubuntu 10.04. I believe i put all files in the right place but the preference selection list is not updated even if i logout/in and restart the computer.

The .desktop file is correct as i compared with other existing files.

Anyone can help me plz?

---

### Post by zonky on 2010-05-03
> **CharlieMe said:**
> I was trying to add new screensaver to Ubuntu 10.04. I believe i put all files in the right place but the preference selection list is not updated even if i logout/in and restart the computer.


I'm seeing the same issue. I've added a new screensaver using a different floating image, and the list of screensavers in gnome-screensaver is not updating with my newly named screensaver.

Can anyone help?

---

### Post by zonky on 2010-05-03
Funnily enough, if i edit an exisitng screen saver, in /usr/share/applications/screensavers/footlogo-floaters.desktop to point to my new .svg which file path is correct, then i restarted ubuntu (for arguments sake) the original foot logo is still there!

It seems like any changes made in /usr/share/applications/screensavers/ are not actually used by gnome-screensaver?

---

### Post by jdoklovic on 2010-05-05
I had the same issue and figured out how to add a custom floater screensaver.

I added the .desktop and .svg files to /usr/share/applications/screensavers and /user/share/pixmaps respectively.

This does *not* show up in the screensaver preferences. To get it to show up, you also need to edit the file:

/usr/share/applications/desktop.en_US.utf8.cache

near the very bottom you'll find the screensaver entries. They are exactly the same as the .desktop files and the ini-like header should be: [screensavers/name_of_your_desktop_file]

Once I added an entry, my custom screensaver showed up in the preferences.

Not sure this is exactly the *proper* way to do it, but it works.

---

### Post by zonky on 2010-05-05
Hi, thanks for this- editing this has worked.

---

### Post by damianonly on 2010-06-15
> **jdoklovic said:**
> I had the same issue and figured out how to add a custom floater screensaver.

I added the .desktop and .svg files to /usr/share/applications/screensavers and /user/share/pixmaps respectively.

This does *not* show up in the screensaver preferences. To get it to show up, you also need to edit the file:

/usr/share/applications/desktop.en_US.utf8.cache

near the very bottom you'll find the screensaver entries. They are exactly the same as the .desktop files and the ini-like header should be: [screensavers/name_of_your_desktop_file]

Once I added an entry, my custom screensaver showed up in the preferences.

Not sure this is exactly the *proper* way to do it, but it works.

It worked for me too. This looks like a bug. The "drag and drop" feature that they mention in the gnome screensaver homepage is not working either.

---

### Post by zabuch on 2010-07-10
/usr/share/applications/desktop.en_US.utf8.cache is updated automatically by dpkg. The cleanest and most reusable way I've found to install new screensaver theme is to package it as .deb. I have described it fully on my blog: [http://techblog.zabuchy.net/2010/how-to-create-simple-theme-for-gnome-screensaver/](http://techblog.zabuchy.net/2010/how-to-create-simple-theme-for-gnome-screensaver/) . Enjoy!

---

### Post by brendanpiater on 2010-08-10
Following on from @zabuch comments on "dpkg" updating that list, I just ran a pending update and the list was refreshed to include my new screensaver. I guess installing something from the repos if you don't have an update pending would do the same.

Hope that helps someone.

Cheers
B

---

### Post by jdandison on 2010-08-31
For what it's worth, I moved the desktop.en_US.utf8.cache file (from /usr/share/applications) to my desktop, then edited my .desktop files to change the screensaver preferences. The changes were immediate, i.e., I didn't have to re-open the Screensavers panel - I only had to switch to a different saver, then back to the one I edited. 

Not sure what the implications are of leaving that file out, so I think a diff -> merge may be best now that things are setup the way I want them.

---

