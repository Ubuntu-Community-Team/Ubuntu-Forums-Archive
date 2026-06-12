---
title: "need help with this command"
date: 2006-03-01
forum: Desktop Environments
---

### Post by tidy_boy on 2006-03-01
Hi guys I have figured out how to import my thunderbird emails from windows over to linux but I am trying to get to this location 

~/.thunderbird/xxxxxxxx.default/

I have tried cd ~/.thunderbird/ but it does not work.

All I have to do is drop my emails from the location on my windows pc into the linux one

---

### Post by markymarknz on 2006-03-01
hi tidy_boy
have you already got the files accessible from the windows partition?
if not you can just mount it then get the files
if the folder doesn't exist the xxxxx.default one then just make a new one with:
mkdir /home/<name>/.thunderbird/xxxx.default

hope this helps

---

### Post by tidy_boy on 2006-03-01
Hey mate I have had to import my emails from outlook in windows to thunderbird and I now have the folder with all my emails in linux. I did not dual boot you see. :D

I just need to know how i get to the thunderbird directory in linux :D

---

### Post by tidy_boy on 2006-03-01
I have been following this guide 
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

On Windows XP/2000, the path is usually 

%AppData%\Thunderbird\Profiles\xxxxxxxx.default\, where xxxxxxxx is a random string of 8 characters. Just browse to C:\Documents and Settings\[User Name]\Application Data\Thunderbird\Profiles\  and the rest should be obvious.

On Linux, the path is usually ~/.thunderbird/xxxxxxxx.default/


I have got my emaild from windows just need to add them to the linux folder

---

### Post by markymarknz on 2006-03-01
If you just create the directory (if not already there)
mkdir /home/<name>/.thunderbird/xxxx.default
then move the files into it - should do the trick

---

### Post by tidy_boy on 2006-03-01
mkdir: cannot create directory `/home/matt/.thunderbird/xxxx.default': No such file or directory


Any ideas

---

### Post by markymarknz on 2006-03-01
what's the permission for .thuderbird folder?
ls -la /home/matt/

---

### Post by Ramses de Norre on 2006-03-01
Does ~/.thunderbird already exist?
If not: mkdir ~/.thunderbird
mkdir ~/.thunderbird/xxxx.default

It's very easy to use ~ instead of /home/username, in terminal you can type it directely with page down.

---

### Post by tidy_boy on 2006-03-01
Sorted the problem the folder that I needed to put my emails was not called thunderbird it is mozzila.thunderbird.

Problem sorted 


Cheers guys :D

---

### Post by markymarknz on 2006-03-01
sweet glad its all good now :D

---

