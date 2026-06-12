---
title: "Password prompt"
date: 2008-12-29
forum: General Help
---

### Post by grkuntzmd on 2008-12-29
I changed my password using the "change password" button on the dialog that pops up when I right-click my name in the upper gnome panel and select "edit personal information". This was the first time I changed my password since installing 8.10.

Now I get prompted for my old password every time I reboot (after a normal login) with a dialog that says that the NetworkManager Applet cannot access the default keyring.

I tried adding "@include common-pamkeyring" to my /etc/pam.d/gdm file and had to use a rescue LiveCD to fix my system after -- I could not log in again at all.

It appears that some keyring is using the old password for encryption. How do change that password?

Thanks.

---

### Post by cariboo on 2008-12-29
Try running seahorse to see if you can change your password. Press Alt-F2 and type:

```
seahorse
```

Jim

---

