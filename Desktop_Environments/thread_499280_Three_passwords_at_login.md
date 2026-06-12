---
title: "Three passwords at login"
date: 2007-07-12
forum: Desktop Environments
---

### Post by azelter on 2007-07-12
When I log into my system I need to enter three passwords before I can work. The first is the standard unix login (in to the gdm or kdm box after X has started). The second is the passphrase for my ssh key (I run ssh-add at start up so I don't need to keep entering pasphrases for ssh conections after I'm logged in). The third password I need to enter is for gnome-keyring as my wireless network requires a key, and by default in Ubuntu this is managed by gnome keyring manager, which wants another password.

I understand that these passwords all have different functions and all relate to different parts of my system, however, that does not change the fact that it's rather excessive to have to enter 3 passwords before being able to work after I turn on my computer.

I think that if I am at the computer and have logged in, then I should be regarded as a legitimate user and thus not have to enter passwords for every other thing I want to do - after I've already logged in. For a simple home system, which is what I and many other 'casual' users have, this should be enough security.

So, does anyone have advice as to how I can remove the password for gnome-keyring-manager? Are there scripts out-there that could be run at login that would remove the need to enter multiple passwords at login? Or do people think this situation is desirable? I'm interested - as I don't think it even really adds to security much to have my wireless key encrypted with yet another password. After all, for anyone that has gained physical access to my computer (or even hacked in via ssh) - my network key is not going to be the prized piece of information on my computer - let's face it - you need to be within 50 yards of my modem to use it! :)

---

### Post by fjgaude on 2007-07-12
Well, you might try what the System/Administration/Login Window menu has to offer. Try the Security tab and Enable Automatic Login and see what happens.

Let us know how you make out. <smile>

frank

---

### Post by azelter on 2007-07-12
Thanks for the suggestion but this will only get round the first password.
I want the first password. My point is that AFTER I've authenticated myself, I should not have to enter several more passwords. Not that I don't want to have to enter any passwords.

---

### Post by fjgaude on 2007-07-12
Racking my brain... can't think of anything else. Maybe others have ideas?

Really, all you wish to do is get rid of one password entry, right? I guess the Ring Manager is the place to start. Have you tried Always Allow? and then you do the passwd only once from then on out? Notice that you can add Applications to the key list? I think you can get to where you wish to be, one of these days. <smile>

I know I access remote boxes that have my passwd in the ring and I'm not asked for my passwd. Now ssh maybe different. I think I into passphrase whenever I have had to reboot. But the OS holds the phrase until then.
 
frank

---

### Post by sisco311 on 2007-07-12
> how I can remove the password for gnome-keyring-manager?```
sudo visudo
```copy this at the and of the file:
>  **your_user_name** ALL=NOPASSWD: /usr/bin/gnome-keyring-managersave and exit(Ctrl+o, Ctrl+x)
this allow you to sudo the gnome-keyring-manager command without entering a password

---

### Post by azelter on 2007-07-12
Thank you. I will try that. As for ssh-add, assuming I use the same password for ssh and to login, I guess I need to find a script that will send my login password keystrokes to ssh-add.

---

### Post by Bazirker on 2007-07-15
I tried this but it didn't seem to work...anyone else get it to work?

---

