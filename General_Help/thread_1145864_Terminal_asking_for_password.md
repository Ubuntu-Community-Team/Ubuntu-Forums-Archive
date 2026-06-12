---
title: "Terminal asking for password"
date: 2009-05-02
forum: General Help
---

### Post by al3nmikho on 2009-05-02
When I open the terminal and try to install something or do anything, it will then ask for a password.  When I try to enter the password, It won't type anything. I tried multiple times but it woudn't work I even copy/paste my pass and it didn't work 


```
kickback@ubuntu:~$ sudo apt-get install build-essential
[sudo] password for kickback: Wib 


```

I need help guys! :(

---

### Post by joeabiraad on 2009-05-02
Hey

Can you copy paste what you are getting in terminal ? 

for example
```

jo@jo-desktop:~$ sudo vi jo
[sudo] password for jo: 
Sorry, try again.
[sudo] password for jo: 

```

---

### Post by lisati on 2009-05-02
> **al3nmikho said:**
> When I open the terminal and try to install something or do anything, it will then ask for a password.  When I try to enter the password, It won't type anything. I tried multiple times but it woudn't work I even copy/paste my pass and it didn't work 


```
kickback@ubuntu:~$ sudo apt-get install build-essential
[sudo] password for kickback: Wib 


```

I need help guys! :(

It's normal for sudo to ask for your password, and it's normal for it not to show. Just type in your regular password.

---

### Post by mb_webguy on 2009-05-02
When you're asked for your password in the terminal, it will not show that you're typing anything in order to prevent anyone who happens to be watching from seeing how many characters your password contains, which would make it easier for them to figure it out.  Just type it and hit enter.

---

### Post by al3nmikho on 2009-05-02
> **mb_webguy said:**
> When you're asked for your password in the terminal, it will not show that you're typing anything in order to prevent anyone who happens to be watching from seeing how many characters your password contains, which would make it easier for them to figure it out.  Just type it and hit enter.

Problem Solved, thank you very much!

---

