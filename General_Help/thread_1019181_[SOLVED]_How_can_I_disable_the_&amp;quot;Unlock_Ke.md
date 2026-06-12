---
title: "[SOLVED] How can I disable the &amp;quot;Unlock Keyring&amp;quot; from popping up"
date: 2008-12-22
forum: General Help
---

### Post by charlescarroll1 on 2008-12-22
I've searched other forum posts, but couldn't find the answer to my question.  I am using a laptop to connect to my wireless network.  Whenever I load up Ubuntu I must enter my password into the "Unlock Keyring".  I read on another post to go to System > Preferences > Sessions and disable GNOME Keyring Daemon Wrapper, but I still receive the pop-up every time I log on.  This seems like a relatively simple thing to figure out, and I know I've done it once before.  Anyone know how I might be able to do this?

---

### Post by charlescarroll1 on 2008-12-23
Any ideas?  Has anyone else experienced this?

It only started popping up after I enabled automatic login.

---

### Post by masinger53 on 2008-12-23
I am configuring this old laptop for my mom for Christmas and I would definitely love to make this go away.  A login and password are going to be enough for her as it is.  =)

Edit:
After a bit more searching, I followed the info here [http://ubuntuforums.org/archive/index.php/t-320308.html](http://ubuntuforums.org/archive/index.php/t-320308.html) especially the last several posts.  Basically, set the default keyring password to blank (since I run Xfce4, I installed seahorse first to easily find it and not have to write scripts).  Not very secure, but not much risk of anyone getting to her machine, so I also enabled automatic login, so all good for the techno-challenged configuration.

---

### Post by charlescarroll1 on 2008-12-23
> **masinger53 said:**
> I am configuring this old laptop for my mom for Christmas and I would definitely love to make this go away.  A login and password are going to be enough for her as it is.  =)

Edit:
After a bit more searching, I followed the info here [http://ubuntuforums.org/archive/index.php/t-320308.html](http://ubuntuforums.org/archive/index.php/t-320308.html) especially the last several posts.  Basically, set the default keyring password to blank (since I run Xfce4, I installed seahorse first to easily find it and not have to write scripts).  Not very secure, but not much risk of anyone getting to her machine, so I also enabled automatic login, so all good for the techno-challenged configuration.

Thanks for the link man, but unfortunately I ran into another wall.

Heres what it says to do:
> 
To get rid of the keyring prompt after automatic login in hardy 8.04 you can:

System > Preferences > Encryption and Keyrings
Under Password Keyrings click on "login Automatically unlocked when user logs in."
Click "Change Unlock Password"
Enter your old password, but leave the new password fields blank.
Ok , confirm and you should be set.


When I go to the Encryption and Keyrings, I do not have a "Password Keyrings" or any option like that.  I have only two tabs "Encryption" and "PGP Passphrases".  Neither of these have any "login Automatically unlocked when user logs in" or "Change Unlock Password".  

I am using 8.10.  Would these options be different in 8.10 than in 8.04?

---

### Post by plucky on 2008-12-24
Try **Applications > Accessories > Passwords and ...> Edit > Preferences** and delete the login keyring and then add again and give it your **login** password.


Good Luck

---

### Post by charlescarroll1 on 2008-12-27
> **plucky said:**
> Try **Applications > Accessories > Passwords and ...> Edit > Preferences** and delete the login keyring and then add again and give it your **login** password.


Good Luck

This worked.  I restarted and had to restart again, but it worked.  Thanks.

---

