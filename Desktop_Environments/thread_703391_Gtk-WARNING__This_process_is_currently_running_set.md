---
title: "Gtk-WARNING **: This process is currently running setuid or setgid."
date: 2008-02-21
forum: Desktop Environments
---

### Post by walkeraj on 2008-02-21
I am a new user in a business environment using LDAP authentication.  At some point yesterday, my LDAP account stopped working on the local machine.  When I attempt to login, I am told my session terminated after less than 10 seconds.  The reason given is that a gtk process is attempting to run setuid or setgid.

In this environment, my home directory is stored on an NFS server automounted to /nfs/nfsdrive/awalker (my username).  All of the files in this directory are owned by this username.  No one around here has seen this problem before or is able to help me with it.  I was able to get it working yesterday, but only by deleting the entire contents of my home directory.

I have tried deleting all of the .gnome* files and .ICEauthority.  None of these or other "solutions" given in similar forums has worked.  Any ideas?

Contents of .xsession-errors:

```

(process:24021): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:24025): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/nfs/nfsdrive/awalker/.profile: 15: shopt: not found
/etc/bash_completion: 44: Syntax error: Bad substitution

```

---

### Post by Suparious on 2008-03-19
unless files were deleted as the root user, or that the server crashed, you should be able to delete and recreate your account.

I assume other users are still logging fine?

 It looks like you may have trashed your .bashrc and/or .bash_profile here.

---

