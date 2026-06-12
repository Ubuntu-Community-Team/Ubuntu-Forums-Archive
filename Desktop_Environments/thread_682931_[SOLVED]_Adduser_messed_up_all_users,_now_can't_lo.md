---
title: "[SOLVED] Adduser messed up all users, now can't login"
date: 2008-01-30
forum: Desktop Environments
---

### Post by iris-n on 2008-01-30
I already posted this issue in Absolute Beginner Talk, but it seems that it isn't so basic. The thing is, this morning i was trying to add a new user for my baby brother, and i ran through the weirdest problems:

I added trough the tty cli. Apart from lack of recognition of latin characters, that went fine.

When i tried to login, nothing. Weird. Logged back into my account, and tried to delete his account from the gui, but none were shown there. Gone to groups, and deleted his. But, all groups were deleted to! Even root.

So, now i couldn't login at all, even in recovery mode. Then i pasted the shadow and passwd files from my other pc, through the live cd, and I recovered recovery mode. But when i try to login, even from new accounts, i get this error:> 
(process:5355): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5359): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Could not get password database information for UID of current process: User "???" unknown or no memory to allocate password entry

Failed to start message bus: Memory allocation failure in message bus
EOF in dbus-launch reading address from bus daemon

Already tried reconfiguring X (solved a keyboard problem inadvertently), reinstalling ubuntu-desktop, adduser, all in vain. 

And i can't get to the users-admin in my root gui, is there any way to reinstall it?

I've never seen such an epoch fail before... anybody has any ideas on what to do?

I think resetting the users would do, but i have no idead on how to do that.

Thanks in advance,

Iris

---

### Post by iris-n on 2008-01-31
Solved it. In case anyone rans into a similar problem and fins the thread, this is the solution:

Copied, from a working system, the files /etc/passwd, /etc/shadow/, /etc/group and /etc/gshadow. Edited them so as to remove any users apart from the system ones (ANY trace of them). Be sure they've got the right permissons (640 for shadow and gshadow, and 644 for passwd and group). Boot in recovery mode, add a new user, and add him to the admin group. Login in his account. Recreate old users. But they still don't have their files, so:

```
cd /home
sudo chown -R <username>:<username> <username>
```

Hope it's of any use.

---

