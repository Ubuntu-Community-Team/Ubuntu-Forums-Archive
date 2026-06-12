---
title: "Folder permissions problems"
date: 2006-01-01
forum: General Help
---

### Post by galvatron1983 on 2006-01-01
Im trying to install a speedtouch 330 USB modem and Im following a very useful how-to, but right now Im stumped on a problem...

I have to copy a simple text file to the etc/ppp/ folder in the file system, but when I try to do so I get an error message thats says: 

"You do not have permissions to write to this folder"

This suggested to me that you need to access the root account to write to it, and to do this Ubuntu would normally ask you for a password to authenticate as a root user am I right? I never get asked for a password though, and all I get is the error message. 

To see if I could change the owner of the folder I looked in the folder Properties on the Permissions tab and it was indeed owned by root. All of the tick boxes that would allow to make changes to the permissions are ghosted and I cant change them. 

Can anyone help???  :confused:

---

### Post by Omnios on 2006-01-01
think it can be done in terminal 

 sudo gedit /...../...../...../New_Filename and save. 

 Sudo gedit open the gedit text editor as root.

 YOu can do the same to mod a text file

---

### Post by iand675@gmail.com on 2006-01-01
I'm not sure if others would recommend doing this or not, but you can do an even higher level permission by doing
```
sudo passwd root
```
then choosing a root password. This also enable you to log in as root. So now do this:
```
sudo -s
```
Now you are using the shell as root. See if this works.

---

### Post by qferret on 2006-01-01
sudo is there for a reason. That way you have to specify EACH and every command you want to run as root. If you inadvertantly run some programs as root (GUI based apps in particular. LimeWire for example) Your permissions can get hosed pretty good. I've screwed up the ownership on .Xauthority a time or 2 before I finally learned my lesson.

---

### Post by Omnios on 2006-01-01
There is also a open as root script that allows for graphical managment in root so you can open a text file or folder as root.

[http://ubuntuforums.org/showthread.php?t=75610&highlight=open+root]("http://ubuntuforums.org/showthread.php?t=75610&highlight=open+root")

[http://www.ubuntuguide.org/#openfilesasrootviarightclick]("http://www.ubuntuguide.org/#openfilesasrootviarightclick")

---

### Post by galvatron1983 on 2006-01-01
I can now log in as root through the terminal, but I dont know how to copy the file I need to be in root-owned "ppp" folder using the terminal. 

The file that needs to copied is in my Home folder. The ppp folder is at /etc/ppp

---

### Post by Lord Illidan on 2006-01-01
Simple..
In your home directory type

```
sudo cp "name of file" /etc/ppp/ 
```

remove quotes and insert your own file. Remember that Linux is case sensitive. Good luck!;)

---

### Post by galvatron1983 on 2006-01-01
Im in the terminal logged in as root but I cannot access the Home folder in the terminal. Im tryping in

---

### Post by galvatron1983 on 2006-01-01
Im in the terminal logged in as root but I cannot access the Home folder in the terminal. At the @ubuntu:~$ prompt im entering 

```
cd Home
```

Is that correct??

Thanks for your help guys!

Oops sorry for the double post too!

---

### Post by Jammy_Stuff on 2006-01-01
```
cd /home/*your username*
```

should do it.

---

