---
title: "Can't Login"
date: 2006-10-02
forum: Desktop Environments
---

### Post by The Pinny Parlour on 2006-10-02
I have just rebooted and now I can't login with my correct details.  Any ideas on how to reset the user/password/

thanks

---

### Post by aysiu on 2006-10-02
Boot into recovery mode.

Then type ```
passwd *username*
reboot
``` where *username* is your actual username

---

### Post by The Pinny Parlour on 2006-10-02
cheers  :)

---

### Post by The Pinny Parlour on 2006-10-02
Just gets to the login point and freezes.  Reboot in normal mode and enter my login and password, nvidia splash screen comes then back to login screen   argh.  

Any more ideas?

Thanks

---

### Post by The Pinny Parlour on 2006-10-02
ok after fruitless attemps I get this:

GDM could not write to your authorisation file. This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system adminisrator.

Any ideas?

The HDD is close to full. BTW

---

### Post by aysiu on 2006-10-02
Maybe deleting some files then?

In recovery mode, these commands may help: ```
rm -rf /home/*username*/.Trash/*
aptitude clean
``` Are there any other files you can delete in your /home directory?

By the way, be *very* careful with that first command. If you hit Enter too soon, you'll delete either your entire home directory or the entire Ubuntu system.

Do you have a live CD? Deleting graphically may be the safest option. The terminal is too powerful and can be dangerous for deleting things.

---

### Post by The Pinny Parlour on 2006-10-02
> **aysiu said:**
> Maybe deleting some files then?

In recovery mode, these commands may help: ```
rm -rf /home/*username*/.Trash/*
aptitude clean
``` Are there any other files you can delete in your /home directory?

By the way, be *very* careful with that first command. If you hit Enter too soon, you'll delete either your entire home directory or the entire Ubuntu system.

Do you have a live CD? Deleting graphically may be the safest option. The terminal is too powerful and can be dangerous for deleting things.



Live CD;  good point will try that.  cheers

---

