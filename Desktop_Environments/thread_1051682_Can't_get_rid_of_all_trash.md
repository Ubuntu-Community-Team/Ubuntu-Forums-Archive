---
title: "Can't get rid of all trash"
date: 2009-01-27
forum: Desktop Environments
---

### Post by Matt_Rapp on 2009-01-27
So I have this pesky folder from creating an live cd that is sitting in my trash bin and will not be emptied with other files. I've tried deleting it through the terminal, even root terminal but it can't find the trash directory. The folder doesn't have any special permissions or anything in its properties, why will it not go away? I have version 8.10.

This is its address through nautilus,I can open it and there is nothing in it.

[B]
"trash:///_gparted-live-0.4.1-2"[/B]

It's really only an annoyance, the trash icon is always full.

---

### Post by adamlau on 2009-01-27
Happens to me from time to time. What should work does not always work for this problem :) .

Try this first (may, or may not work):

```
sudo rm -rf ~/.local/share/Trash
```

Try this second (where user is your login name):

```
sudo -i
```
```
rm -rf /home/user/.local/share/Trash
```

Try this third (this resolution usually works):

```
gksu nautilus
```

And delete '/home/user/.local/share/Trash'. You may need to:

```
Ctrl+Alt+Backspace
```

Or reboot in between attempts. And you may need to:

```
sudo chown -hR root:admin ~/.local/share/Trash
```

Or user:admin, or user:user, your choice depending on what you want to do. It is a confounding issue that does not always resolve itself as you would expect :( .

---

### Post by Matt_Rapp on 2009-01-28
The second one worked, thanks!

---

### Post by goramit on 2009-01-29
#1 worked for me.  Thank you!

---

### Post by donkyhotay on 2009-01-29
This generally happens when you attempt to delete a file with root permissions (such as after a sudo make install). It happens to me often enough I just created a script for it  and set it into my main menu with gksudo so that it's easier. I kind of wish gnome would have an option to 'empty trash as admin' or something along with the regular empty trash to make this easier but oh well.

---

### Post by wolfe on 2009-01-30
Thanks for this, I've had 2 small items sitting in my trash for months but just never had the ambition to learn how to remove them.

---

### Post by Edaw 0 on 2009-02-01
Thanks!

---

