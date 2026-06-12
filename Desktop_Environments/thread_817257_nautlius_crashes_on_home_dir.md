---
title: "nautlius crashes on home dir"
date: 2008-06-03
forum: Desktop Environments
---

### Post by nbo10 on 2008-06-03
Hi All,
I was connected to  a server and coping a file over when I lost my internet connection. And now when I open file browser to my home dir in crashes. I can go to other dir just fine. how do I fix this. thanks

---

### Post by pytheas22 on 2008-06-03
Try this command:
```

mv ~/.nautilus ~/.nautilus-broken
```

Then log out and back in, and let us know whether the problem has been fixed.

---

### Post by nbo10 on 2008-06-03
Nope, After I open my home dir it grays out and if I force a quit it just restarts nautlius each time and I have to restart my computer.

---

### Post by pytheas22 on 2008-06-03
Alright, sorry that didn't work.  The next thing to try: create a new user by using the utility at System>Administration>Users and Groups.  Log out of your account and log in as the new user.  Can you access the new user's home directory in Nautilus?  This will tell us whether the problem lies with Nautilus itself or with some user-specific setting.

---

### Post by nbo10 on 2008-06-03
I can create a new user and open nautlius just fine.

---

### Post by arsenic23 on 2008-06-03
I get this problem sometimes when zips,rars,cbzs, and other media that thumbsnails are in the same directory is some X factor I haven't determined.

Do you have any archives or media files in the root of your home directory? You might try moving them to another folder with the terrminal.  

Also you could start nautilus from a terminal and see what errors it spits out, just run:
```
nautilus ~/
```

---

### Post by nbo10 on 2008-06-03
Nope, no  archives or media files. I started nautilus in a terminal and it started but still froze up with out any error on the command line.

---

### Post by dur on 2008-06-03
Try logging in as root and removing the file you were trying to copy from your home directory. Login as your second user and execute these commands:

```
sudo -s
rm -rf (filename here with no parenthesis)
```

---

### Post by nbo10 on 2008-06-03
Thanks. I just started deleting files in my home dir and now it works. Thanks

---

