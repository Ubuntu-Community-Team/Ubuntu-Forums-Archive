---
title: "Can't login"
date: 2005-05-11
forum: Desktop Environments
---

### Post by Battousai on 2005-05-11
Ok so I just managed to have ubuntu to work , and I already made something really stupid.
I just changed my personal folder to root/ , and now I can't login anymore (your sessions lasted for less than 10 seconds... ) 
I'm the only user, so I don't have other accounts on the computer.

EDIT : It should be in tha Hoary section
Also , keep in mind that I'm still a newbie in linux.

---

### Post by dave9191 on 2005-05-11
Im guessing that you dont have write access privalages onto the /root folder. Hence your sessions are being terminated. Try logging in into a console and getting root privalages and changing the directory back to what it was or giving yourself write access to the root folder. 

Hit Ctrl + Alt + F1 to go to the console (Ctrl + Alt + F7 to go back to GUI). Login in and type 

sudo bash

enter your password. 

you will now have full access to the system to make the changes you need. 

I would recomend changing your folder back to /home/user_name. But to make the root folder writeable you will have to execute 

chmod 777 /root

YOU DO NOT want to leave it like that, but only use this as a fix to get back into the system using GUI to fix it. Once you have it sorted then you want to chmod 744 /root again. Chmod 777 will make the root folder readable, writeable and exectuable to everyone. Not a good idea.

---

### Post by Battousai on 2005-05-11
[QUOTE=dave9191]Im guessing that you dont have write access privalages onto the /root folder. Hence your sessions are being terminated. Try logging in into a console and getting root privalages and changing the directory back to what it was or giving yourself write access to the root folder. 

Hit Ctrl + Alt + F1 to go to the console (Ctrl + Alt + F7 to go back to GUI). Login in and type 

sudo bash

enter your password. 

you will now have full access to the system to make the changes you need. 

I would recomend changing your folder back to /home/user_name. But to make the root folder writeable you will have to execute 

chmod 777 /root

YOU DO NOT want to leave it like that, but only use this as a fix to get back into the system using GUI to fix it. Once you have it sorted then you want to chmod 744 /root again. Chmod 777 will make the root folder readable, writeable and exectuable to everyone. Not a good idea.[/QUOTE]
 It didn't work. Here's what I did:
ctrl-akt-F1
I logged with the problematic account
sudo bash
password
chmod 777 /root
Ctrl-alt-F1
Trying to log with the same account/passwd

I still get the same error message

EDIT : and when I do a ls in command mode , I only have dbootstraps_settings and install-report.template , nothing else!

---

### Post by bigbangbigbigbang on 2005-05-12
[QUOTE=Battousai]Ok so I just managed to have ubuntu to work , and I already made something really stupid.
I just changed my personal folder to root/ , and now I can't login anymore (your sessions lasted for less than 10 seconds... ) 
I'm the only user, so I don't have other accounts on the computer.

EDIT : It should be in tha Hoary section
Also , keep in mind that I'm still a newbie in linux.[/QUOTE]
 OK, if you can login as root, than probably you forgot to create a normal user.
Just login in comman mode, than run adduser, this will create a new user account including home directory
If you had created a normal user account but moved/deleted its home directory, you can recreate it with mkdir /home/username
then chown username:groupname /home/username

cheers

---

### Post by Battousai on 2005-05-12
[QUOTE=bigbangbigbigbang]OK, if you can login as root, than probably you forgot to create a normal user.
Just login in comman mode, than run adduser, this will create a new user account including home directory
If you had created a normal user account but moved/deleted its home directory, you can recreate it with mkdir /home/username
then chown username:groupname /home/username

cheers[/QUOTE]
 Ok , I created a new account and have access to Ubuntu. But I don't have root privileges with that account : I can't access the user management panel or anything else that needs a password.

EDIT : I managed to get access with my admin account! I read some documentation to learn more about sudo ,then I edited my sudoers file so that my emergency account has all rights. Then I could access the user panel and modify the home directory of the other account :D

Thanks for help!!

---

### Post by bigbangbigbigbang on 2005-05-12
[QUOTE=Battousai]Ok , I created a new account and have access to Ubuntu. But I don't have root privileges with that account : I can't access the user management panel or anything else that needs a password.[/QUOTE]

If you have a functional root account with a password you can use su to become root.
Otherwise, if you want to use sudo, check out the /etc/sudoers file. It has to include the following line: 
# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

New users are not members of the admin group by default. You have to add them by typing (as root) adduser your-username admin.

the basic syntax is: adduser username groupname

Add your main user in the same way to the following groups: adm, dialout, cdrom, floppy, audio, dip, video, plugdev, lpadmin, scanner and to any other you may need.
Alternately you also may edit the file /etc/group directly and add your user to the groups this way.
These changes will take effect the next time as you login with this user account.

---

### Post by vsujohn on 2005-05-13
I'm having a similar problem where it won't come up with a splash screen and it will give me an error message saying I can't login this way, it will then send me to a non-gui interface where it asks for my user name and password, and it says that they are incorrect.
I can't do anything with it, and I'm lost  :???:

---

### Post by vsujohn on 2005-05-22
can anyone help me with this?????  ](*,)

---

### Post by dave9191 on 2005-05-22
[QUOTE=vsujohn]can anyone help me with this?????  ](*,)[/QUOTE]

Did you have a fully working ubuntu system before? Could you login using the gui before? Did you edit any config files or install any new packages  / apps? 

Dave

---

### Post by vsujohn on 2005-05-23
yes
all I did was change some settings I needed for ALSA, and a few things for my video card  :-#

---

### Post by dave9191 on 2005-05-24
Well Im guessing that its the graphics card settings that did it. You might have to confgure the xsever again. What are the error messages in the .xsession-errors file in your home dir? Or it might have something to do with whatever settings you changed. 

Dave

---

