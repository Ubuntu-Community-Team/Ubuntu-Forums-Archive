---
title: "gnome-keyring problems"
date: 2005-10-30
forum: Desktop Environments
---

### Post by kevinlyfellow on 2005-10-30
I have a some drivespace from my university, and I like to have it mounted on my desktop.  Of course this requires a password to access.  Loging in oneday I decided to click "Save password on keyring"... well after that, every other application I use causes the keyring to pop-up wanting me to login to the server.  So I deleted the settings in ~/.gnome2/keyrings.  I unmounted the drive.  I installed a keyring manager and I hoped I could figure something out there.  I greped for the server that it keeps trying to get my to login into, couldn't seem to find anything.  I dpkg-reconfigure'd gnome-keyring.  I can't seem to figure out anyway to solve this issue.  I'd be very appreciative to anyone who can help.

---

### Post by MichaëlVD on 2005-11-02
I'm having the same problem. Really annoying!

---

### Post by MichaëlVD on 2005-11-07
You can install the gnome-keyring-manager in synaptic. There, you can delete keys.

---

### Post by kevinlyfellow on 2005-11-13
Ok, I got this figured out.  I created a new user and tried to see if I had the same problem.  I wasn't.  So the problem was in my home folder.  So I copied my home folder as the new user's folder and changed permission and whatnot, and low and behold I was having the same problem.  So I deleted folder by folder in the directory until the problem went away.  And I discovered the issue was in the .gtk-bookmarks file.  I had bookmarked the mounted drive probably late at night when I wasn't thinking clearly!  I found that it had the very entry I was looking for that for some reason grep wouldn't find.  I just deleted the entire file.  Now I don't have that issue anymore.  MichaëlVD thanks for the advice, but I had said that I already tried a keyring manager (which was of course gnome-keyring-manager).  So moral of the story, don't bookmark things you need to login to.

---

