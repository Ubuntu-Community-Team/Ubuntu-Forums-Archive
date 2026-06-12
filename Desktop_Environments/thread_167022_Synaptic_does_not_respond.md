---
title: "Synaptic does not respond"
date: 2006-04-27
forum: Desktop Environments
---

### Post by simbiwa on 2006-04-27
After installing Ubuntu 5.10 , my resolution was stuck to 640x480 , I read a lots of posts and got the answer to make changes to   /etc/X11/xorg.conf, which i tried using this comand :sudo gedit /etc/X11/xorg.conf   it asked for a password, i gave my user password , nothing happened.

I used the command su , it asked for a password , i gave my root password and then the command :sudo gedit /etc/X11/xorg.conf   , an error poped up in the terminal but gedit started with the above file. I made the changes by adding the HorizSync value and the VertRefresh value , saved the file and rebooted . The resolution problem was solved.

As Totem could not play any vedio files as plugins were missing , i tried EasyUbuntu but command "sudo " does not work, synaptic does not respond 

If I use su and then type synaptic , it shows error but starts synaptic but does not upgrade](*,)

---

### Post by jazzmuzik on 2006-04-27
If your screen rez was in 640 x 480 after install it may mean that Ubuntu couldn't properly detect your video card or monitor and it uses 640x480 as a safe bet.

So you tried "sudo synaptic" or "gksudo synaptic" ?

---

### Post by robotgeek on 2006-04-27
I think you have enabled root account. Read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) on how to disable (scroll to the bottom)

---

### Post by simbiwa on 2006-04-28
[QUOTE=jazzmuzik]If your screen rez was in 640 x 480 after install it may mean that Ubuntu couldn't properly detect your video card or monitor and it uses 640x480 as a safe bet.

So you tried "sudo synaptic" or "gksudo synaptic" ?[/QUOTE]
I have tried both "gksudo synaptic" as well as "sudo synaptic" but nothing happens . when I try "su" then give my root password then the command "sudo synaptic" , then synaptic wakes up and starts running.

It does not work in the menu , when I try it asks for a password but then nothing happens.

---

### Post by jazzmuzik on 2006-04-28
I may have misunderstood your orginal message. I thought you were in gui mode at 640x480, but I think you meant to say you were in text mode. If that's the case your graphical user interface installation didn't go correctly.

---

### Post by simbiwa on 2006-04-28
[QUOTE=jazzmuzik]I may have misunderstood your orginal message. I thought you were in gui mode at 640x480, but I think you meant to say you were in text mode. If that's the case your graphical user interface installation didn't go correctly.[/QUOTE]
You have not misunderstand, I am in GUI, that problem of resolution is solved.
The problem is that in GUI I can not get Synaptic to work.

I use the terminal , and "sudo" does not work ..like if I type "sudo gedit /etc/X11/xorg.conf" , it asks for a password , I type my user password and then nothing happens.

If i type "su" and give my root password then the command it works.

in GUI , synaptic does not start unless I use the terminal and use the "SU" comand and root password.

Is there any way I can just click the Synaptic from the menu in GUI to use it ?

---

### Post by jazzmuzik on 2006-04-28
Synaptic is in the menu system at System, Administration, Synaptic Package Manager.

If you are using a root password, you must have changed the default Ubuntu setup and that may be why the sudo method is failing. Is this a network installation? I've never done one but perhaps it utilizes a real root user as opposed to using a regular user with sudo privelidges.

---

### Post by simbiwa on 2006-04-28
[QUOTE=jazzmuzik]Synaptic is in the menu system at System, Administration, Synaptic Package Manager.

If you are using a root password, you must have changed the default Ubuntu setup and that may be why the sudo method is failing. Is this a network installation? I've never done one but perhaps it utilizes a real root user as opposed to using a regular user with sudo privelidges.[/QUOTE]
No , It is not a network instalation, but I am connected to Internet through lan on a network by my service provider.

I have tried starting Synaptic from  System, Administration, Synaptic Package Manager , it asks for a password , I tried my user password , it did not work, then i tried my root pasword but that too does not work.

Is there any way I can get back to using "sudo" method ?

i have ried this [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)  but still the problem exists.
I can not start Synaptic directly from GUI , I have to use the Terminal and a root password using "SU" command.

---

### Post by simbiwa on 2006-04-28
[QUOTE=jazzmuzik]Synaptic is in the menu system at System, Administration, Synaptic Package Manager.

If you are using a root password, you must have changed the default Ubuntu setup and that may be why the sudo method is failing. Is this a network installation? I've never done one but perhaps it utilizes a real root user as opposed to using a regular user with sudo privelidges.[/QUOTE]
I have tried using Synaptic from System,> Administration,> Synaptic Package Manager. It asks for a password, I type my user password..nothing happens!.
I try again using root password ....nothing happens.

No, It is not a network instalation, but I am conected to internet by lan through my cable service provider.

Is there anyway I can get back to using the "sudo" method as i have to use "su" and a root pasword for all the "sudo" comands. I even have to use "su" for starting Synaptic by using the terminal .

---

### Post by jazzmuzik on 2006-04-28
I think you are mistyping your password. Linux is case sensitive, so a password like BugsBunny is completely different than bugsbunny.

---

### Post by simbiwa on 2006-04-28
I am sure I am typing correct password as I have tried it many times .

Anyway thanks a lot Jazzmuzik, I am sorry if I have not been all that clear in presenting my problem.

There are 2 problems that I am facing at the moment.

Synaptic not starting in GUI and comand "sudo " not having any effect in the terminal.

---

### Post by Zo|oZ on 2006-05-05
[QUOTE=simbiwa]I am sure I am typing correct password as I have tried it many times .

Anyway thanks a lot Jazzmuzik, I am sorry if I have not been all that clear in presenting my problem.

There are 2 problems that I am facing at the moment.

Synaptic not starting in GUI and comand "sudo " not having any effect in the terminal.[/QUOTE]


Same here!

I plug in my password and nothing happens. When I go to run the application again I get this dialog:

"failed to run /usr/bin/gnome-app-install as user root: Child terminated with 1 status"

I'm going to start another thread with this problem

---

### Post by Zo|oZ on 2006-05-05
[QUOTE=simbiwa]After installing Ubuntu 5.10 , my resolution was stuck to 640x480 , I read a lots of posts and got the answer to make changes to   /etc/X11/xorg.conf, which i tried using this comand :sudo gedit /etc/X11/xorg.conf   it asked for a password, i gave my user password , nothing happened.

I used the command su , it asked for a password , i gave my root password and then the command :sudo gedit /etc/X11/xorg.conf   , an error poped up in the terminal but gedit started with the above file. I made the changes by adding the HorizSync value and the VertRefresh value , saved the file and rebooted . The resolution problem was solved.

As Totem could not play any vedio files as plugins were missing , i tried EasyUbuntu but command "sudo " does not work, synaptic does not respond 

If I use su and then type synaptic , it shows error but starts synaptic but does not upgrade](*,)[/QUOTE]


you must add your own user name to the sudoers file /etc/sudoers. 

Do this:

1. open terminal , type su. When asked type the root password.
2. type visudo
3. scroll to the bottom of the file. There is the line root ALL=(ALL) ALL.
4. Add beneath that line your user name and ALL=(ALL) ALL
5. Save ctrl-o (oh, not zero)
6. Exit ctrl-x

---

### Post by simbiwa on 2006-05-06
Thanks a lot

---

