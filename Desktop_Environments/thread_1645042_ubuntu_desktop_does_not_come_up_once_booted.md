---
title: "ubuntu desktop does not come up once booted"
date: 2010-12-14
forum: Desktop Environments
---

### Post by mahsa2010 on 2010-12-14
Hello
I have ubuntu 8.10 on Dell laptop. I wanted to install samba on it. It asked me about installing a lib. I said yes. and then it wanted to "remove" some packages. I agreed by mistake!!!!!! and stopped it in the middle of removing. Now when ubuntu boots up, it boots normally: no graphic desktop!!. By crtl+alt+f2 and F7 it switches between graphic and normal. But the desktop does not have anything. Once it boots, it says:kinit: resume from old one /var/.../uuid/....
Would you please help me how to know what exactly is deleted? And how to repair it?
I tried "sudo apt-get -f install" but it errors that dependencies aren't met!!!

---

### Post by Krytarik on 2010-12-15
Look in /var/log/apt/history.log to see what packages have been removed. It seems like it's at least "ubuntu-desktop".

You may also try:
```
sudo apt-get --fix-broken install
```

Here is another ongoing thread with a similar problem:
[http://ubuntuforums.org/showthread.php?t=1644912](http://ubuntuforums.org/showthread.php?t=1644912)

---

