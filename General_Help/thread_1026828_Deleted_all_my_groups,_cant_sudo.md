---
title: "Deleted all my groups, cant sudo"
date: 2008-12-31
forum: General Help
---

### Post by mpegjohn on 2008-12-31
Hi,
I was messing about trying to add myself to a new group, and accidentally deleted 90% of the groups I belonged to, including admin.
Now when I try sudo, I get an error:
 not in the sudoers file.  This incident will be reported.
So I can't do any admin tasks or put back any groups.

What do I do?
What are the default groups I should belong to?

I am using a network login, onto a server install with no X.

Please help as I am in a panic!

Regards,
John

---

### Post by jerome1232 on 2008-12-31
Do you have another user in the admin group?

If not do you have physical access to the machine? 

If you do have another user in the admin group and you know the password for the other user you can do this.
```
su otheruser
sudo useradd user group
### keep doing that for each group you want to give the user, the default  groups are
adm dialout cdrom plugdev lpadmin admin
```

If you can't do that but you have physical access to the server then time to hook up a monitor and keyboard, reboot the machine, mash esc to get the grub menu, boot into recovery mode, drop to a root shell. Then add your user to the groups from the root account.

---

### Post by donkyhotay on 2008-12-31
During the grub screen on startup press escape to get into the grub menu. From there select 'recovery mode' and it will boot you into a CLI as root. From there you should then be able to recreate your groups and add yourself back onto the sudoers list.

---

