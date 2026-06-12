---
title: "permissions prob. with Windows ISO files"
date: 2009-01-11
forum: General Help
---

### Post by smartsmokey on 2009-01-11
So I downloaded XP the other day and now after all the .rar garbage, I have my iso. BUT - when I go to burn/copy/view/movie this ISO? It asks me for a password. Of course I type in my Ubuntu user password, which does not work. When it asks for a password, should I be entering the CD key or something? I REALLY don't understand this. How do I NOT have permission to manipulate the file???????????????

---

### Post by chex_m8 on 2009-01-11
make sure you have execute permission for the file
ls -l
if not then
chmod a+x "nameoffile"
you need to be in the same directory or specify the absolute pathname.

---

### Post by smartsmokey on 2009-01-11
> **chex_m8 said:**
> make sure you have execute permission for the file
ls -l
if not then
chmod a+x "nameoffile"
you need to be in the same directory or specify the absolute pathname.

im not sure i understand, do i fo to terminal and abitrarily type in ls-l? What does ls-l do? I'll run the chmod bit. Let you know
EDIT: okay ls -l shows me everything in my main user folder...however the iso is in a folder on the desktop, and I can't move it. How do I ls -l the desktop?
Okay I moved the folder into my main user file and did the ls -l again and the Windows file shows up, however when i type chmod a+x  Microsoft.Windows.XP.Professional.Corporate.SP2.Integrated.September.2007-ETH0 it does nothing, says no such command or file

---

### Post by chex_m8 on 2009-01-11
post the output of ls -l, it will show me if you have execute epermission for the file.
ls -l /home/username/Desktop

---

### Post by chex_m8 on 2009-01-11
Microsoft.Windows.XP.Professional.Corporate.SP2.In tegrated.September.2007-ETH0
ok is ther a space between ".In tegrated."
if so you need "" around the file name or rename it with no spaces.
also please dont edit your previos post just reply, its hard to tell youve respnded

---

### Post by smartsmokey on 2009-01-11
> **chex_m8 said:**
> Microsoft.Windows.XP.Professional.Corporate.SP2.In tegrated.September.2007-ETH0
ok is ther a space between ".In tegrated."
if so you need "" around the file name or rename it with no spaces.
also please dont edit your previos post just reply, its hard to tell youve respnded

.Corporate.SP2.Integrated.September.2007-ETH0<<<<<<no there's no space, sooooo?
PS before it goes into user/home/ it says "drwxr-xr-x"
PSSS the lettering of the file entry is blue by the way, if that means anything

---

### Post by smartsmokey on 2009-01-11
smartsmokey@smartsmokey-laptop:~$ chmod a+x " Microsoft.Windows.XP.Professional.Corporate.SP2.Integrated.September.2007-ETH0"
chmod: cannot access ` Microsoft.Windows.XP.Professional.Corporate.SP2.Integrated.September.2007-ETH0': No such file or directory
PS you have to trust me that there's no space between in tegrated, it looks fine in terminal and right now in the editing of this post - however once i change this post it will still say In tegrated, dont know why, so disregard that, dont let it throw u off

---

### Post by chex_m8 on 2009-01-11
an ls -l of the directory where the file is located would really help

---

### Post by smartsmokey on 2009-01-11
here's the readout for the Windows entry. I can't post the entire list, as it contains personal files, etc. 
drwxr-xr-x  2 smartsmokey smartsmokey     4096 2009-01-11 13:44 Microsoft.Windows.XP.Professional.Corporate.SP2.Integrated.September.2007-ETH0
WTF????? in terminal there is NO space in "integrated" yet when i copy and paste into here there IS a space

---

### Post by chex_m8 on 2009-01-11
you appear to have the proper permissions. 
lets test it one more time
try 
sudo chmod 777 "filename"

make sure you are executing these commands from the directory where the file is.

---

### Post by smartsmokey on 2009-01-11
> **chex_m8 said:**
> you appear to have the proper permissions. 
lets test it one more time
try 
sudo chmod 777 "filename"

make sure you are executing these commands from the directory where the file is.

smartsmokey@smartsmokey-laptop:~$ sudo chmod 777  Microsoft.Windows.XP.Professional.Corporate.SP2.Integrated.September.2007-ETH0
Password or swipe finger: 

smartsmokey@smartsmokey-laptop:~$ 
smartsmokey@smartsmokey-laptop:~$


smartsmokey@smartsmokey-laptop:~$ sudo chmod 777  Microsoft.Windows.XP.Professional.Corporate.SP2.Integrated.September.2007-ETH0
smartsmokey@smartsmokey-laptop:~$


smartsmokey@smartsmokey-laptop:~$ sudo chmod 777 " Microsoft.Windows.XP.Professional.Corporate.SP2.Integrated.September.2007-ETH0"
chmod: cannot access ` Microsoft.Windows.XP.Professional.Corporate.SP2.Integrated.September.2007-ETH0': No such file or directory
smartsmokey@smartsmokey-laptop:~$

---

### Post by chex_m8 on 2009-01-11
ok, so no error message. it worked right? post the ls -l of the file.

---

### Post by smartsmokey on 2009-01-11
> **chex_m8 said:**
> ok, so no error message. it worked right? post the ls -l of the file.

wow, did the ls -l and the file is now in GREEN BLOCK

drwxrwxrwx  2 smartsmokey smartsmokey     4096 2009-01-11 13:44 Microsoft.Windows.XP.Professional.Corporate.SP2.Integrated.September.2007-ETH0
it's like still not letting me do anything with the file

---

### Post by chex_m8 on 2009-01-11
it let you change the permissions on it. 
it still isnt letting you burn the iso?
you should be able to do what you want with it because you have full permissions now.
if you want you could try logging in as root and burning the iso.

---

### Post by smartsmokey on 2009-01-11
> **chex_m8 said:**
> it let you change the permissions on it. 
it still isnt letting you burn the iso?
you should be able to do what you want with it because you have full permissions now.
if you want you could try logging in as root and burning the iso.
no i have a folder titled e-xpc2sp2k7.r08, and inside that there's the iso file. BUT, I can NOT do anything with the ISO file, it will not let me drag/cop onto the desktop, and when i use the disc burning application it only goes as far as the e-xpc2sp2k7.r08 folder, and will not let me see inside of it

---

### Post by chex_m8 on 2009-01-11
when your in the nero program its probably not recognising the iso because of the strange .2007-ETH0 extension. iv'e never used ubuntu to burn iso's so i can't help with that but this appears to not be a permissions issue.
you might try changing the extension to .iso

---

### Post by smartsmokey on 2009-01-11
> **chex_m8 said:**
> when your in the nero program its probably not recognising the iso because of the strange .r08 extension. iv'e never used ubuntu to burn iso's so i can't help with that but this appears to not be a permissions issue.
you might try changing the extension to .iso

okay. Thanks a lot for all the halp bro. I'll figure it out eventually. To be honest I should just stick with Ubuntu as the only OS on my computer. I don't know.

---

