---
title: "Profile is Corrupt"
date: 2010-01-16
forum: Desktop Environments
---

### Post by 9a8sy on 2010-01-16
A few days ago the network I was on when down and my laptop locked up. I ended up powering down my PC. When I rebooted and signed into my profile, it would only come up with the background wallpaper, no icons or menu. I can log into a different profile just fine. I did a forced disk check but that didn't solve my problem. Is there anyway to repair my profile? If not, can I take ownership of my folders under my corrupt profile?

---

### Post by 9a8sy on 2010-01-19
So nobody here can help? Does anyone know of another "Good" forum on Linux where I might be able to find someone who could help in this situation?

---

### Post by nothingspecial on 2010-01-19
This is very simple to fix - do not worry.

You need to boot into recovery mode - a root shell.

Then ```
adduser bob
```

```
adduser bob admin
```

```
cp -rv /home/oldusername /home/bob/
``` to copy all the files in your corrupt home directory to bob`s home directory. Or```


mv /home/oldusername /home/bob
``` to move them, which will be alot quicker but make it more difficult to fix your corrupt account

```
chown -R bob:bob /home/bob/oldusername
```

```
exit
```


Log in as bob and all your files will be in bob`s home directory in a folder called your old username.

Obviously change bob for whatever you like.

---

### Post by 9a8sy on 2010-01-19
Just what I needed. Thanks!!

---

