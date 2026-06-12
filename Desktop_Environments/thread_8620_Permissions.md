---
title: "Permissions"
date: 2004-12-19
forum: Desktop Environments
---

### Post by Dko on 2004-12-19
How can I make it so I can have permissions to every file or directory.  I can't change permissions because im not "root" or what not.  I hope I explanied this well enough.  I just hate being told what I can and cannot do with my own files on my own computer.

---

### Post by Rancoras on 2004-12-19
Well, that's very dangerous to do.  If someone or a virus were to compromise your machine, they or it would have unfettered access to your system files, etc.  When you need root access, all you need to do is prepend sudo to your command if you're using the command line.  If you're trying to do something in the GUI that requires root permisson, then a password box should appear.  In that box you enter the password for the account you created during the install process or the password to an account that you have listed in the sudoers file.  Editing, the sudoers file is pretty advanced stuff, so get a little more familiar with linux before trying something like that.

---

### Post by Dko on 2004-12-19
The thing is what im trying to do doesn't give me a password.  Im trying to move a folder inside another folder and typing in these commands over and over just to get them right is gona drive me insane.  I just wan't to be able to move files around simply.

---

### Post by Ste on 2004-12-19
[QUOTE=Dko]The thing is what im trying to do doesn't give me a password.  Im trying to move a folder inside another folder and typing in these commands over and over just to get them right is gona drive me insane.  I just wan't to be able to move files around simply.[/QUOTE]
 If you can't use the terminal to move folders around.
Then sudo to root then run Nautilus to do what you have to then close it.
Not sure how safe this is but it should get the job done.

---

### Post by Rancoras on 2004-12-19
[QUOTE=Dko]The thing is what im trying to do doesn't give me a password.  Im trying to move a folder inside another folder and typing in these commands over and over just to get them right is gona drive me insane.  I just wan't to be able to move files around simply.[/QUOTE]

What files are you moving around?  what are you trying to accomplish?  Maybe there's a better way.  You really don't want to go mucking around with files that require root access to move, unless you are sure of what you are doing.  In an earlier post you said you were very new to linux.

---

