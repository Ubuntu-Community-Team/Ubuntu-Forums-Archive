---
title: "How  do you launch a program as root user under unity?"
date: 2012-06-07
forum: Desktop Environments
---

### Post by Randy Schilling on 2012-06-07
I would like to open certain programs, such as gedit and the command-line interface,
from the unity launcher both as regular user and as root (administrator) user.  
I had this set up under Ubuntu 11.04 using a program called Main 
(or something???) but I can't seem to find this program under 12.04.
Is there an easy way to set this up?
Thanks,  so fortunate to have this help forum.  Regards - Randy

---

### Post by wilee-nilee on 2012-06-07
Here is the forums policy on this.

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by davetv on 2012-06-08
> **wilee-nilee said:**
> Here is the forums policy on this.

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)


Hi Wilee-nilee. I think the OP is asking for a unity equivalent of gksu or kdesu

---

### Post by wilee-nilee on 2012-06-08
> **davetv said:**
> Hi Wilee-nilee. I think the OP is asking for a unity equivalent of gksu or kdesu

Partially, maybe read closer.

---

### Post by mcduck on 2012-06-08
> **Randy Schilling said:**
> I would like to open certain programs, such as gedit and the command-line interface,
from the unity launcher both as regular user and as root (administrator) user.  
I had this set up under Ubuntu 11.04 using a program called Main 
(or something???) but I can't seem to find this program under 12.04.
Is there an easy way to set this up?
Thanks,  so fortunate to have this help forum.  Regards - Randy

For any graphical applications, just add "gksudo" in front of the command you'd normally use to launch the application.

(If you want to create new launchers for this purpose, install "Alacarte", it's the tool Gnome desktop uses for editing menu items. Once installed, it will appear with the name "Main Menu" in your menus (or in Unity's Dash). 

...and for terminal, running "sudo -i" will start a root session. "exit" will return you back to normal user again.

For more detailed information, you should read this document: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Frogs Hair on 2012-06-08
Bleach bit is the only application I have installed that comes with a root and regular user option . I have created a Nautilus Root launcher with main menu after installing Alacarte and adding the new item  . Now I just get a password prompt when using the Icon instead of using the terminal.

---

### Post by Randy Schilling on 2012-06-08
What I was looking for was the "Main Menu".  
I could not recall that it is installed as "Alacarte".
Thanks Mcduck.

The problem I have with the use of gksu to launch a 
graphical application such as nautilus from a terminal 
is that it locks your terminal to that app, leaving you
with two windows on your desktop to run a single app.


I was not aware of sudo -i as a way to access the root prompt #.
I use to do this with "sudo gnome-terminal" or "gksu gnome-terminal".
I like "sudo -i" because it does not add another terminal to your desktop.
I'm surprised  that it does not  ask for a password.

I don't understand the difference between sudo and gksu. gksu seems
to be used with graphical apps and sudo is apparently not restricted.
In my experience they're completely interchangeable.

Thanks as always for your help.

---

### Post by mcduck on 2012-06-08
> **Randy Schilling said:**
> What I was looking for was the "Main Menu".  
I could not recall that it is installed as "Alacarte".
Thanks Mcduck.

The problem I have with the use of gksu to launch a 
graphical application such as nautilus from a terminal 
is that it locks your terminal to that app, leaving you
with two windows on your desktop to run a single app.


I was not aware of sudo -i as a way to access the root prompt #.
I use to do this with "sudo gnome-terminal" or "gksu gnome-terminal".
I like "sudo -i" because it does not add another terminal to your desktop.
I'm surprised  that it does not  ask for a password.

I don't understand the difference between sudo and gksu. gksu seems
to be used with graphical apps and sudo is apparently not restricted.
In my experience they're completely interchangeable.

Thanks as always for your help.

to prevent an GUI app from locking a temrinal when launched, you simply need to tell the shell to launch it in the background. For example:
```
gksudo gedit &
```

Some programs might still output errors and other messages to the temrinal, if you want to prevent that you can use the "nohup" command:
```
nohup gksudo gedit &
```
This will redirect the output to a textfile in your home directory, and also allows you to close the terminal without the program getting closed automatically with it.

What comes to "sudo -i" asking for password, it does, but duso has a built-in timeout mechanism so if you've used sudo recently, it's not going to ask you for password again until certain time has elapsed.

---

### Post by MG&amp;TL on 2012-06-08
Following on from mcduck,

If you want closing the terminal to have no effect on the app, follow the command with "disown"-example:

```
gedit &
#closing the terminal now will kill the app
```

```
gedit &
disown
#closing the terminal now has no effect
```

---

### Post by IWantFroyo on 2012-06-08
> **MG&TL said:**
> Following on from mcduck,
 
If you want closing the terminal to have no effect on the app, follow the command with "disown"-example:
 
```
gedit &
#closing the terminal now will kill the app
```
 
```
gedit &
disown
#closing the terminal now has no effect
```
 
Odd. I can start a program with the "gedit &" method, and then just close the terminal.

---

### Post by MG&amp;TL on 2012-06-08
> **IWantFroyo said:**
> Odd. I can start a program with the "gedit &" method, and then just close the terminal.

Okay, that's weird. I don't personally have gedit installed, maybe it forks itself?

---

### Post by IWantFroyo on 2012-06-08
> **MG&TL said:**
> Okay, that's weird. I don't personally have gedit installed, maybe it forks itself?
 
I'm not just talking about gedit. I can open any program, and as long as I add the "&", it becomes independent. :|

---

### Post by MG&amp;TL on 2012-06-08
> **IWantFroyo said:**
> I'm not just talking about gedit. I can open any program, and as long as I add the "&", it becomes independent. :|

The only other thing I can think of is what shell and terminal emulator do you use? I've got bash and lxterminal.

---

### Post by Randy Schilling on 2012-06-08
Yes,  & to "disconnect" program from terminal.
Now I know what it means to run a program  in the "background".
I too could not see that that "disown" made any difference.

Thanks

---

