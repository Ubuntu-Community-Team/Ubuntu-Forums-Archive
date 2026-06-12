---
title: "Login Problem in Ubuntu 16.04"
date: 2017-03-10
forum: Desktop Environments
---

### Post by AnupamMitra on 2017-03-10
Since yesterday night can't enter in my desktop o/s ubuntu 16.04 thogh I entered correct password. However, I can enter into Terminal by Alt+Ctrl+F2 wherein if I enter my password, it allow me to write/post.

---

### Post by Perfect Storm on 2017-03-11
Do you have nvidia card in your computer?

---

### Post by AnupamMitra on 2017-03-11
No, what I found is as under.
 VGA compatible controller : Intel Corporation Device 1902 (rev 06).

---

### Post by Perfect Storm on 2017-03-11
Try reset the password, you can see how here: [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by AnupamMitra on 2017-03-11
@Artificial Intelligence - I humbly suggest that it is not a problem of password. When I enter the password to log in, it shows that "failed to start session". Moreover, when intentionally I input wrong password, it shows "invalid password,...........". Kindly think again and give your valuable advice.

---

### Post by Perfect Storm on 2017-03-11
okay.

Try with:
```
sudo apt install --reinstall ubuntu-desktop
sudo apt install --reinstall ubuntu-session

```

---

### Post by DuckHook on 2017-03-11
@OP

Please describe your actions just prior to the problems. Did you do a no-no like:```
sudo gedit
```…or:```
sudo nautilus
```If so, you may have corrupted your /home directory or .Xauthority.

---

### Post by AnupamMitra on 2017-03-12
@Artificial Intelligence - Many many thanks Dear. This time I could enter to my system with your advice. I got back everything. Hats off. Regards.

---

