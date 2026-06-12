---
title: "Wireless Network Authentication Required"
date: 2009-04-05
forum: General Help
---

### Post by DavidOrr on 2009-04-05
Hello all, A newbie requesting some help. I have a Dell Studio laptop that runs Vista Home Premium. I only have this laptop because of the cost or I would have bought a Mac, I am really a Mac user since the early 90"s. Not to offend anyone but Windows really sucks to me. Yesterday I decided to install ubuntu-8.10-desktop-i386.iso and everything went great, I can now dual boot back to Vista without any problem at all. The only issue I have with booting up in ubuntu is with my wireless connection, to connect to my wireless I am always prompted to enter my password key which is 26 digits and then my user password and then all is fine. So how do I get around this?, because other than this issue I really love this OS. After learning ubuntu like I did with the Mac, Windows will be gone. Note that I know some networking but I am not any where near great at it.

Thanks in advance_David

---

### Post by Peter09 on 2009-04-05
There should be an option somewhere in the dialog to remember your password.

---

### Post by DavidOrr on 2009-04-05
I cannot find anywhere that gives me the option to remember password.

Now I am prompted to "enter password for default keyring to unlock" but I never made a password for this, what can I do to fix this?

---

### Post by Yashiro on 2009-04-05
Applications > Accessories > Passwords & Encryption Keys
Edit > Preferences

Click the login keyring. Do change unlock password.
Set it to the same password as your ubuntu login.
Make sure location for application passwords is also set to the login keyring.

Close that dialog now and you should be back in the main Pass and Encryption window again. Look in personal keys and passwords and remove any entries that seem to be related to your wireless login.

Now reboot. When you login in and are asked your wireless password make sure you check it to remember forever if that option exists.

I'm doing this from memory here as I recall having a similar issue last year on Debian.

---

### Post by DavidOrr on 2009-04-05
Thank you Yashiro, I deleted the default key and made a new one, now when I boot up I only have to enter my login password and I connect right away, but I still cannot find where to have the OS remember the passwords. I guess I have a lot to learn.

---

### Post by Vinnyd on 2010-02-03
Hi everyone, My problem is little different..... i get the same message after inputting network name and password.... i click connect and it just pops up again i don't get it. I'm running Ubuntu 8.10 for Ppc (PS3) i get no internet connection what so ever just the same message. I go to add and remove and it wont let me load any programs because it needs to up date and being that there no internet i can't. what do i need to do to connect wireless with my PS3 using Ubuntu 8.10? Please explain in detail im new with Linux.

Vinnyd

---

