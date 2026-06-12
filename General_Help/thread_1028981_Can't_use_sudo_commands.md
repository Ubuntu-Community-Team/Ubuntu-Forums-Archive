---
title: "Can't use sudo commands"
date: 2009-01-02
forum: General Help
---

### Post by Zebra_ on 2009-01-02
I'm a complete beginner at Linux, and whenever I try to use a sudo command it comes up with [sudo] password for user:, and I enter my user password, but it says "Sorry, try again". I know it's the right password because I can use it to change the password in System>Admin>Users and Groups. Any suggestions?

---

### Post by eBoxNet on 2009-01-02
is there any possibility that you have change your user's group?
your group should be admins cause admins are sudoers.
pls check and let me know,thanks

---

### Post by Zebra_ on 2009-01-02
I'm not sure. How do you check this?

---

### Post by eBoxNet on 2009-01-02
System -> Administration -> User Accounts

(or something like that i am not able to check right now)

but i think you are an admin cause you said you can "unlock" things...
thats weird :/

do you have any uppercase letters on your password?

---

### Post by Zebra_ on 2009-01-02
It says Name: *My name* and "root" and Login name: "user" and "root" and Home directory: /home/user/ and /root. my password is only lowercase letters and numbers

---

### Post by Zebra_ on 2009-01-02
bump

---

### Post by jtgd on 2009-01-04
What does your /etc/sudoers file look like?

---

### Post by oneadvent on 2009-01-04
Have you tried changing your password to something stupid simple like "1234" and trying again?

Maybe there is a character that isn't translating right for you in the terminal.

---

### Post by Zebra_ on 2009-01-04
Sorry, how do you look at that?

---

### Post by Zebra_ on 2009-01-04
Well I tried changing my password and that didn't work. Is there any way to reset your password?

---

### Post by oneadvent on 2009-01-04
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

That link should do it for you.

We've all had to do it at some point.

---

### Post by Zebra_ on 2009-01-04
Wow thanks a lot! I'll try with this new password and see if it works...

---

### Post by Zebra_ on 2009-01-04
Hey thanks a bundle guys that did the trick.

---

### Post by pastalavista on 2009-01-09
There's a good tutorial on how to fix it [[here]]("http://www.psychocats.net/ubuntu/fixsudo")

---

