---
title: "Would it be possible to install applicatons???"
date: 2006-06-13
forum: Desktop Environments
---

### Post by true_friend on 2006-06-13
Hi 
would it be possible to install other applications on 6.06  which are not offcially supported by ubuntu and kubuntu. like yahoo messenger, real player 10 etc. As they can be installaed easily on redhat and other distros.
wiating for answer.

---

### Post by KenSentMe on 2006-06-13
When you have a .deb of the application, you can run 

sudo dpkg -i package.deb

For more information about installing software, check

[https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)

If you want to install realplayer, check

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by linbetwin on 2006-06-13
Yahoo! Messenger for Linux is outdated. You can use Gaim to connect to the Yahoo! network (and numerous other networks). But if you really want Y!M, I've made a HOWTO here (it's for Breezy, but it should work in Dapper too):
[http://ubuntuforums.org/showthread.php?t=81895&highlight=howto+yahoo%21+messenger](http://ubuntuforums.org/showthread.php?t=81895&highlight=howto+yahoo%21+messenger)
As for RealPlayer 10, do this in a terminal:
```
wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb
```
and then
```
sudo dpkg -i realplayer_10.0.7-0.0_i386.deb
```

---

