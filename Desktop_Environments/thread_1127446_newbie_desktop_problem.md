---
title: "newbie desktop problem"
date: 2009-04-16
forum: Desktop Environments
---

### Post by e_pupazzi on 2009-04-16
I've got a noob question :) The directory displayed on my desktop is not

/home/user/Desktop

but

/home/user


xdg-user-dir shows /home/user

where can i change the environment variable? Thank you in advance!

---

### Post by Daisuke_Aramaki on 2009-04-16
> **e_pupazzi said:**
> I've got a noob question :) The directory displayed on my desktop is not

/home/user/Desktop

but

/home/user


xdg-user-dir shows /home/user

where can i change the environment variable? Thank you in advance!

I don't really get that. The location of your Desktop is /home/user, which is indeed the way it should be. Desktop is a folder under /home/user.

---

### Post by RyanVanDiemen on 2009-04-16
what he meant is probably that the content of the directory /home/user/desktop is not showing on his desktop, but /home/user is. which is weird, never encountered that...  anybody, idea?

---

### Post by RyanVanDiemen on 2009-04-16
found it: go to your .config directory and edit user-dirs.dirs file and change line XDG_DESKTOP_DIR="$HOME/" to the directory you want to be shown as your desktop. in your case 
XDG_DESKTOP_DIR="$HOME/Desktop" or any other if you wish so.

hope this answers your question

---

### Post by e_pupazzi on 2009-04-16
Solved, thank you Ryan!

sorry for the double post, there was some db issue today with the forum...

---

### Post by _Purple_ on 2009-04-16
> **e_pupazzi said:**
> I've got a noob question :) The directory displayed on my desktop is not

/home/user/Desktop

but

/home/user


xdg-user-dir shows /home/user

where can i change the environment variable? Thank you in advance!

 The command given below will give you the desktop directory:
```
xdg-user-dir DESKTOP
```

The default settings are stored in /etc/xdg/user-dirs.defaults where as the settings for any particular users are stored in /home/user/.config/user-dirs.dirs as RyanVanDiemen has mentioned. You can change the settings for all the users or for any specific user.

---

