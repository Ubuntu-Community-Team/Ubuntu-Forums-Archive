---
title: "Brand new laptop: can't find/there is no default password but sudo requires one"
date: 2013-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mario11 on 2013-08-29
Hello.

I'm Mario and I am new to this forum. I'm a computer programmer and of course, I know how to handle command line and such (Not a beginner in other words).

I have been recently given a Dell Inspiron N4050 as a gift.The computer logs in automatically the default user but as almost any other user I need to do administrative tasks like installing and updating software and these tasks require me to enter my password. However, the computer is brand new and nobody from technical support at DELL was able to tellme what is the password for the default user (DELL). Furthermore, they have said that their database indicates my computer came with Windows, which is false. I know it could not have been manipulated at the shop because it came in a seales box and the inner bag was sealed. There where no fingerprints on the computer either.

I just checked /etc/passwd and the line for the default user reads;

```
dell:x:1000:1000:DELL,,,:/home/dell:/bin/bash
```

However, *sudo passwd* still asks for a password.

I'm sick and can't move more more than some meters away from my bed. Therefore I can't use a live CD to generate and put a known password hash on /etc/passwd.

Could you please tell me what to do?,

Thanks you very much in advance.

---

### Post by oldfred on 2013-08-29
If it was a correct OEM install it should have asked for a new user & pw on first boot. This is mostly how to install but see last paragraph. Did you see that?
 OEM mode so user can add name & password later:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

      
 [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

---

### Post by mario11 on 2013-08-29
Thanks you so much!. It worked fine.

---

