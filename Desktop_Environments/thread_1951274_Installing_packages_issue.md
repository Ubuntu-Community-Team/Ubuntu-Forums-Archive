---
title: "Installing packages issue"
date: 2012-04-02
forum: Desktop Environments
---

### Post by dicamarques on 2012-04-02
Hi, i'm new to lubuntu and yesterday i installed it on my old computer.
I'm trying to install skype and it asks me for my password ("you need to grant administrative rights to install software"), i enter the correct password and it tells me it is incorrect.
Is there a way to disable the lubuntu from requesting passwords to install packages, or i need to enter a password that's not from my user??

Thanks

---

### Post by codemaniac on 2012-04-02
Whenever you fire any system administration command with the help of sudo , the system will as k you for the admin password .It is only for your securities sake !!

---

### Post by dicamarques on 2012-04-02
> **codemaniac said:**
> Whenever you fire any system administration command with the help of sudo , the system will as k you for the admin password .It is only for your securities sake !!

Ok, but the problem is that i insert the correct password and he tells me it's incorrect

---

### Post by kc1di on 2012-04-02
> **dicamarques said:**
> Ok, but the problem is that i insert the correct password and he tells me it's incorrect
Did you by any chance use upper case when you entered the original password? passwords are case sensitive in Linux. 

Just a thought.

---

### Post by dicamarques on 2012-04-02
> **kc1di said:**
> Did you by any chance use upper case when you entered the original password? passwords are case sensitive in Linux. 

Just a thought.

I am 100% sure i'm typing the correct password i even created a new user with a basic passwrod to test ( 123456 ).

---

### Post by codemaniac on 2012-04-02
If you have downloaded the .deb file for skype, you should be able to just double click it and it will install skype in your system .

---

### Post by kc1di on 2012-04-02
only other thing I can think of is it's asking for a skype password not your admin password.
Worth a try.

---

### Post by dicamarques on 2012-04-02
> **kc1di said:**
> only other thing I can think of is it's asking for a skype password not your admin password.
Worth a try.
 How would that be possible? I havent still installed it and my skype and lubuntu password are the same.

---

### Post by dicamarques on 2012-04-02
Here's a pic of it.

[IMG]http://desmond.imageshack.us/Himg580/scaled.php?server=580&filename=photo0038b.jpg&res=medium[/IMG]

This time trying to upgrade from 11.04 to 11.10.
Any help?

---

### Post by codemaniac on 2012-04-02
Yea sure updating the system definately require admin privileges .
Have you tried resting your password .
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by dicamarques on 2012-04-02
> **codemaniac said:**
> Yea sure updating the system definately require admin privileges .
Have you tried resting your password .
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

No luck, i have managed to use skype with the static version.
Is it because i installed the mini version?
Btw For some random reason lubuntu doenst store my keyboard layout it always changes to the US version.

---

### Post by Rodney9 on 2012-04-02
Keyboard Layout Problem - [http://ubuntuforums.org/showthread.php?t=1874069](http://ubuntuforums.org/showthread.php?t=1874069)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by dicamarques on 2012-04-02
> **Rodney9 said:**
> Keyboard Layout Problem - [http://ubuntuforums.org/showthread.php?t=1874069](http://ubuntuforums.org/showthread.php?t=1874069)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

Thanks
 ):P

---

### Post by dicamarques on 2012-04-02
SUCCESS!!!!!!!!!!!
i've googled eveywhere and in a atemp to make it work i tryed to enable the root account
```
sudo passwd root
```

and when it asked me for a password i entered root and i'm installing skype at the time im typing .

Thanks for the help of everyone :D

---

