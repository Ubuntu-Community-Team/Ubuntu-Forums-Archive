---
title: "XFCE4 shutdown/reboot action in panel not working"
date: 2006-07-10
forum: Desktop Environments
---

### Post by nickless on 2006-07-10
I installed xfce4 on an ubuntu server 6.06 and then the xubuntu-default-settings, but the button on my xfce4-panel will only shutdown X and not the whole system. This is a problem that can be solved with editing sudoers. No big deal, but on my search for the right commands to give rights I find this on xfce.org :
> 15. How do I enable the shutdown/reboot action in the session-manager logout dialog?

You have to allow the user(s) to execute $installdir/libexec/xfsm-shutdown-helper with sudo. Please install sudo, and refer to xfce4-session and sudo documentation.
Now in ubuntu there is no /libexec anywhere and I have not located xfsm-shutdown-helper or anything similiar either ( I found the icons thought...)
What now? Just give users right for /sbin/halt ?

---

### Post by nickless on 2006-07-10
I tried some sudoer entries, but nothing worked :(
```

# Cmnd alias specification
Cmnd_Alias SYSTEM = /sbin/modprobe /sbin/shutdown, /sbin/halt, /sbin/reboot, /sbin/poweroff, /sbin/ifdown, /sbin/ifup
# User privilege specification
root    ALL=(ALL) ALL
jan ALL = (root) NOPASSWD: ALL

```

---

### Post by Nopposan on 2007-01-04
I'm having a similar problem, however, a solution is in the quote from the wiki that you cited.
It just wasn't obvious to me either, but you need to actually run the command like this:

$sudo install -d /libexec/xfsm-shutdown-helper

That should help, but if your user isn't in the sudoers file then you won't be able to keep using the shutdown button on the toolbar time after time; at least, I wasn't able to do that.  'Haven't checked yet, but I'm guessing that the directory you created is erased and then recreated by sudo at reboot.  'Trouble is, I don't know if I want every user to be in the sudoers file -- 'trying to enforce internet filtering.  'Got to research sudo like the wiki advised me to.

---

