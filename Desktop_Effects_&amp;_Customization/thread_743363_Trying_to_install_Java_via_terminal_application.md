---
title: "Trying to install Java via terminal application"
date: 2008-04-02
forum: Desktop Effects &amp; Customization
---

### Post by JMann on 2008-04-02
Please bear with me.  I'm a brand new linux user :)

I'm trying to install java off of [http://java.com](http://java.com).  I'm being told to type "su" in the terminal and then type in my root password.  I'm typing in the same password I've been using for everything else - logging on, turning on other applications, etc., but now I'm getting "Authentication failure."  Also, no text appears when I type in the password, though I assume this is okay for security reasons.

Am I typing in the wrong password, or am I using terminal incorrectly?

Thanks.

---

### Post by TheMemphisExperience on 2008-04-03
You could do two things.

1) Change root's password through the user account settings. I don't know why that would help or why your login pass isn't letting you have temporary root permission. But it might do something.

user@compycomp:~$ sudo su
[sudo] password for omegapie: type password here! careful, it is hidden. make no mistakes! <3


2) Go to applications -> add/remove ->show: all available applications

Run a search for Java. Check the box most applicable. Apply changes. Wait.  Congrats, you can now play Java games and/or watch you tube.

Good Luck!

---

