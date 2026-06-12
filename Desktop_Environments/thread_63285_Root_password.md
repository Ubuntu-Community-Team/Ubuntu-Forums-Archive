---
title: "Root password"
date: 2005-09-07
forum: Desktop Environments
---

### Post by AhmedShaheen on 2005-09-07
I'm new to Ubuntu . I installed the 5.04 version . 
and I made a user called ahmed with a password but in Admininstration   I want the Root password and I didn't know it because the setup wizard didn't ask me about it .
any one help me please ??

---

### Post by hashimoto on 2005-09-07
[QUOTE=AhmedShaheen]I'm new to Ubuntu . I installed the 5.04 version . 
and I made a user called ahmed with a password but in Admininstration   I want the Root password and I didn't know it because the setup wizard didn't ask me about it .
any one help me please ??[/QUOTE]
 Hi and welcome! 

No root in Ubuntu. Ubuntu uses "sudo" for administrative tasks.
Please read: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

And this is your real friend with Ubuntu:
[http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html)

---

### Post by karuptdata on 2005-09-07
Sure its really simple my friend...what you need to do is open a terminal and within the terminal you need to type in "gdmsetup" this will launch the gnome setup manager.At the top of the manager you will have several tabs select the one that says security and then select "Allow root to login with GDM" then close that window. 

The second part to your question to change the root password open a terminal window and type "passwd root" you then will have to enter user password then it will prompt you to change your root password, and you should be able to login to root from the login screen. 

For additional info check out this site it really helped me learn ubuntu! 

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by arnieboy on 2005-09-07
[QUOTE=karuptdata]The second part to your question to change the root password open a terminal window and type "passwd root" you then will have to enter user password then it will prompt you to change your root password, and you should be able to login to root from the login screen.[/QUOTE]
thats ```
sudo passwd root
```

---

