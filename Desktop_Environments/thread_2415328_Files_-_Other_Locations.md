---
title: "Files - Other Locations"
date: 2019-03-24
forum: Desktop Environments
---

### Post by Geoff_Lane on 2019-03-24
Folks,

Running Ubuntu 18:04 LTS

Have an issue when I access 'other locations' on my local network. I have an sftp://192.168.1.12/ locations which logs me in to the root location via my ssh credentials. This is fine as this device is used as a media server which I access via the /media directory.

So far so good.

If using the files v3.26.4 manager I then switch to any local folders when I return to my network share in puts me in the 'home' folder and not the 'root'. Can see no way of opening parent folder, no obvious way of entering a filepath.

The only way I can appear to get back is either pressing back button continuously r re-establishing my sftp connection.

Previous version of Ubuntu I could open a location text window which would allow me to enter / but if there is one here I haven't found it.

If anyone has a suggestion appreciate advice.

Geffers

---

### Post by CatKiller on 2019-03-24
> **Geoff_Lane said:**
> Can see no way of opening parent folder, no obvious way of entering a filepath.
I haven't used Gnome for quite a while, but Ctrl-L used to bring up the location bar. It probably still does.

---

### Post by Dennis N on 2019-03-24
> If using the files v3.26.4 manager I then switch to any local folders when I return to my network share in puts me in the 'home' folder and not the 'root'
Make a bookmark for the remote root directory. Then you can easily return there.

---

### Post by Geoff_Lane on 2019-03-25
> **CatKiller said:**
> I haven't used Gnome for quite a while, but Ctrl-L used to bring up the location bar. It probably still does.

Thank you very much - that works.

Geffers

---

### Post by Geoff_Lane on 2019-03-25
> **Dennis N said:**
> Make a bookmark for the remote root directory. Then you can easily return there.

Thank you for reply, I did have a shortcut to get me to the initial location, it was just the option to go back a directory that I needed but suggested Ctrl-L would suffice and it did.

Geffers

---

### Post by Dennis N on 2019-03-25
This may be obvious, but I would add that just using multiple tabs and multiple file manager windows would get around the use of the arrows to access last-viewed folder on the other machine. One widow on the local, and another on the remote machine.

---

