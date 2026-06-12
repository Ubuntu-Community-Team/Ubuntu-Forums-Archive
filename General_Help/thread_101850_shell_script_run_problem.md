---
title: "shell script run problem"
date: 2005-12-10
forum: General Help
---

### Post by etola on 2005-12-10
Hi,

For some reason I am not able to run the shell scripts anymore. When I double click on them, they are opened in a text editor. Also, I cannot change the attributes of the shell scripts. They are rw-rw-rw- form and when I chmod them to 777 nothing chages ( with root user ).

Any idea what I am doing wrong ? 

Did I disabled the execution of shell scripts somehow ? (this is fairly impossible since I installed ubuntu just last week and I didn't played with it too much)

thanks,,,

etola

---

### Post by etola on 2005-12-10
Ok I find the reason. 

It seems that I was trying to run the scripts from a vfat partition. And it didn't worked from there (i don't know why, if anybody knows please let me know ) 

bye


[QUOTE=etola]Hi,

For some reason I am not able to run the shell scripts anymore. When I double click on them, they are opened in a text editor. Also, I cannot change the attributes of the shell scripts. They are rw-rw-rw- form and when I chmod them to 777 nothing chages ( with root user ).

Any idea what I am doing wrong ? 

Did I disabled the execution of shell scripts somehow ? (this is fairly impossible since I installed ubuntu just last week and I didn't played with it too much)

thanks,,,

etola[/QUOTE]

---

### Post by RHTopics on 2005-12-10
etola,

I have experienced this same situation when I tried to execute a shell script from a USB pen drive with the Live CD version.  The USB pen drive is formatted as vfat and will not execute the script.  Yet using Knoppix 4.0, I am able to execute shell scripts from the same USB pen drive.

I am also wondering what needs to be changed to allow execution of a shell script.

---

### Post by professor_chaos on 2005-12-10
Interesting. I can execute a script on a usb drive as vfat32 just fine with breezy 5.10

Can you source the file? i.e. "source name_of_script.sh"

---

### Post by RHTopics on 2005-12-10
Using the "source ./script_file.sh" command allowed the bash script to be executed from the USB drive, while just entering "./script_file.sh" gave back the following message:

```
-bash: /media/LEXAR/script_file.sh: /bin/bash: bad interpreter: Permission denied
```

The "source" command runs the script as part of the current process.  Referencing "A Practical Guide to Linux" by Mark G. Sobell, the consequences of using the "source" command may have undesirable side effects such as changes in the values of shell variables you rely on.

Using the "source" command generated messages on console tty1 like just being logged in and the present working directory changed to the home directory.  Running the "source" command while in a Gnome Terminal, caused the terminal session to end.  This is on an iMac running the Live CD version of Breezy Badger.

---

### Post by etola on 2005-12-11
[QUOTE=professor_chaos]Interesting. I can execute a script on a usb drive as vfat32 just fine with breezy 5.10

Can you source the file? i.e. "source name_of_script.sh"[/QUOTE]


I tried it for the install.sh script of automatix and easy ubuntu. 

It is not dependent on the script i think

---

### Post by RHTopics on 2005-12-11
etola,


I could not be certain from your reply whether the "source" command allowed you to successfully execute your script.

---

### Post by etola on 2005-12-11
[QUOTE=RHTopics]etola,


I could not be certain from your reply whether the "source" command allowed you to successfully execute your script.[/QUOTE]


sorry, my mistake.  I thought you are asking me the name of the script. I will try it as soon as I go back to home and tell you the result.

---

### Post by schilcha on 2005-12-11
[QUOTE=etola]It seems that I was trying to run the scripts from a vfat partition. And it didn't worked from there (i don't know why, if anybody knows please let me know ) [/QUOTE]

This might be caused by the mount-options for the vfat partition. I took a glance at the mount-man-page: The exec / noexec options determine whether you're allowed to execute binaries or not. It's allowed by default *unless* the user / users options are specified. In this case, you need to explicitly allow execution.

I don't have a vfat partition, so I couldn't test whether this also applies to scripts (non-binary programs). Also, I don't know how ubuntu integrates a vfat partition into the systems (i.e. which mount-options). 

Try to have a look at /etc/fstab and check with man mount.

Good Luck!

---

### Post by etola on 2005-12-11
[QUOTE=professor_chaos]
Interesting. I can execute a script on a usb drive as vfat32 just fine with breezy 5.10

Can you source the file? i.e. "source name_of_script.sh"[/QUOTE]

[QUOTE=schilcha]
This might be caused by the mount-options for the vfat partition. I took a glance at the mount-man-page: The exec / noexec options determine whether you're allowed to execute binaries or not. It's allowed by default *unless* the user / users options are specified. In this case, you need to explicitly allow execution.
[/QUOTE]

Hi, 

'source' ing the file didn't worked but enabling the exec/ did the trick! after that I can execute scripts. 

I also tried sourcing again after exec/ is enabled and it worked as well.

thank you guys..

---

### Post by RHTopics on 2005-12-11
schilcha,

Your diagnoses was correct for me as well.  Below is the mount for a Lexar USB Pen drive on a iMac running the Live CD.

```
/dev/sda1 on /media/LEXAR type vfat (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)
```

---

