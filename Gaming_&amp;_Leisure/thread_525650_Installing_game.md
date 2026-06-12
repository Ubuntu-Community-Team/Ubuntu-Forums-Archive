---
title: "Installing game"
date: 2007-08-14
forum: Gaming &amp; Leisure
---

### Post by burt_57 on 2007-08-14
I have downloaded a game for my grand son ... it is call Lualua.
It is saved in my home directory.
I just do not know how to install it.
And I can not find on the site where I have downloaded it how to install it. Can someone help.

---

### Post by shad0w_walker on 2007-08-14
Is this the game?

[http://www.phelios.com/linuxgames/lualua.html](http://www.phelios.com/linuxgames/lualua.html)

I have downloaded this one (If this isn't the one this might not help) and its very simple to setup.

Extract the .tar.gz file to somewhere approriate

In the folder you extracted the game to there is a file called laulau, double click it and it should run.

---

### Post by burt_57 on 2007-08-15
YA, that is the game and I see thee file you mention lualua,
and when I click on it nothing happen.
Oh well maybe I should try to download it again.

---

### Post by hikaricore on 2007-08-15
Try running it from a terminal instead.

It's likely you're just missing a libary required by the game or something of this sort.  Post any errors here.

---

### Post by burt_57 on 2007-08-15
> **hikaricore said:**
> Try running it from a terminal instead.

It's likely you're just missing a libary required by the game or something of this sort.  Post any errors here.

How do I run it in terminal ?
I had did it once but lost the command !

---

### Post by cogadh on 2007-08-15
It's under the Acessories menu in the Applications menu.

---

### Post by burt_57 on 2007-08-16
> **cogadh said:**
> It's under the Acessories menu in the Applications menu.

I know that, what I do not know is whar command I type to make it run :lolflag:

---

### Post by cogadh on 2007-08-16
Launch the terminal from the menu, then change directories to the directory where you extracted the files, then run the command/file that shad0w_walker told you to double-click on by typing its name into the terminal and hitting enter. Now if the file encounters any errors, those errors will be displayed in the terminal.

---

### Post by burt_57 on 2007-08-17
> **cogadh said:**
> Launch the terminal from the menu, then change directories to the directory where you extracted the files, then run the command/file that shad0w_walker told you to double-click on by typing its name into the terminal and hitting enter. Now if the file encounters any errors, those errors will be displayed in the terminal. 
robert@robert-desktop:~$ /home/robert/lualuaLinux\lualua
bash: /home/robert/lualuaLinuxlualua: No such file or directory
robert@robert-desktop:~$ 
 
bash: /home/robert/lualuaLinux: is a directory
robert@robert-desktop:~$ lualua
bash: lualua: command not found
robert@robert-desktop:~$

---

### Post by cogadh on 2007-08-17
If I am understanding your directories correctly, you need to change directories like this in the terminal:
```
cd lualuaLinux
```
Then run the application like this:
```
sh lualua
```
Then you should get some meaningful output in the terminal.

---

### Post by burt_57 on 2007-08-20
> **cogadh said:**
> If I am understanding your directories correctly, you need to change directories like this in the terminal:
```
cd lualuaLinux
```
Then run the application like this:
```
sh lualua
```
Then you should get some meaningful output in the terminal.

robert@robert-desktop:~$ cd lualuaLinux
robert@robert-desktop:~/lualuaLinux$ sh lualua
lualua: 3: Syntax error: Unterminated quoted string
robert@robert-desktop:~/lualuaLinux$ /sh lualua
bash: /sh: No such file or directory
robert@robert-desktop:~/lualuaLinux$ \sh lualua
lualua: 3: Syntax error: Unterminated quoted string
robert@robert-desktop:~/lualuaLinux$ sh lualua
lualua: 3: Syntax error: Unterminated quoted string
robert@robert-desktop:~/lualuaLinux$ 

will not work .......thank anyway

---

### Post by cogadh on 2007-08-20
This is a longshot, but after changing directories, try running it like this:
```
bash lualua
```

---

### Post by burt_57 on 2007-08-21
> **cogadh said:**
> This is a longshot, but after changing directories, try running it like this:
```
bash lualua
```
 
robert@robert-desktop:~$ cd lualuaLinux
robert@robert-desktop:~/lualuaLinux$ bash lualua
lualua: lualua: cannot execute binary file 

What am doing wrong... still will not work

---

### Post by Perfect Storm on 2007-08-21
Unpackaging:
```
tar zxfv lualuaLinux.tgz
```

switch to lualua directory:
```
cd lualuaLinux
```

launch Lualua:
```
./lualua
```

If any error or dependency missing output happens, please report back.

---

### Post by burt_57 on 2007-08-22
> **Artificial Intelligence said:**
> Unpackaging:
```
tar zxfv lualuaLinux.tgz
```

switch to lualua directory:
```
cd lualuaLinux
```

launch Lualua:
```
./lualua
```

If any error or dependency missing output happens, please report back.

robert@robert-desktop:~$ tar zxfv lualuaLinux.tgz
tar: lualuaLinux.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by Perfect Storm on 2007-08-22
Make sure you execute the command in the right place, eg;

file on Desktop
```
cd ~/Desktop
```

```
cd <path>
```
to change directory.

---

### Post by burt_57 on 2007-08-23
> **Artificial Intelligence said:**
> Make sure you execute the command in the right place, eg;

file on Desktop
```
cd ~/Desktop
```

```
cd <path>
```
to change directory.

My file was in home folder in a directory call lualuaLinux.
When I go there I see the folders, I can open the folder and see
the exe. file called lualua !
Anyway I have deleted it  ..trash it .
For now am going back to windows for a while .
Thank for all of your help , be back when I cool down  :lolflag:

---

### Post by Perfect Storm on 2007-08-23
Sounds like you downloaded the wrong package (you described there was an .exe file in it). You need to get the linux version.

---

### Post by Aesir09 on 2007-08-23
if you dont get it to work at tall, try the following,
uninstall:
```
sudo apt-get remove Lualua
```

**Lualua might be spelled with a lowercase L i wouldnt know**

install:

[code]sudo apt-get install Lualua[/code[

---

