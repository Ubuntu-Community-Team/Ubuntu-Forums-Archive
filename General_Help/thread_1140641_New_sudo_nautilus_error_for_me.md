---
title: "New sudo nautilus error for me"
date: 2009-04-27
forum: General Help
---

### Post by Dondo on 2009-04-27
tried typing "sudo nautilus" and ended up with this:

[I]dondo@Ubuntu:~$ sudo nautilus
[sudo] password for dondo: 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:1357:cool:: WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root
--> file:///root/Desktop
--> file:///

(nautilus:1357:cool:: Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 3 elements at quit time (keys above)

(nautilus:1357:cool:: Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time
dondo@Ubuntu:~$ [/I]     

What did I miss?

Dondo

---

### Post by kanikilu on 2009-04-28
It looks like you have the [nautilus-share package]("http://packages.ubuntu.com/jaunty/nautilus-share") that for some reason only suggests, but doesn't require samba.

If you haven't done it already, you'll need to install samba to be able to take full advantage of that package...

```
sudo apt-get install samba smbfs
```

---

### Post by mc4man on 2009-04-28
You should use gksudo nautilus  instead.

If it's doing what's expected (allowing you to open directories with root priv.'s) then you can just ignore the 'warnings'

They're  irrelevant to what your probably doing
( IIRC the # of elements stuff = the # of directories you've opened plus 1 

You'll only need samba ect. if your sharing

---

