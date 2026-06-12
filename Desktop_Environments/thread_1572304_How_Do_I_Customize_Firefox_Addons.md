---
title: "How Do I? Customize Firefox Addons"
date: 2010-09-10
forum: Desktop Environments
---

### Post by mathgeek2000 on 2010-09-10
I'm running Ubuntu 10.04 on my laptop. -- I'm the only user, but I may loan the laptop to trusted guests, and let them use the 'Guest' account. (As it's clean and won't interfear with my stuff)

Since the guest home directory is regenerated each time, that includes Firefox's default profile. -- Here's what I'd like to do --

 ** Add Certain useful Addon's to the default profile -- 
   ex: LastPass, Adblock Plus

So when the default directory is generated, these would be available immediately.
Periodically, as Administrator I might update them so:

 -- Where in the Firefox folders is the default profile stored. -- I know the Ubuntu team customizes it, for example. How can I add to it?

---

### Post by asmoore82 on 2010-09-10
AdBlock Plus in the software repos - this packages does an "admin" install -
installing the extension to firefox itself instead of your personal profile.

---

### Post by -jrosco- on 2010-09-11
When you call the guest session login from the top menu this will run /usr/share/gdm/guest-session/guest-session-setup.sh. You could always edit this shell script to mkdir or copy an firefox temp default profile to the guest temp home directory everytime the guest session is called. Or you could just create a new limited user.
 
JC

---

### Post by lovinglinux on 2010-09-12
[http://ubuntuforums.org/showthread.php?t=1485995](http://ubuntuforums.org/showthread.php?t=1485995)

---

