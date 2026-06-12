---
title: "password problem in terminal mode"
date: 2006-03-02
forum: Desktop Environments
---

### Post by Stem on 2006-03-02
Total newbie, want to type commands in terminal mode, type any sudo command and it asks for a password. Can not type anything in . Return works but letters and numbers do not, what am I missing;)

---

### Post by bluevoodoo1 on 2006-03-02
It's probably working, when you type your password nothing will show up, that's usual. You won't see ****** or ### or anything like that. It's a security measure not to have that. After your sudo command try your password in, hit return and see if it works! (I hope I answered what you mean't!)

---

### Post by PaintballMan10988 on 2006-03-02
I am also totaly new,  and having the same problem.  This is what it tells me...

mike@Typhoon:~$ su
Password:
su: Authentication failure
Sorry.


I am 100% sure i have the right password.  Any ideas?

Thanks so much,

Mike

---

### Post by Stem on 2006-03-02
Thanks, that is what I meant, since the cursor did not move I did not think to hit the return after the password was entered. It also took me a couple of minutes to figure out how to use the post tools to post and answer!

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=PaintballMan10988]I am also totaly new,  and having the same problem.  This is what it tells me...

mike@Typhoon:~$ su
Password:
su: Authentication failure
Sorry.


I am 100% sure i have the right password.  Any ideas?

Thanks so much,

Mike[/QUOTE]


Try using "sudo" instead of "su" then enter your user password.

This link might be of some use...
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

and these threads...
[http://ubuntuforums.org/showthread.php?t=99601&highlight=su](http://ubuntuforums.org/showthread.php?t=99601&highlight=su)
[http://ubuntuforums.org/showthread.php?t=114843&highlight=su](http://ubuntuforums.org/showthread.php?t=114843&highlight=su)

---

### Post by Stem on 2006-03-02
MIke, are you typing in the "sudo " command, I do not see that in your example, I typed in a sudo command, it asked for password and after entering and the help from bluevoodoo1 it accepted my command lines

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=Stem]MIke, are you typing in the "sudo " command, I do not see that in your example, I typed in a sudo command, it asked for password and after entering and the help from bluevoodoo1 it accepted my command lines[/QUOTE]

yeah he wrote...

> 
mike@Typhoon:~$ su
Password:
su: Authentication failure
Sorry.


"Su" is a valid command. "su" will try to access the root account (which is disabled by default). Check this [post]("http://ubuntuforums.org/showpost.php?p=560997&postcount=8") for more detail.

---

### Post by PaintballMan10988 on 2006-03-02
I tihnk i must be doing something wrong.  I will make a new thread.

Thanks for the help,

Mike

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=PaintballMan10988]I tihnk i must be doing something wrong.  I will make a new thread.

Thanks for the help,

Mike[/QUOTE]

Well what are you trying to do exactly? (maybe I can help) :-k

---

### Post by pigphish on 2008-05-02
had the same exact problem however "sudo su" did the trick. 

Maybe someone more experienced can elaborate. I assume its a gui thing

---

### Post by c4v3m4n on 2008-05-02
just remember that you can't see your password when typing it.  That confuses a lot of people new to it.

---

