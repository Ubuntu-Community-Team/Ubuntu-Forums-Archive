---
title: "Installing (application/x-executable)"
date: 2009-05-15
forum: General Help
---

### Post by mancimailman on 2009-05-15
I recently downloaded grid wars. It was a zip file, I extracted to a folder I created which I named gridwars. After extraction there are 3 folders, gfx, music, and sounds. There is a .dll called bass.dll. A txt document called Config.txt. AND then there is what I figure I must install, the icon for it is a diamond (same as the .dll) it is just called gridwars. When I right click and go to properties it says it is a "executable (application/x-executable)". Double clicking does nothing. Under permissions, in properties, I tried checking off the "allow executing file as a program" still nothing. 

chmod 755 gridwars.x
chmod: cannot access `gridwars.x': No such file or directory

./gridwars.x
bash: ./gridwars.x: No such file or directory

chmod +x <gridwars>
bash: syntax error near unexpected token `newline'

./<gridwars>
bash: syntax error near unexpected token `newline'

I know this is simple, sorry for the long explanation trying not to miss anything, the folder i created for grid wars is under my home directory.

---

### Post by lisati on 2009-05-15
I just googled "Grid Wars" and found this: [http://worldofstuart.excellentcontent.com/grid/wars.htm](http://worldofstuart.excellentcontent.com/grid/wars.htm)
 As near as I can make out, this is a Windows program. You will need to use Wine to run it. Have a look here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by mancimailman on 2009-05-15
What I am trying to install is not a windows program, it is for linux. It is not, a windows .exe
I am already fammiliar with wine as well :)

---

### Post by michy99 on 2009-05-15
In the terminal, switch to the directory where gridwars is located and enter

```
./gridwars
```

If it doesn't work what error message do you get?

---

### Post by michy99 on 2009-05-15
Just for the fun of it, I downloaded gridwars to see if I could get it to run. I double-clicked on gridwars and it started right up. Did you try the command I gave in the post above? What was the result?

---

### Post by mancimailman on 2009-05-16
how do i switch to the directory where grid wars is located in the terminal? im new to linux and ubuntu, decided to give up on windows

manicmailman@m2Da2Dn2Di2Dc:~$ [code]./gridwars[code]
bash: [code]./gridwars[code]: No such file or directory
I made a folder in my home directory and extracted the zip file of gridwars that i downloaded into that folder

---

### Post by michy99 on 2009-05-16
Sorry, I had an error in my post above which is corrected now. To change directories in linux, use the cd command. When you open the terminal, you are in your home directory. If the folder you made is named gridwars then

```
cd gridwars
./gridwars
```

See if this works or if you get an error message.

---

### Post by mancimailman on 2009-05-16
This is what I got, 


cd gridwars
manicmailman@m2Da2Dn2Di2Dc:~$ cd gridwars
manicmailman@m2Da2Dn2Di2Dc:~/gridwars$ ./gridwars
bash: ./gridwars: Permission denied
manicmailman@m2Da2Dn2Di2Dc:~/gridwars$




 by the way thanks for all your help so far

---

### Post by michy99 on 2009-05-16
Sorry I didn't get back to you sooner; I had some things to tend to. Ok, in the gridwars directory do
```
ls -l
```
and post the result.

---

### Post by mancimailman on 2009-05-16
manicmailman@m2Da2Dn2Di2Dc:~$ cd gridwars
manicmailman@m2Da2Dn2Di2Dc:~/gridwars$ ls -l
total 640
-rwx--x--x 1 manicmailman manicmailman  95288 2006-02-17 21:25 bass.dll
-rwx--x--x 1 manicmailman manicmailman   3302 2006-03-09 13:49 Config.txt
drwx------ 6 manicmailman manicmailman   4096 2006-03-14 09:27 gfx
-rw-rw-r-- 1 manicmailman manicmailman 529332 2006-03-15 20:25 gridwars
drwx------ 2 manicmailman manicmailman   4096 2006-03-14 09:27 music
drwx------ 2 manicmailman manicmailman   4096 2006-03-14 09:27 sounds
manicmailman@m2Da2Dn2Di2Dc:~/gridwars$

Dont worry about time as i am away from the computer lots, and thanks for all your help

This is what I got after changing the permissions in properties,

manicmailman@m2Da2Dn2Di2Dc:~/gridwars$ ./gridwars
./gridwars: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
manicmailman@m2Da2Dn2Di2Dc:~/gridwars$ 


manicmailman@m2Da2Dn2Di2Dc:~/gridwars$ ls -l
total 640
-rwx--x--x 1 manicmailman manicmailman  95288 2006-02-17 21:25 bass.dll
-rwx--x--x 1 manicmailman manicmailman   3302 2006-03-09 13:49 Config.txt
drwx------ 6 manicmailman manicmailman   4096 2006-03-14 09:27 gfx
-rwxrwxr-x 1 manicmailman manicmailman 529332 2006-03-15 20:25 gridwars
drwx------ 2 manicmailman manicmailman   4096 2006-03-14 09:27 music
drwx------ 2 manicmailman manicmailman   4096 2006-03-14 09:27 sounds
manicmailman@m2Da2Dn2Di2Dc:~/gridwars$ 

well you cant see it here, but in my terminal befor I changed the permissions, in this line "-rwxrwxr-x 1 manicmailman manicmailman 529332 2006-03-15 20:25 gridwars" <----gridwars was not highlighted green, after changing permissions, it is high lighted green, look at attached picture......

I also got this after typing in ./gridwars, in the gridwars directory after changing permission.,

manicmailman@m2Da2Dn2Di2Dc:~/gridwars$ ./gridwars
./gridwars: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by michy99 on 2009-05-16
try```
chmod +x gridwars
./gridwars
```

Make sure you are in the gridwars directory first. For some reason the file is not executable at the moment. The first line should fix that.

---

### Post by mancimailman on 2009-05-16
I GOT IT TO WORK, thanks to you michy99 and some google I was able to figure it out, without the error messages I received with the advice you gave me tho i would not have figured it out,it turns out that libstdc++6 (4.3.2-1) will noty work with gridwars, needed to install the old version which acctually runs along side 6, I installed it with apt-get, (sudo apt-get libstdc++5) neways right after I did that I double clicked on it and it works perfectly.



here is the link I got the info from 

 [http://www.linuxquestions.org/questions/debian-26/error-while-loading-shared-libraries-libstdc.so.5-cannot-open-shared-object-file-677449/](http://www.linuxquestions.org/questions/debian-26/error-while-loading-shared-libraries-libstdc.so.5-cannot-open-shared-object-file-677449/)

Also, I would like to mark this as [SOLVED] but I do not know how?

---

### Post by michy99 on 2009-05-17
Glad you got it working. I guess I must have had libstdc++5 installed.

The only way to mark a thread as solved now is to edit your original post and add [Solved] to the subject line.

---

### Post by mrsocksman on 2009-06-14
> **mancimailman said:**
> I GOT IT TO WORK, thanks to you michy99 and some google I was able to figure it out, without the error messages I received with the advice you gave me tho i would not have figured it out,it turns out that libstdc++6 (4.3.2-1) will noty work with gridwars, needed to install the old version which acctually runs along side 6, I installed it with apt-get, (sudo apt-get libstdc++5) neways right after I did that I double clicked on it and it works perfectly.



here is the link I got the info from 

 [http://www.linuxquestions.org/questions/debian-26/error-while-loading-shared-libraries-libstdc.so.5-cannot-open-shared-object-file-677449/](http://www.linuxquestions.org/questions/debian-26/error-while-loading-shared-libraries-libstdc.so.5-cannot-open-shared-object-file-677449/)

Also, I would like to mark this as [SOLVED] but I do not know how?
dude, i got it to work to, because its   sudo apt-get INSTALL libstdc++5, lol but hey, at least it worked booh yeah

---

