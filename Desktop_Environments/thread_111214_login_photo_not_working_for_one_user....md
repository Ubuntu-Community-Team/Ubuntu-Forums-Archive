---
title: "login photo not working for one user..."
date: 2006-01-01
forum: Desktop Environments
---

### Post by joe_d on 2006-01-01
I have two users on a 5.10 system, and if i go to "Preferences -> Login Photo" for both users and change them, on the login panel (using Themed greeter of "Happy Gnome with Browser"), only the first user has their chosen photo.  The 2nd user just has the default picture.   

Any ideas how to fix this, or where this gets stored?    If i reboot and login as the 2nd user and select "Preferences->Login Photo" it is on the one i selected (but doesn't show up in the browser at login).

Thanks.

---

### Post by mrhelpman on 2007-04-22
I have seen this happen when the permissions on the home directory for a user are set to only allow the user to read the file. Try:
$sudo chmod a+r /home/username

Where username is the name of your user.

John T.

---

