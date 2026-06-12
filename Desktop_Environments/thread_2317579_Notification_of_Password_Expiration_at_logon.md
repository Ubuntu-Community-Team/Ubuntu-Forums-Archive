---
title: "Notification of Password Expiration at logon"
date: 2016-03-17
forum: Desktop Environments
---

### Post by guilly on 2016-03-17
Hi,

I'm in the process of developing a kubuntu image for a clients and am leveraging Active Directory for authentication source. Is there a way to notify users of password expiration at logon ? It seems to work fine inside of a terminal session. I've tested this by issuing sudo command which prompts me for my password I received the notification and was even able to change the password successfully. But from what I can see at the initial KDE logon screen no notification is shown and even worse if the users password is in fact expired you receive an error stating incorrect password which can be miss leading....

---

### Post by Edison_James on 2016-03-19
I am not aware of any way to do this outside of the terminal.

---

### Post by guilly on 2016-03-21
I'm a little shocked there isn't an elegant way of dealing with expired passwords at logon. How can you possibly integrate your desktops within the enterprise without having proper LDAP integration ? The only solution I've found was to create a script which makes a call to AD via LDAP and do some basic math by looking at the passlastset attribute.

Here's the reference: [https://askubuntu.com/questions/691010/how-do-i-display-login-message-such-as-password-expiry-warning](https://askubuntu.com/questions/691010/how-do-i-display-login-message-such-as-password-expiry-warning)

Unless I can find a better solution I guess this is the solution I will have to go with....

---

### Post by Dorian_Mode on 2016-03-23
Interesting. In The Linux Command Line for Beginners. chapter 5; Users and User accounts. It shows that it is possible to set or change the default warning (which is 7 days) so if a password is set to expire, the user will receive a warning while logging in for seven days. So it is possible, but I will have to read this some more to see if he actually shows how to do it.
Edit; He doesn't actually explain the process in the book, unfortunately. But maybe you can figure out how to edit the /etc/passwd config. file.

This is an ebook available from Amazon.
[URL="https://www.amazon.ca/Linux-Command-Line-Beginners-Guide-ebook/dp/B007CD3SOI/ref=sr_1_13?s=digital-text&ie=UTF8&qid=1458782526&sr=1-13&keywords=linux+command+line"]https://www.amazon.ca/Linux-Command-Line-Beginners-Guide-ebook/dp/B007CD3SOI/ref=sr_1_13?s=digital-text&ie=UTF8&qid=1458782526&sr=1-13&keywords=linux+command+line


[/URL]

---

### Post by guilly on 2016-03-29
Yes, if you're using local authentication this will work. But once you start relying on LDAP there doesn't seem to be a mechanism to notify the user when the password is about to expire....

---

### Post by gordintoronto on 2016-03-29
This does not answer your question, but perhaps it is relevant: most security experts now feel that having passwords expire is a bad thing, which actually reduces security.

---

