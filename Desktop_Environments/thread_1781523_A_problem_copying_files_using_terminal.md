---
title: "A problem copying files using terminal"
date: 2011-06-13
forum: Desktop Environments
---

### Post by Banshee-2007 on 2011-06-13
Hi everybody
I am a new user , and have chosen Ubuntu 11.04 . However , I faced a problem when I started learning how to use the terminal . I tried to apply the copying command at first , but it didn't work , so I googled and found this : [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

I applied the instructions , but Ubuntu refused to copy files . I tried to copy a file called ( Blender ) and name the copy as gimp , so I wrote in the terminal : cp Blender gimp  . However it gave this message : ( cp: cannot stat `blender': No such file or directory ) , even though the file is still there . I applied the same thing in Linux Mint 9 and every thing had worked , but when I applied to again it gave me the same error message that Ubuntu gives me !!

I tried to apply the terminal of copy the whole directory , but the same problem was existed :(

Help please

---

### Post by Toz on 2011-06-13
Perhaps its a question of case sensitivity - Unix is case sensitive. Can you, in the terminal window, run the command: ```
ls -l
```so that we can see what files are located there?

Also, note that to copy directories, you need to use the -r paramater like:```
cp -r <source> <destination>
```

---

### Post by Banshee-2007 on 2011-06-14
hi
I entered this command , then terminal gave this :

> 
total 580
drwxr-xr-x 3 ahmed ahmed   4096 2011-06-14 23:54 Desktop
drwxr-xr-x 3 ahmed ahmed   4096 2011-06-13 22:48 Documents
drwxr-xr-x 3 ahmed ahmed   4096 2011-06-14 23:05 Downloads
-rw-r--r-- 1 ahmed ahmed    179 2011-06-11 04:01 examples.desktop
drwxr-xr-x 2 ahmed ahmed   4096 2011-06-11 04:18 Music
drwxr-xr-x 2 ahmed ahmed   4096 2011-06-13 14:07 Pictures
drwxr-xr-x 2 ahmed ahmed   4096 2011-06-11 04:18 Public
drwxr-xr-x 4 ahmed ahmed   4096 2011-06-13 14:06 Software Files
drwxr-xr-x 2 ahmed ahmed   4096 2011-06-11 04:18 Templates
drwxr-xr-x 2 ahmed ahmed   4096 2011-06-11 04:18 Videos
-rw-r--r-- 1 ahmed ahmed 534214 2011-04-30 05:38 winetricks



I dded the ( -r ) paramater , but nothing has changed .
And thanks for your replay

---

### Post by Toz on 2011-06-14
As you can see, there is no Blender file in your current directory, so it is unable to copy it. With the command line, you need to be inside the directory (or reference the directory) that contains the Bender file.

So the big question is, where is your Blender file located?

Try entering the following in the terminal window to locate the file. Post back the results.```
find ~ -name [Bb]lender -print
```

This command means:
**find** (file location program)
**~** (starting from your home directory)
**-name [Bb]lender** (where the name is either Blender or blender)
**-print** (print out the results to the screen)

---

### Post by Banshee-2007 on 2011-06-14
Thanks a lot for your effort and time

But I wonder , how did you know that there's no folder called ( blender ) in the desktop , while I do not see any name of any folder in the result that terminal gave .
So could you explain more for me how to use that command and how can I read the result if you don't mind please ??

An other thing , I checked the command that you've given me , and the result is :

> 

/home/ahmed/.PlayOnLinux/configurations/icones/Blender
/home/ahmed/Desktop/blender
/home/ahmed/Desktop/blender/blender
/home/ahmed/Documents/blender
/home/ahmed/.blender/scripts/blender
/home/ahmed/Software Files/blender-2.57b-linux-glibc27-i686/blender
/home/ahmed/.thumbnails/fail/blender



The result shows the folder in the desktop , that's why I checked using the copying command again , but that was useless .

---

### Post by nzjethro on 2011-06-14
> **Banshee-2007 said:**
> 
But I wonder , how did you know that there's no folder called ( blender ) in the desktop , while I do not see any name of any folder in the result that terminal gave .


The command ls -l lists all files in your current directory. I imagine that you were in your Ahmed (your username) folder, anx thus ls showed everything in /ahmed (i.e. your Desktop file, Music file etc). This can be seen by the file names, which are on the far right of the output from the ls command.

To list everything on your Desktop (if you think that is where blender is) type
```
cd /Desktop
ls -l
```

This will list all files and folders on your desktop (i.e. cd changes your current directory to /Desktop, ls lists files). You can see from your search for blender that it is indeed on the Desktop (i.e. /home/ahmed/Desktop/blender exists). You may have been trying to copy from the wrong directory. Try
```
cd /Desktop
```
Then your copy command.

---

### Post by Banshee-2007 on 2011-06-14
Thanks for you replay
I was in desktop when I tried the command of listing stuff inside the directory . But I think terminal gets that I was in my home folder .

I have a problem in changing my location inside the terminal . For instance , when I used your command :

> 
cd /Desktop
The terminal refused to get the terminal !!!

This is the result :

> 
bash: cd: /Desktop: No such file or directory

Actually I am becoming crazy because I don't like ubuntu because it's full of problem and bugs , and the the problem is every time I leave I come back for it , because there is no Linux is compatible with my laptop's drivers other it !!!

---

### Post by Derek Karpinski on 2011-06-14
```
cd ~/Desktop
```

OR:

```
cd /home/ahmed/Desktop
```

Both are the same thing.

---

### Post by conradin on 2011-06-14
There is no /Desktop folder by default atleast. / is the root directory.
enter the code
```
pwd
```
I think youre in /home/userName
so then, you dont have to change directories, just specify the absolute path. ```
cp -R /Where/The/File/is/blender /where/you/want/the/file/to/go/gimp
```

---

### Post by Banshee-2007 on 2011-06-14
First : I used the command :
> 
cd ~/Desktop
And it worked successfully . However , when I tried my copying command :

> 
cp blender gimp
terminal gave me this result :

> 
cp: omitting directory `blender'
Even though I checked the files which are there , and blender folder was there . So I used :

> 
cp -r blender gimp
And it worked successfully , although you guys said , and what the  tutorials in the thread above says that the command that contains ( -r )  , is used to copy directories to folders , so is there anything wrong  ??

Second : I used the command :

> 
pwd
and the result was like this :

> 
/home/ahmed/Desktop
After I specified my location in the terminal to make terminal define my  location as I am in my home folder , I applied this command :

> 
cp -r /home/ahmed/Desktop/blender /home/ahmed/Documents/gimp
And the result was like this :

> 
cp: cannot create directory `/home/ahmed/Document/gimp': No such file or directory
But when I removed the last word ( gimp ) , it copied the folder ( blender ) , with the same name to the Documents

So what can I do in this case , because you guys told me type ( gimp ) at last of the command .

---

### Post by Toz on 2011-06-14
> After I specified my location in the terminal to make terminal define my location as I am in my home folder , I applied this command :

Quote:
[QUOTE]cp -r /home/ahmed/Desktop/blender /home/ahmed/Documents/gimp 

And the result was like this :

> cp: cannot create directory `/home/ahmed/Document/gimp': No such file or directory

[/QUOTE]

If you look at the error message you received, you will see that you misspelled **Documents** (you used **[COLOR="Red"]Document[/COLOR]**). The folder **[COLOR="Red"]Document[/COLOR]** does not exist, therefore the error. 

> But when I removed the last word ( gimp ) , it copied the folder ( blender ) , with the same name to the Documents

So what can I do in this case , because you guys told me type ( gimp ) at last of the command . 

Rename the folder using the **mv** command like:```
mv /home/ahmed/Documents/blender /home/ahmed/Documents/gimp
```

---

### Post by nzjethro on 2011-06-14
> **Banshee-2007 said:**
> 
After I specified my location in the terminal to make terminal define my  location as I am in my home folder , I applied this command :

And the result was like this :



But when I removed the last word ( gimp ) , it copied the folder ( blender ) , with the same name to the Documents

So what can I do in this case , because you guys told me type ( gimp ) at last of the command .

IT is likely that you have no /home/ahmed/Documents/gimp folder. First up, run ls on your /home/Documents folder, with 
```
cd /home/Documents
ls
```
Check the output, there may be a folder called "Gimp" or "GIMP" (case is important). Else if it has to end up in a folder called /home/Documents/gimp, use
```
sudo mkdir /home/Documents/gimp
```
to make the folder. Then copy as you tried before.
Perhaps if you specify exactly what you are trying to do (i.e. copy /this/file/in/this/directory to /this/directory) we will be able to help a bit better.
The command line is pretty confusing to a new user, stick with it though, and it becomes faster and easier than GUI. And there's heaps of support out here for these kinds of tech issues. :D

---

### Post by Banshee-2007 on 2011-06-15
> **Toz said:**
> If you look at the error message you received, you will see that you misspelled **Documents** (you used **[COLOR=Red]Document[/COLOR]**). The folder **[COLOR=Red]Document[/COLOR]** does not exist, therefore the error. 



Rename the folder using the **mv** command like:```
mv /home/ahmed/Documents/blender /home/ahmed/Documents/gimp
```

About the first problem when I checked correcting the directory name , it worked successfully .

About the second command , I really didn't understand what's the use of this command . I mean how does it work ??

What I understood is :
I renames the name of the folder ( gimp ) . But , does that mean using the first part :

```

/home/ahmed/Documents/blender

```

is to name the folder ( gimp ) , after the name of the folder ( blender ) ??



> 

Else if it has to end up in a folder called /home/Documents/gimp, use
 	Code:
 	sudo mkdir /home/Documents/gimp 
to make the folder. Then copy as you tried before.



If this code is used to create a folder , then I think it's a big issue :o
Because this way , GUI would fast than using the terminal to create a folder , then copying the files I want !!

Thank you guys

---

### Post by Derek Karpinski on 2011-06-15
Because the title of your post is 'A problem copying files using terminal'.......
 
Everyone here is trying to help you copy files in terminal.

---

### Post by Banshee-2007 on 2011-06-15
> **Derek Karpinski said:**
> Because the title of your post is 'A problem copying files using terminal'.......
 
Everyone here is trying to help you copy files in terminal.


I know friend , and I enjoy that . Thanks to everybody helped me and gave some of his time and effort . I am not complaining about that , I'm just complaining about the difficulty of learning the terminal in the beginning , that's all the matter !!

---

### Post by Derek Karpinski on 2011-06-16
It's not so 'difficult' as it is different. Click, drag, & drop seem so much easier at first because you're used to it.  Once you understand the power of the command line, you'll find yourself using it more and more to do stuff like this.
 
To play around without breaking anything, try making a test folder in your home directory and copying, moving, deleting, changing ownership of those files in that directory.

---

### Post by goodbyemrevans on 2011-06-16
As a fellow newbie trying to learn my way around the command line, I've found William E. Shotts, Jr.'s [The Linux Command Line]("http://linuxcommand.org/tlcl.php") to be extremely helpful.

---

