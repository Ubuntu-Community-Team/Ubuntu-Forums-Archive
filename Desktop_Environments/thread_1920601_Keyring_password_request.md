---
title: "Keyring password request"
date: 2012-02-05
forum: Desktop Environments
---

### Post by motorcity909 on 2012-02-05
Hi all

I've set Xubuntu to log me in automatically but it still prompts for an unlock keyring password once the desktop comes up and I can't do anything until I enter my password - couldn't even take a screenshot so took the attached (imag0132.jpg) on my phone.

I've installed Seahorse and remembered that I had this issue once on Ubuntu and simply changed the passwords in Seahorse to blank.  There were three keys in Seahorse (see attached screenshot) so I changed them to blank and rebooted....and it still prompted for the password.

I also realised this had logged me out of Ubuntu One sync so I deleted the U-One keyring, logged in to U-One again which regenerated that keyring (now no.4) and new password, so that's fine.  The other two keyrings both still have a blank password.

I know there are security aspects to these keyrings but I'd really like to not have to enter it everytime I logon.  This is a family PC in my home so I trust all the users (obviously).

Any help as always is much appreciated.
Dave

---

### Post by mcduck on 2012-02-05
You have to change the *keyring's* password to blank, not the passwords stored in the keyring...

(so make sure you right-click on the "Passwords:default" and then select the "Change Password"-option. You don't need to do anything with the actual keys.)

---

### Post by ajgreeny on 2012-02-05
This could also be the wireless network connection asking for password, so check that the wireless network is set to **Automatically connect** and is also **Available to all users** in the Edit Connections dialog box.

---

### Post by mcduck on 2012-02-05
> **ajgreeny said:**
> This could also be the wireless network connection asking for password, so check that the wireless network is set to **Automatically connect** and is also **Available to all users** in the Edit Connections dialog box.
Setting the keyring password to empty would give the same result, and also works for any other program that's using the keyring... ;)

---

### Post by motorcity909 on 2012-02-05
Thanks for the replies, clearing that password has worked perfectly, complete with a reboot to check.

Appreciated as always
Dave

---

