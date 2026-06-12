---
title: "user/login error"
date: 2005-11-14
forum: Desktop Environments
---

### Post by Doobiedo on 2005-11-14
ive been having trouble getting ubuntu set up, first x wouldn't load, then i couldn't login so i edited /etc/X11/gdm/gdm.conf file to allow me to login as root. now ive tried to create a new user account but it gives me this

"Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File sould [sic] be owned by user and have 644 permissions"

then it logs me out again.
with this error

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /varlog/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h " " -l ":0" "username"
/etc/gdm/Xsession: Beginning session setup . . .

(gnome - session : 9037): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory '/home/username/.gnome2/': Permission denied

anybody know whats wrong?

---

### Post by Iandefor on 2005-11-15
Not at all. That's really weird. Check the permissions on /etc/X11/gdm/gdm.conf.
To do that, open up /etc/X11/gdm in Nautilus (this assumes you're able to login with GNOME as root), right click gdm.conf. Look at the permissions of gdm.conf.

---

### Post by micsmith on 2005-11-15
I too feel this is a dumb question but just for verification, as I am having similar troubles as well, what permissions are there supposed to be on gdm.conf?

---

### Post by Doobiedo on 2005-11-15
Ive done some digging around and it appears that my /home directory has been installed onto my fat32 partition and i this is causing the problem (lack of multi user support and all)  

can someone show/tell me how to move the home folder onto my main partition without scrambling any data. Thanks

---

