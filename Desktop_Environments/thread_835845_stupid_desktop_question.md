---
title: "stupid desktop question"
date: 2008-06-20
forum: Desktop Environments
---

### Post by akahige on 2008-06-20
I'm running VMware on Hardy, and for whatever reason, the keybindings -- including the ability to use SHIFT or CTRL -- get randomly hosed. I suspect that the issue is more with the way VMw interacts with X, rather than the specific window manager. Had this problem on XFCE and it still happens with Gnome.

The only fix that I've found is to log out of the desktop and log back in (if not totally reboot).

Since it can be rather time consuming to shut down all the running apps, I'm wondering if there's any way to leave things running and have them come back after whatever process logging out of the desktop actually involves.

---

### Post by pytheas22 on 2008-06-20
If you go to System>Preferences>Sessions, under the Session Options tab you can check the box to remember running applications when you log out.  Then they will be restarted automatically the next time you log in.  However I've found that most applications don't work well with this feature; they will start back up, but they won't load the files you were working on--so for instance OpenOffice writer might start back up automatically, but there won't be any documents open and I'll have to manually open the ones I was working on before the logout.  But at least it's better than having to start every application back up as well as open your files again.

A better solution would be figuring out what's going on with vmware.  Unfortunately I can't help you there as all my experience on Linux is with VirtualBox, but I hope someone else can.

---

### Post by akahige on 2008-06-20
I don't think the session option is going to play nice with VMware. In fact, I'd pretty much guarantee that it won't -- which is why I was thinking if it could be *left* running without any ill effects, everything might be okay.

Re. the problem with VMw... I totally agree with you that solving the problem would be ideal, but they won't even acknowledge that there's a problem -- and I've seen reports of similar behavior going back years.

---

### Post by pytheas22 on 2008-06-21
> I don't think the session option is going to play nice with VMware. In fact, I'd pretty much guarantee that it won't -- which is why I was thinking if it could be *left* running without any ill effects, everything might be okay.

I didn't realize that you wanted to keep VMware running while the X server is restarted.  I thought you just wanted to not have to open all your applications again.  I agree that there's probably no way to do that, because I don't know how you could keep your virtual machine running without X.

> I totally agree with you that solving the problem would be ideal, but they won't even acknowledge that there's a problem

Give VirtualBox a try then? or qemu, xen...

---

