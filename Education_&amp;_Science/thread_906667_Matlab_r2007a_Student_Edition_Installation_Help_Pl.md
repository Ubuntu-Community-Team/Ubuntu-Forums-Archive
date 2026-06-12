---
title: "Matlab r2007a Student Edition Installation Help Please"
date: 2008-08-31
forum: Education &amp; Science
---

### Post by Xephyrind on 2008-08-31
Hello, I have spent reading through forums and trying to install matlab on my linux distribution-debian AMD64 machine. After I have mounted my cdrom with the exec option added in my fstab, I run the following command:
```
/cdrom/install_unix.sh
```

 I get the following error message:
```
    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /media/cdrom0/unix/update/install/main.sh: line 86: /media/cdrom0/unix/update/bin/glnxa64/xsetup: No such file or directory

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

```

Somehow the student version doesn't have the AMD64 installation file?!?! **What can I do to get Matlab installed?** Please help me in detail such as the exact bash command line I should type in since I am quite noobie at BASH (still trying to learn). Any help is appreciated. Thank you!~ (For the record, I've posted the exact same post in the Education and Science Forum, but no one answered after 3 hours. Therefore, I've decided to try posting here)

---

### Post by jpkotta on 2008-08-31
Is the file actually not there?  Are you running the installer as root?

---

### Post by Xephyrind on 2008-08-31
> **jpkotta said:**
> Is the file actually not there?  Are you running the installer as root?

Thank you jpkotta for being the only person for replying to me. I have finally figured out how to deal with this about three hours ago. Really appreciate your concern :)~

---

### Post by Sef on 2008-08-31
Could you post your solution?  Thank you.

Moved to Education and Science.

---

### Post by Xephyrind on 2008-09-01
> **Sef said:**
> Could you post your solution?  Thank you.

Moved to Education and Science.

Certainly, Boss~ :) Been working on one since last night :) almost finished. Checking for potential confusion right now. After that I am going to post it up :D

---

### Post by Xephyrind on 2008-09-01
After seventy-two hours of grueling trying to figure out how to install Matlab on my AMD64 (64 bit architecture) debian system as a linux n00bie, I hope this simple guide will save countless hours for others. Below are the solutions for Debian and Ubuntu. Again, this is the noobie way of doing it probably, but it has worked for me. If you have better solution please share it with everyone. I'd like to know as well. As a common and good academic practice, The following people and references are cited and thanked:
Raviolios and andrew.hoell on our beloved Ubuntu Forum. Their posts can be found in the following internet address to another post in the forum.
[http://ubuntuforums.org/showthread.php?t=717976&highlight=matlab](http://ubuntuforums.org/showthread.php?t=717976&highlight=matlab)
**SOLUTION:**
*Debian:*
1. Log in as root in terminal by typing:
```
su -
```

2. input in your root password.

3. Enter the top directory by issuing the following command
```
cd ..
```

4.pop in your matlab CD into your cd/dvd rom drive. I believe most systems auto mounts cd/dvd rom drive upon the detection of your matlab cd in the drive. Issue the following command in the terminal:
```
ls
```

The reason we did all that is that it seems on the forums, some systems mounts the optical/cd/dvd drive as a folder called cdrom and some others as a folder called dvdrom. Since I am a noob, my best bet is simply just see which one your system called as your optical drive is mounted automatically. You should see a lot of folders with ONLY one folder's name related to your cd/dvd rom drive.

5. After discovering the name of your optical drive in the system, we will go ahead and edit a line in your fstab file.
[i]
The fstab file is in your /etc directory. If you choose to use GUI to access the fstab file, you will need to have root power in GUI to edit that file, or else the system will not let you save. I vaguely rememeber that it has to do with some nautilus command with su or sudo, but I don't remember the detail.
[/i]
I used VIm text editor in CLI to do the job.
```
vim /etc/fstab
```

6. look for a line that looks something like but doesn't have to be exactly like this: (if your optical given name is cdrom then it should say something like /dev/cdrom /cdrom or something like that. In short, don't bother changing anything in there except for in the upcoming step 7 which is adding an 'exec' at the right location).

** /dev/dvd /dvd iso9660 noauto,ro,user 0 0 **

7. add an 'exec' right after the mumbo jumbo noauto,ro,user like the following example:
**/dev/dvd /dvd iso9660 noauto,ro,user*,exec* 0 0**

8. save the file. In VIm, simply press [shift]+ZZ

9. Since student version of matlab does not come with 64bit version of the file system, we'll have to live with the 32bit version. To do that, we need to first install the 32bit version of some library by issuing the following code in the terminal:
```

```

10. Issue the following command in the terminal:
```
apt-get install ia32-libs
```
Select Yes by inputting y with [carriage-return], then
pop in your debian installation disk.

11. now just to be careful. Let's remount our optical drive. Since my computer calls my Asus cd/dvd/rw 'cdrom', I guess that's the name I'll have to live by and refer to my optical drive, 'cdrom'. If yours is referred to as something else, substitute in the corresponding name in the right locations in the following terminal command:
```
umount /cdrom
```
so if yours is called dvd then issue in terminal
```
umount /dvd
```

12.mount optical drive by issuing following command in terminal
```
mount -t iso9660 /dev/cdrom /cdrom
```

13. decide you place you want to install matlab in. I put it in /usr/local/matlab74_sv in terminal:
```
mkdir /usr/local/matlab74_sv
```

14. now finally to install, in terminal:
```
/cdrom/install_unix.sh -glnx86 -t
```

15.Now just follow the directions on screen and make sure the installed path is directed to matlab74_sv, then you are pretty much done.

16. Register/activate your product or else your matlab will NOT run and WILL DEFINITELY complain about your some JRE thing. Direction to activate is here:

[http://www.mathworks.com/support/sol...ution=1-3YZBZ6](http://www.mathworks.com/support/sol...ution=1-3YZBZ6)

17.If after you registered/activated your matlab student version and it doesn't work, please let me know and kindly give me the solution. This is because I have not submitted my schedule to mathworks, yet; therefore, I do not know anything about the activation process.

18. Constructive criticism is greatly appreciated as your contribution in criticism, suggestions, and questions about this article will nourish me as a scholar and as an individual. Finally hope this guide will at least somewhat help people :)!~

---

### Post by jonos on 2008-10-28
Hi Xephyrind,

Thanks for your howto. So that you know, there are some steps afterwards to finish the install and activation process. Indeed, the JRE problem brought by Matlab is not a licence error. You have to link to an appropriate 32 bit jre on your system.

What worked for me was to install a 32 bit jre with synaptic. Then to export the java path in the Matlab bash.

```
sudo vim $MATLABROOT/bin/matlab 
```

Then add the following line at the beginning of the bash (just after the first long commented part) by replacing of course the path by the one linking to your 32 bit jre.

```
export MATLAB_JAVA=/usr/lib/jvm/ia32-java-6-sun/jre 
```

You must also link your 32-bit java for your machine to use it. 

```
cd $MATLABROOT/sys/java/jre/ 
sudo ln -s glnx86/ glnxa64 
```

next check if the variable is being correctly used by matlab.

```
matlab -n 
```

If this shows you the line that you've added then you are all set. You can start using matlab.

```
matlab -glnx86 
```

you should get to the activation process and then to your matlab install.

jon

---

