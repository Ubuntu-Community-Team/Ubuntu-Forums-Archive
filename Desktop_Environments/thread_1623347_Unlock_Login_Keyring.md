---
title: "Unlock Login Keyring"
date: 2010-11-16
forum: Desktop Environments
---

### Post by nshiell on 2010-11-16
I have an Ubuntu desktop
I have set it up to connect to my MSN Messenger account
Each time I boot up I get a dialogue box saying
"The login keyring did not get unlocked when you logged into your computer"
with a space to type in my password

This should NOT be asking for my password after I am into my account!

I think this is a usability bug? How can I fix this?

---

### Post by mcduck on 2010-11-16
Actually yes, it should be asking for the keyring password, since you have one and probably are using automatic login so you aren't doing anything else to confirm that you are you and not some random person trying to access your keyring.. Encrypting stuff without any kind of password or other confirmation to unlock it would be pointless...

(The keyring will get automatically unlocked if the keyring password is the same as your login password, and you actually type in your password in the login screen.)

If you don't want to have to unlock the keyring, either use normal login (and make sure your keyring password is same as your login password) or set the keyring password to empty one (which will make the keyring to store the keys unencrypted, which is less secure but probably not a problem since you are already using automatic login).

If you wish to remove the keyring password, just go to System/Preferences/Passwords and Encryption Keys, right-click the "Passwords:login"-keyring and select "Change Password". type in your current password and leave the fields for new one empty.

(If you aren't using Ubuntu 10.10 but some older version instead, the right place is Applications/Accessories/Passwords and Encryption Keys.)

---

### Post by pylover on 2010-11-16
i have ubuntu maverick,

when i login, it asks unlock keyring more than one, some times 2 or 3 dialogs appears .

---

### Post by mcduck on 2010-11-17
What is the "it" in this case?

If you have many programs that use the keyring, and they all start at the same time, they could indeed all ask for the password at the same time. Only if it's the *same* program asking to unlock the keyring multiple times that would be a sign of some problem.

Still, the solution is same as above, either use normal login so the keyring will already be unlocked when those programs start, or set the keyring password to empty one.

---

### Post by Tigerlinux on 2011-01-23
mee too having this problem in ubuntu ultimate, so i just set a new password for it

---

### Post by 130s on 2011-08-11
[mcduck]("http://ubuntuforums.org/member.php?u=17309")'s plan works fine for me. Thanks!

---

