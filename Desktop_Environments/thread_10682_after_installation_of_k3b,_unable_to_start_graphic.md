---
title: "after installation of k3b, unable to start graphical session"
date: 2005-01-10
forum: Desktop Environments
---

### Post by largo on 2005-01-10
After i installed k3b and the cdrdao library, I cant login to a graphical session anymore. I'm getting the error the session only lasted for 10 seconds blablabla. when I view the the details. It sais there is a problem in the /home/myuserfolder/.ICEAuthority some file acess problem. There is no problem with a console based session. Is it possible to restore the old backed up home folder..? Or waht could i do?

---

### Post by droebbel on 2005-01-10
log in on a text console (get there with ctl-alt-F1) and do
$sudo chown <your-user>:<your-group> .ICEauthority
And do not run kde programs via sudo anymore... using a root terminal works better, I think.

---

### Post by largo on 2005-01-10
thanks a lot, but ho do i get the group I'm in? I have no idea which group i created my user in (its the standard user, which i created during the installation)

---

### Post by rider343 on 2005-01-10
the group have the same name of your user

---

### Post by wallijonn on 2005-01-10
That would be

[COLOR=Red]sudo chown largo:largo .ICEauthority[/COLOR]

for example.

---

### Post by Quest-Master on 2005-01-10
Oh man. I wish I knew about this earlier.

I totally reinstalled my Ubuntu because of this. :\ I was in the exact same spot too.. installed k3b and wha-lah, dead Gnome.

XFCE still worked though. ;d

---

