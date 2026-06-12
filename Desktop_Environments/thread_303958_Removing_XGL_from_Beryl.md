---
title: "Removing XGL from Beryl"
date: 2006-11-21
forum: Desktop Environments
---

### Post by Lem on 2006-11-21
I have Beryl with Xgl - mainly because I'd upgraded from Dapper/Xgl/Compiz. I'd like to do away with XGL as it does not like mythtv and people are having success with myth and Beryl using edgy's built-in aiglx. (ie. not installing aiglx seperately)

Now I could research back through all the steps I did to get XGL installed and undo, but if someone else has already done the above then I'd be grateful for some guidance notes. Thank you!

---

### Post by superm1 on 2006-11-21
Well the easiest way to do this is to switch back to your default gnome/kde session at login.  

Once your in a clean beryl/compiz less session, take off any extra compiz repos from your /etc/apt/sources.list.

Open up synaptic, search for compiz and remove anything that comes up.
Search for xgl and remove xserver-xgl.
Go to the list of locally installed packages.  Any libgl* named packages may need to be rolled back.  Choose each one and press ctrl-e and choose the version sitting on the edgy repositories.

---

### Post by PriceChild on 2006-11-21
Btw you *should* be able to get into a standard gnome/KDE from the login manager.

Press "Sessions" and choose it from there.

---

