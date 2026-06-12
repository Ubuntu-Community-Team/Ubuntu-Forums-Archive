---
title: "Auto Login Option - Don't you Think It Should be Fixed or Removed"
date: 2010-11-05
forum: Desktop Environments
---

### Post by gwm on 2010-11-05
About 6 months ago, I tried auto login. To my way of thinking, it didn't work properly (I come from an automated control environment, where computers need to be able to start up and run unattended). Since then, I've found other threads relating to this issue. Mine was
**[http://ubuntuforums.org/showthread.php?t=1485375](http://ubuntuforums.org/showthread.php?t=1485375)**
One suggestion I got was to google for solutions. I tried that and found that many others would like auto login but also find it problematic (sometimes they get quite intense about it). I also found that this problem has been around for at least 4 years now.
I was also given specific links to specific solutions but these apply to previous releases where menus and things were in different places.
So I thought to try auto login again with *Maverick*. It is still buggy! If this was a system that needed to run unattended, Ubuntu would not be an option.
I am still asked for my key ring password.

:popcorn:

---

### Post by kerry_s on 2010-11-05
passwords & encryption keys
right click password:login
select change password
put the current password & leave the other 2 blank
it says some stuff about unsafe, click okay

you will no longer be asked for password.

---

### Post by gwm on 2010-11-05
Thanks kerry_s,
If I understand you correctly, you are suggesting that if I blank the default keyring password, the prompt will cease.

In other words, the problem comes from way back, during installation. There was a panel where one is asked for a keyring password. Since I wanted to use auto login, at that point, I should have refrained from entering a password.

Is that right?

---

### Post by kerry_s on 2010-11-05
yeap. this issues been around a while, it's a pam issue. it don't make since to me why this hasn't been dealt with & fixed.

---

### Post by gwm on 2010-11-08
Been there, done that!

Contrary to the above advice, the solutions I found by googling suggested ensuring that the keyring and the user have the same password. When I tried that, I found I was being asked for authentication not once, but twice.

The *Password Encryption Keys* app, displays two lists and my email-pop-server-password appeared under both of them. I don't know how I got that right. So, I deleted the entry from both and blanked the keyring password. The next *Send - Receive* in *Evolution Mail* asked for credentials as expected (since I had wiped the stored password) and now everything is roses. No more prompt for keyring passwords.

Thank you very much indeed.

---

