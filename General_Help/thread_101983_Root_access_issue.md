---
title: "Root access issue"
date: 2005-12-11
forum: General Help
---

### Post by Rosette on 2005-12-11
Hey, I recently installed Ubuntu (4 hours ago :P) and have been happily puttering around learning the new OS and trying not to wake everyone in the flat up with my screaming and swearing. However I have a problem that screaming at my PC won't fix - namely I don't have root access... which is obviously a bit of a problem as it's my PC and it'd be real handy if I could actually do things with it. I only have my normal user account with its password, but no root access password. How do I get round this problem?

---

### Post by inn_ on 2005-12-11
You can enable root whit this command:
sudo passwd root
..-> password

---

### Post by DiscoKiller on 2005-12-11
go to: System->Administration->Users and Groups. Select the 'show all users and groups check box, then in the list find 'root', click properties and you can set your password in there, i recommend the set by hand option. once that is sorted you can run processes in terminal as root by typing sudo b4 your command. it will then ask you for your password. however if you want to run a session as root then u have to go to System->Administration->login screen setup. under one of the tabs there is an option to log in as root. i`d be more specific but my login screen setup doesnt want to work for some reason, anyways i hope this helps....it is my first post actually attempting to help someone!

---

### Post by DiscoKiller on 2005-12-11
easy as that eh?.....*hangs head*

---

### Post by linbetwin on 2005-12-11
[quote=Rosette]Hey, I recently installed Ubuntu (4 hours ago :P) and have been happily puttering around learning the new OS and trying not to wake everyone in the flat up with my screaming and swearing. However I have a problem that screaming at my PC won't fix - namely I don't have root access... which is obviously a bit of a problem as it's my PC and it'd be real handy if I could actually do things with it. I only have my normal user account with its password, but no root access password. How do I get round this problem?[/quote]

Hi, Rosette,

You don't necessariliy need to set a root password and it's not recommended. You can use your user password to gain root privileges. Type "sudo" in front of every command that requires root privileges. It will ask you for your user password the first time but then you'll be root for 15 minutes. So you'll be writing "sudo" before every command, but it won't ask you for the password for 15 minutes.

You can also do "sudo -s" and you'll be root until you issue "exit".

---

### Post by Madpilot on 2005-12-11
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

More discussion there about using sudo rather than root, and how to enable it if you think you really need it.

---

### Post by DiscoKiller on 2005-12-11
i`ll keep quiet in future i think :S

---

### Post by tkr7 on 2005-12-11
This sudo chpasswd root didn't help with me, but I maniged to get the root account into control by commanding: sudo su root, and after that I could easily change root's password and now su-command gives me root account after giving this password. This way you don't need to write "sudo" before every command if you are doing many things that require root's actions.

---

### Post by Rosette on 2005-12-12
Thanks for the help, guys. Appreciated.

---

