---
title: "Tried everything cant login to admin account!"
date: 2012-12-03
forum: Desktop Environments
---

### Post by Mundafar on 2012-12-03
I have Ubuntu 12.04 LTS installed and have read many articles on finding a way to change the admin password as i forgot it after installing it a while ago. I have 2 users on this comp which i know the pass to 1 but the admin 1st user i can no longer get into. I have tried many ways like going through grub, root and trying to unmount. i have had it tell me several times that the password has been updated successfully and i still cant login. If i am in my other user and i try to install things and use the password that i changed it to it works but actually logging into the main user account wont work after hours of racking my brain and following threads of things that are supposed to help. I just want to get my work back and films that are in that account. Someone please tell me something new that works...lol...it would be so much appreciated! Thx

---

### Post by cmcanulty on 2012-12-03
I believe this will do it
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by Mundafar on 2012-12-03
i went through all the steps and they went as prompted, was told successful change of password but still cant login...

---

### Post by steeldriver on 2012-12-03
What exactly happens when you try to log in? what error message (if any) do you get?

Can you log in at one of the non-GUI virtual terminals (Ctrl-Alt-F1 etc.)? if so it is really a session startup problem not a login problem

---

### Post by Mundafar on 2012-12-03
It doesnt tell me invalid password like if i put in anything different, but when i try to login the screen goes black it makes a noise and brings be back to the my various users login page.

---

### Post by Mundafar on 2012-12-03
> **steeldriver said:**
> What exactly happens when you try to log in? what error message (if any) do you get?

Can you log in at one of the non-GUI virtual terminals (Ctrl-Alt-F1 etc.)? if so it is really a session startup problem not a login problem

it finally brings me to mundafar@mundafar:$ which i never got i always got root@mundafar
but now it asks current unix pass which i dont know right...lol

---

### Post by Cheesehead on 2012-12-03
What you seem to be describing is:
1) When you enter a password you know is wrong, the system tells you.
2) When you put in a password you know is right, X crashes, which returns you to the login prompt.
Is that right?

Try this, too:
At the login screen, press CTRL + ALT + F1 to switch to a text-only interface. Try logging in. When finished, use the 'logout' command, then CTRL+ALT+F7 to return to the graphical interface.
If you can successfully login as an admin using text, diagnosing and repairing your system (or recovering data before a reinstall) will be much easier.

---

### Post by black veils on 2012-12-05
you should backup your data first. you should always have a backup. boot a live disc of ubuntu, choose the try mode. open terminal and copy-paste ```
gksudo nautilus
``` or change it if you use another file manager. navigate to the drive and folder which stores you data, copy-paste it to another usb stick or external hard drive. dont worry if it says about symlinks, just accept that.

---

