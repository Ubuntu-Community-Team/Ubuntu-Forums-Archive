---
title: "Password to unlock keyring"
date: 2011-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RSASKA on 2011-04-22
Hello,

Ever since I re-installed Ubuntu 9.04 on my Dell last week, now when I turn on the laptop, it asks for my password to unlock the keyring before connecting to my wireless router which connects to the Internet. 

I've tried searching these forums for a solution. I'm sure it's some simple option to turn off. Help!

---

### Post by gbrainin on 2011-04-22
I'm not using 9.04, so the menus may be somewhat different, but under System -> Administration -> Users and Groups you should be able to modify a user's privileges (on my system, it's under "Advanced").  If you give yourself the right to connect to a wireless network, it should stop asking for a password when it does that.

---

### Post by zeefunn12 on 2011-04-22
[IMG]http://images.maketecheasier.com/2009/03/keyring-prompt.jpg[/IMG]
If  you have set your Ubuntu machine to auto-login everytime you start your  computer, you will find that as soon as you reach your desktop, the  keyring manager will automatically pop up and ask you for the password  to unlock itself and retrieve the key to connect to the wireless  connection.
The keyring manager is integrated with Gnome such that  when you login from the main screen, it will automatically unlock  itself as well. However, if you use the auto-login function, Gnome will  skip the keyring manager process and log the user in without unlocking  the keyring manger.
To get rid of this annoyance, what you can do  is to set a blank password for the keyring manager so that it won’t  prompt you  for password everytime you login.
Do bear in mind that  setting a blank password for your keyring manager will expose all your  passwords to anyone that use your computer.
Go to *Applications -> Accessories -> Password and Encryption Keys*
[IMG]http://images.maketecheasier.com/2009/03/keyring-manager.jpg[/IMG]
Go to *Edit-> Preferences*
Highlight the *login – Automatically unlocked when user logs in* entry. Press the *Change Unlock Password* button.
[IMG]http://images.maketecheasier.com/2009/03/password-keyring.jpg[/IMG]
Enter your old password and leave blank for the new password. Click Change.
[IMG]http://images.maketecheasier.com/2009/03/keyring-change-pwd.jpg[/IMG]
It will prompt you for security issue. Click *Use Unsafe Storage* to continue.
[IMG]http://maketecheasier.com/wp-content/plugins/jquery-image-lazy-loading/images/grey.gif[/IMG]
Done. Next time when you login, the keyring manager won’t prompt you for password again.


More information please visit this site tipsmap.com

---

### Post by KegHead on 2011-04-22
Hi!

You could try;

system...admin...login

And login in automatically.

KegHead

---

