---
title: "problem on creating new folder"
date: 2012-02-21
forum: Desktop Environments
---

### Post by ramakanta on 2012-02-21
i have recently install ubuntu 10.10 desktop edition.
but my problem is can't be creat a new folder inside the ***[FONT=Lucida Console]file system[/FONT]***. please help me how to create a folder inside the [FONT=Lucida Console]***file System.***[/FONT]
 thank you.
:confused:

---

### Post by drmrgd on 2012-02-21
> **ramakanta said:**
> i have recently install ubuntu 10.10 desktop edition.
but my problem is can't be creat a new folder inside the ***[FONT=Lucida Console]file system[/FONT]***. please help me how to create a folder inside the [FONT=Lucida Console]***file System.***[/FONT]
 thank you.
:confused:

By "File System", what are you referring to?  I mean, what is the exact location where you're trying to create the file?  Also, please copy and paste the error that you're getting here so that we can evaluate it.

If you're trying to create the folder outside of your /home directory, it's likely that the problem is due to insufficient privileges.  You need to be administrator in order to create folders outside of home/, which you can get if you issue:

```
sudo mkdir <directory_name>
```

---

### Post by ramakanta on 2012-02-22
i have attached a scr shoot , where  i want to create a folder.
 i done , this command , that you sent me. thanks..
but now i cant be copy and paste of my files inside . please help me.

than you.

---

### Post by claracc on 2012-02-22
You need to use sudo too in order to copy files in a folder owning by root.

In a xterm, you will have to run:

sudo cp /directory/name_of_file_you_want_to_copy /folder_you_want_the_file_to_be_copied/. You have to specify the complete path where the file you want to copy is and the path where you want to copy it.

Before doing it I recommend two good documents for understanding sudo and cp as well as using command line:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by ramakanta on 2012-02-22
if possible kindly give some simple example..

suppose i have  a mp3 file "***rag.mp3***" in home directory inside  the ***Music*** folder .
i want to copy this ***rag.mp3*** to ***File System/usr/rama***
***rama*** is folder that i have created.
than you.

---

### Post by claracc on 2012-02-22
I think you have to have your music files in your /home/name_of_user/music/ folder, it is better because /home/name_of_user/ is the folder were are all the user files and where you have all permissions to do or undo.

Anycase

you open an xterm: menu apps/accesories/xterm, then you go to Music folder:
cd /home/Music and there you write sudo cp rag.mp3 /home/usr/rama/
you are asked for your root password, you introduce it and it is all.

---

### Post by drmrgd on 2012-02-22
> **ramakanta said:**
> if possible kindly give some simple example..

suppose i have  a mp3 file "***rag.mp3***" in home directory inside  the ***Music*** folder .
i want to copy this ***rag.mp3*** to ***File System/usr/rama***
***rama*** is folder that i have created.
than you.

As claracc said, any directories that are not in your home folder require elevated permissions in order to modify.  So, you have to either do it by the terminal and issue 'sudo' in front of all of the commands.  If you'd prefer to work in Nautilus (the graphical file manager), then in the terminal issue:

```
gksudo nautilus
```

Once you enter your password, you'll be able to run the graphical file manager as root.  However, you **need to be very careful!**  While you have root level permissions, you can really do some damage on the system if you delete the wrong things or move things around that need to be in a certain place.

Can we ask why you want to put your music in /usr?  That's not really the place to store such things, and to be honest, you're really better off not messing with the system files (which include /usr) unless you really need to, and know what you're doing.

---

### Post by ramakanta on 2012-02-22
thanks suggestion.
actually  i am not any interest to copy my music file  in side the usr folder. it is just example .i am new to linux . so just i want to learn how to copy a file ,create  a folder. etc.
thanks again

---

### Post by ramakanta on 2012-02-22
thank you.

---

### Post by kg4cna on 2012-02-23
It's good that you want to learn how to do things in linux...BUT, as the previous responders stated, it is best to NOT do those things outside your "home" folder....lest you unintentionally damage your system and not know what you did.

Enjoy!
A~

---

