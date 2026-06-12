---
title: "Global KDE Desktop Settings"
date: 2006-11-09
forum: Desktop Environments
---

### Post by Greslore on 2006-11-09
Greetings.  

I am currently setting up a public machine image with Kubuntu.  I am customizing the KDE Desktop to the way it should be for all users logging in.  (Via LDAP).  How exactly do I make these changes global for all users logging in?

I am adding stuff like shortcuts to apps, mapped windows drives, wallpaper, etc. 

I tried searching, but no luck.

---

### Post by TheWizzard on 2006-11-09
> **Greslore said:**
> Greetings.  

I am currently setting up a public machine image with Kubuntu.  I am customizing the KDE Desktop to the way it should be for all users logging in.  (Via LDAP).  How exactly do I make these changes global for all users logging in?

I am adding stuff like shortcuts to apps, mapped windows drives, wallpaper, etc. 

I tried searching, but no luck.

try kiosk tool

---

### Post by Greslore on 2007-07-27
I realize this is an old thread, but figure I would post an update.  I gave kiosk tool a try, and it worked great for local users.  I found that when I tried to log in as an LDAP user with their NFS mounted home, kiosk tool did not work.

What I did:
Created a local user called kdetemplate.  I set this user up exactly how I want all the other user's KDE Desktop to be.  I then copied /home/kdetemplate/.kde to /usr/local/

I then modified /etc/profile:
cp -R /usr/local/.kde $HOME
chown -R $USER $HOME/.kde
chgrp -R $USER $HOME/.kde

And viola!  That did the trick.  Now, every time a user logs in, their desktop will be copied and reset to the template.  So far, so good.

---

### Post by ingo on 2007-12-05
Sounds like a decent plan. Where did you get all the info from like what is in /etc/profile? I am after that kind of info - where are all the files that a KDE desktop calls on when in use. So far I've found some KDM, Ksplash and kthememanager stuff, but nothing about /etc/profiles :)

Thanks in advance.

---

