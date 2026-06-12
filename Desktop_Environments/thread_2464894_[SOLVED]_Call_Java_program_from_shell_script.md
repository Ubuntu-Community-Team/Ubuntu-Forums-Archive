---
title: "[SOLVED] Call Java program from shell script"
date: 2021-07-15
forum: Desktop Environments
---

### Post by gechert on 2021-07-15
This seems simple but I can't get it to work. I am trying to launch a java program with a shell script. The command "java -jar program.jar" works from a terminal.  But the script file below fails ("command not found").  The shell script is marked as executable.  The screen shot is my system details: 20.04 LTS Gnome 3.36.8 

```


#!/bin/sh

# shell to start Java program


exec java -jar /home/gary/.local/share/applications/program.jar


```

---

### Post by monkeybrain20122 on 2021-07-15
You don't need the 'exec'. If you put the script in your PATH (e.g ~/.local/bin or ~/bin) then you can run  by just typing its name.

Also program.jar should not be in ~/.local/share/applications, the directory is for launchers (i.e .desktop files)

---

### Post by gechert on 2021-07-15
I want the script on my desktop so I can run it from there.  I have another script there that launches a (non-java) program.  Is that possible?

Thanks for the guidance on the file location.  I have been confused for years on where the best place is for applications.  Is there a clear explanation of that somewhere?

---

### Post by monkeybrain20122 on 2021-07-15
If you want to launch it from desktop you need a .desktop file to be placed in ~/.local/share/applications. then it will show up in your dash or menu depending on your DE, from there you can pin or drag and drop it to the desktop (but I don't see the point of littering your desktop with launchers if you use a DE with a dash, which serves the same purpose without the clutter) , though gnome shell might have removed the function. You have two ways to do it:

either 
1. create a .desktop file to run your jar file directly

or

2. create a .desktop file whose Exec= line points to an executable shell script which runs the .jar file.

usually you do 2) because you want the shell script to set some environmental variables specific for your application, if your script just runs the application there is no need to go through the intermediary of a shell script.

Your .jar file (or shell script if go the route 2)  should be placed in a directory for executables, like ~/.local/bin or ~/bin so it is in your PATH (where the system finds executables) 

In your case the script just runs the jar so there is no point to have it, we shall go route 1)

 A minimalist .desktop file would look like

```

[Desktop Entry]
Name=name of your program
Terminal=false
Type=Application
Categories=
Exec=java -jar /path/to/jar/file
Icon=/path/to/a/logo/for/your/program
```

Make this executable and place it in ~/.local/share/applications

---

### Post by gechert on 2021-07-16
OK I got this to work, after a good deal of work.  I appreciate the help.  It seems that placing the .desktop file in /.local/share/applications adds the program to the Unity launcher, but not to the desktop.  In order to get the launcher on the desktop, I found this: [https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux).

Just venting but this seems far more complicated that it should be.  Or than it is in Windows, or Linux Mint, for example.  And I still don't understand why a shell script to launch a different (non-java) program works from the desktop but the same approach did not work on java.

---

### Post by monkeybrain20122 on 2021-07-16
> **gechert said:**
> OK I got this to work, after a good deal of work.  I appreciate the help.  It seems that placing the .desktop file in /.local/share/applications adds the program to the Unity launcher, but not to the desktop.  In order to get the launcher on the desktop, I found this: [https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux).

Just venting but this seems far more complicated that it should be.  Or than it is in Windows, or Linux Mint, for example.  And I still don't understand why a shell script to launch a different (non-java) program works from the desktop but the same approach did not work on java.

If you are using unity why do you need it on the desktop? Just press the meta key you have all the app icons displayed in front of you just like icons on the desktop, besides, why would you want to launch a shell script from desktop? It is a bad idea anyway (it should prompt you to run or to display instead of just run by clicking because of security, this can be configured from File if you use anything other than Nautilus since gnome has removed the run option)

---

