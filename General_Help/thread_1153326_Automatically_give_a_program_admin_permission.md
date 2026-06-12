---
title: "Automatically give a program admin permission?"
date: 2009-05-08
forum: General Help
---

### Post by Surfrock66 on 2009-05-08
I use gnome-do with the microblogging plugin.  Every time my computer starts, the permission window pops up until I enter my password.  While I know it's unwise, is there a way to automatically give a program admin permission when it starts?

---

### Post by kevstar31 on 2009-05-08
sudo chmod a+s **path to program**

---

### Post by Surfrock66 on 2009-05-08
total n00b, but is there a way to trace the path to the program?  I checked in /usr/share/gnome-do, is it /usr/bin/gnome-do?

EDIT: ok, so I tried /usr/bin/gnome-do and it didn't work.  The popup, however, said "/usr/bin/mono" was the problem and I ran the command on that, and now gnome-do won't load on startup, and I can't open the program from the applications menu.  Thoughts?  An undo command for the original command?

---

### Post by Surfrock66 on 2009-05-09
Bump?

---

### Post by Alterax on 2009-05-09
Tried **sudo chmod a-s** on those programs to remove the sticky bit?

---

### Post by hobo14 on 2009-05-09
If you can see the program in System -> Preferences -> Startup Apps  you can edit it's command from

"sudo ProgName"

to

"sudo -u YourUserName ProgName"

it will start with root privileges without asking for a password.

---

### Post by mcduck on 2009-05-09
> **Surfrock66 said:**
> I use gnome-do with the microblogging plugin.  Every time my computer starts, the permission window pops up until I enter my password.  While I know it's unwise, is there a way to automatically give a program admin permission when it starts?

are you sure it's asking for admin permissions, and not just asking you to unlock the keyring?

Any plugin like that requiring admin permissions would make me consider couple of times before using it, as it shouldn't need that kind of permissions for anything.

Unlocking the keyring, on the other hand, makes much sense as it probably needs o connect to the net and if you use automatic login you need to remove your keyring password or type every time you log in.

---

### Post by hobo14 on 2009-05-09
> **mcduck said:**
> are you sure it's asking for admin permissions, and not just asking you to unlock the keyring?

Any plugin like that requiring admin permissions would make me consider couple of times before using it, as it shouldn't need that kind of permissions for anything.

Unlocking the keyring, on the other hand, makes much sense as it probably needs o connect to the net and if you use automatic login you need to remove your keyring password or type every time you log in.

Oh yeah, I hate that.
You can stop keyring from being started in System->Preferences->Startup Applications, 
or do this:
delete the files in ~/.gnome2/keyring/
re boot, nxt time the relevant app asks for it's password (eg wirless asking for WEP/WPA) give it, but when keyring asks for a new password, dont enter anything, just hit Create. You will get a sercurity warning, just hit OK (or whatever it says) and, viola!: no more pesky keyring questions, even with autologin.

Theres another solution around that uses pamkeyring, but that can cause your login screen to go nut: it just thinks you are continuously entering wrong login data.  Happened to me.

---

### Post by Surfrock66 on 2009-05-09
> **mcduck said:**
> are you sure it's asking for admin permissions, and not just asking you to unlock the keyring?

Any plugin like that requiring admin permissions would make me consider couple of times before using it, as it shouldn't need that kind of permissions for anything.

Unlocking the keyring, on the other hand, makes much sense as it probably needs o connect to the net and if you use automatic login you need to remove your keyring password or type every time you log in.

You're right it's asking for access to the keyring.  I'll try the suggestion in the post below, thanks!

---

### Post by mcduck on 2009-05-10
> **hobo14 said:**
> Oh yeah, I hate that.
You can stop keyring from being started in System->Preferences->Startup Applications, 
or do this:
delete the files in ~/.gnome2/keyring/
re boot, nxt time the relevant app asks for it's password (eg wirless asking for WEP/WPA) give it, but when keyring asks for a new password, dont enter anything, just hit Create. You will get a sercurity warning, just hit OK (or whatever it says) and, viola!: no more pesky keyring questions, even with autologin.

Theres another solution around that uses pamkeyring, but that can cause your login screen to go nut: it just thinks you are continuously entering wrong login data.  Happened to me.
Actually the best way to get rid of the keyring password is very simple, just use the keyring manager found in the Applications-menu.. ;) This way you won't loose any keys in the keyring (which would happen if you removed the setting files) or any functionality.

1. Go to Applications/Accessories/Passwords and Encryption Keys and open the Passwords-tab.

2. Right-click on the "Passwords:login"-folder and select "Change Password"

3. Enter your old password, and either new password twice to change the password, or leave the fields for new password empty to remove the password.

(This is how it's done on 9.04, if you are using older version the Keyring Manager is a bit different. Just ask if you need instructions for that instead..)

---

