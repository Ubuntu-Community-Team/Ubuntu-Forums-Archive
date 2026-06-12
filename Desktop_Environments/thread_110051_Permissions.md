---
title: "Permissions"
date: 2005-12-29
forum: Desktop Environments
---

### Post by iameatingjam on 2005-12-29
Just installed kubuntu, my first time using linux, having a bit of trouble. While on the administration account (the only account) I don't have write permissions for my main drive (except the shared folder, home folder and public stuff) in properties it says I should be able to modify/write things, but i can't. I can't modify permissions for the drive either.... What do i do?

---

### Post by HermanAB on 2005-12-30
One word:
sudo

---

### Post by veloct on 2005-12-30
That's built in security. Only root can make changes to all files.  But as HermanAB said, you can use 'sudo' to issue a command as root.

---

### Post by iameatingjam on 2005-12-30
Could anyone give me some instructions, I tried downloading the sudo thing but got an error that i couldn't expand it. Please, linux is so confusing for me right now.

---

### Post by cwaldbieser on 2005-12-30
[QUOTE=iameatingjam]Could anyone give me some instructions, I tried downloading the sudo thing but got an error that i couldn't expand it. Please, linux is so confusing for me right now.[/QUOTE]
"sudo" is a command you must use from the terminal.  This is similar to the MS-DOS prompt in Windows.  You can find the terminal under the Accessories menu.

Sudo will let you run a command as the super-user.  In Ubuntu, this user is called root, and has user-id 0.

The basic syntax is:
```

$ sudo command

```
(The "$" is the terminal prompt.)
So, if you need to run the file explorer (konqueror) as root, you open the terminal, and type:
```

$ sudo konqueror

```
It will ask you for your password.  You won't see it as you type.

Normally, you don't want to leave a program running as root for very long, because it is easy to mess up your system if you forget that it can basically do anything including deleting important files.

When you get more familiar with commands at the terminal, you will start using sudo with commands that are more concise, so you won't have to worry about leaving sudo programs running.

---

### Post by iameatingjam on 2005-12-30
Thankyou, that makes it much clearer.

---

### Post by iameatingjam on 2005-12-30
Um, one more thing, do I have to use a command to execute a program? I tried downloading some applications but they don't want to launch. If not, what could be wrong?

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=iameatingjam]Um, one more thing, do I have to use a command to execute a program? I tried downloading some applications but they don't want to launch. If not, what could be wrong?[/QUOTE]
Did you use synaptic to get the program, or did you actaually download a tarball (file ending in .tar.gz or .tar.bz2)?  If you download with synaptic, it will normally put it on the menu, but you can always run the program from the terminal, too.

What was the program called?

---

### Post by iameatingjam on 2005-12-31
[QUOTE=cwaldbieser]Did you use synaptic to get the program, or did you actaually download a tarball (file ending in .tar.gz or .tar.bz2)?  If you download with synaptic, it will normally put it on the menu, but you can always run the program from the terminal, too.

What was the program called?[/QUOTE]

There were a few programs, all tarballs, most of them were emulators, I especially want Zsnes or Mupen. Some games too . either nothing happens when I try to launch something or I get the window asking what application I want to open it with.

---

### Post by whitesox on 2005-12-31
use synaptic, , its the frontend to apt-get (ignore that if you dont understand it) and it is very powerful.  Some programs arent in the repositores, in that case, add more (its in the forums somewhere) if it isnt in that, well, use a tarball, then just type in the name of the program in the terminal. Mupen would be ```
& mupen
``` no caps

---

### Post by whitesox on 2005-12-31
use synaptic, iameatingjam, its the frontend to apt-get (ignore that if you dont understand it) and it is very powerful. If you install a program with it, it WILL work.  However. some programs arent in the repositores, in that case, add more (its in the forums somewhere) if it isnt in that, well, use a tarball, install it, then just type in the name of the program in the terminal. Mupen would be ```
& mupen
``` no caps

installing a tar file is tricky, untar the file, then open up the terminal, then do $ cd <name of folder where it was untarred>, then do $ sh <usually install or setup.sh>, then enjoy
(sorry for all the editing, iameatingjam)

---

