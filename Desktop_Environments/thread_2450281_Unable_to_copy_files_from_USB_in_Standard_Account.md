---
title: "Unable to copy files from USB in Standard Account"
date: 2020-09-10
forum: Desktop Environments
---

### Post by greg2lapa on 2020-09-10
I have my primary (admin) account. I created a Standard Account and when I try to copy a file off a USB flash drive it says pasting is not allowed cause of permissions.I added the standard account user to the group of the admin account but this didn't fix anything. Anybody know how to make it so I can copy files onto the Standard Account?

---

### Post by CelticWarrior on 2020-09-10
If the problem is "pasting" then the issue is with the destination folder's permissions.

---

### Post by greg2lapa on 2020-09-10
I checked the folder and it is full read/write for everyone. I went and granted full read/write to the entire home folder of the "standard" user. Same problem when trying to access files on the flash drive. I also set the "standard" user to be in the group of the admin (sudo user)

---

### Post by CelticWarrior on 2020-09-10
You're messing with things you don't understand. Sooner than later you'll have an unbootable system.

---

### Post by greg2lapa on 2020-09-10
> **CelticWarrior said:**
> You're messing with things you don't understand. Sooner than later you'll have an unbootable system.Anyone else have any ideas why this flash drive is not readable from the Standard account?

---

### Post by CelticWarrior on 2020-09-10
Again, a misunderstanding. The drive IS readable but **the destination folder isn't writable** (for the user trying to do it) so you may need to use commands preceded by 'sudo' but not - NEVER - change the home folder permissions as you did.

---

### Post by SeijiSensei on 2020-09-10
Try writing the file to /tmp where everyone can write. Otherwise as an ordinary user you can only write to your home directory.

---

### Post by greg2lapa on 2020-09-10
If anyone knows a permanent fix for this, I'd appreciate it. In the meantime I'm stuck having to change the ownership of the Flash Drive (with sudo chown -R UBUNTU-USERNAME FLASHDRIVE) each time I want to add something to it on a different computer, which is a  major PITA.

---

### Post by CelticWarrior on 2020-09-10
What you're saying now is the opposite of the original post.
> [COLOR=#000000]when I try to copy a folder **of a** USB flash drive[/COLOR] where "of a" is the same as "from the/a". Unless you intended to say "to a/the"?

---

