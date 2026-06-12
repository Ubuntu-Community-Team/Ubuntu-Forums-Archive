---
title: "[SOLVED] Whats my username and password?"
date: 2008-12-17
forum: General Help
---

### Post by asheq on 2008-12-17
I just installed everything, was on the login screen, and it asked me for my username and password....
What could it possibly be?

---

### Post by iaculallad on 2008-12-17
> **asheq said:**
> I just installed everything, was on the login screen, and it asked me for my username and password....
What could it possibly be?

Use the username and password you had inputted on Ubuntu's installation wizard.

---

### Post by jerome1232 on 2008-12-17
If you can't remember what you put in during installation then you'll have to boot into recovery mode and find your username then reset your password there.

While the computer is booting up hit the 'esc' key you should be given the grub menu, select the highest option that has the word recovery in it.

Eventually you should get a blue screen that has as few options, select drop to a root shell.

once at a root shell type this command to figure out your username
```
ls /home
```

It'll list out your user's home directory which is the same as your username.

now change your password.
```
passwd *usernamehere*
reboot
```

now you should be able to boot up and login with that username and the new password you have choosen

---

### Post by asheq on 2008-12-17
Thanks, I was there but when i try to type my new password, it won't let me type...
It asks for a new one, and my keyboard just won't work.
What now?
It'll let me press the enter key 
But not type.

---

### Post by kanikilu on 2008-12-17
I believe when you change your password there, no output will show on the screen. Just type the password, press enter, confirm it by re-entering it, and then press enter again when done.

---

### Post by jerome1232 on 2008-12-17
Just type you password in, your keyboard is working it just doesn't echo apostrophe's back for security reasons (someone looking over your shoulder can't see how many characters the password is)

---

### Post by asheq on 2008-12-18
Ohh. See, I thought of that. But didn't want to sound like an idiot if I had replied with that.  Thanks!

---

