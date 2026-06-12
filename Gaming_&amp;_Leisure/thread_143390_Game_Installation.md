---
title: "Game Installation"
date: 2006-03-12
forum: Gaming &amp; Leisure
---

### Post by wolf_3d on 2006-03-12
I'm trying to install Enemy Territory. The file et-linux-2.60.x86.run is some sort of shell script. But i have no idea how to run it. I have looked on the net on how to run shell scripts but don't seem to be getting very far.

---

### Post by geo926 on 2006-03-12
Open a Terminal window Accessories->Terminal, then type ```
su root
``` It should prompt you for the root password, enter it then type ```
sh et-linux-2.60.x86.run
``` It should bring up the installer after that!:KS

---

### Post by wolf_3d on 2006-03-12
thx for the reply. However there appears to be another problem. I type in the terminal what you said: su root and then it asks for a password (which is the same one i entered at the login screen yeah?) but when i start typing nothing appears on the screen.:???:

---

### Post by installer on 2006-03-12
[QUOTE=wolf_3d]thx for the reply. However there appears to be another problem. I type in the terminal what you said: su root and then it asks for a password (which is the same one i entered at the login screen yeah?) but when i start typing nothing appears on the screen.:???:[/QUOTE]

Yes that's normal :)

---

### Post by wolf_3d on 2006-03-12
Well i get this error message when i press return. The message says;

[CENTER]su: Authentication failure
Sorry.[/CENTER]

but it IS the correct password i used to login. The password dosen't even appear as im typing it. There's just this black cursor that just sits there. :(

---

### Post by Horndog on 2006-03-12
[QUOTE=]su: Authentication failure
Sorry.[/QUOTE]

That's because there is no root account set up which is default for Ubuntu. Use:```
 sudo
```

---

### Post by wolf_3d on 2006-03-12
ok i get this message and then i type: sh et-linux-2.60.x86.run and it says there is no such file or directory. But the file is sitting on my desktop!

john@ubuntu:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
john@ubuntu:~$ sh et-linux-2.60.x86.run
sh: et-linux-2.60.x86.run: No such file or directory
john@ubuntu:~$

---

### Post by Horndog on 2006-03-12
Try this:
```

sudo ./et-linux-2.60.x86.run
```

Make sure that script has execution privileges.

---

### Post by wolf_3d on 2006-03-12
nope....unfortunately getting this message:

john@ubuntu:~$ sudo ./et-linux-2.60.x86.run
Password:
sudo: ./et-linux-2.60.x86.run: command not found
john@ubuntu:~$

---

### Post by Horndog on 2006-03-12
[QUOTE=wolf_3d]nope....unfortunately getting this message:

john@ubuntu:~$ sudo ./et-linux-2.60.x86.run
Password:
sudo: ./et-linux-2.60.x86.run: command not found
john@ubuntu:~$[/QUOTE]

What directory is the file in? The terminal has to be in the directory of the file.
If the file is on your desktop then:
```
john@ubuntu:~$ cd Desktop
```
Then:
```
john@ubuntu:~/Desktop$ sudo ./et-linux-2.60.x86.run
```

---

### Post by akiro.yamamoto on 2006-03-12
Go to the directory that you downloaded the file to then:
```

chmod a+x *.run
sudo ./et-linux-2.60.x86.run

```

I hope that helps.. ;)

---

### Post by threethirty on 2006-03-13
The only thing that I've ever done with .run files is double click on it.  It is supposed to all of that itself.  It's like a .exe in Windows

---

### Post by wolf_3d on 2006-03-13
[QUOTE=threethirty]The only thing that I've ever done with .run files is double click on it.  It is supposed to all of that itself.  It's like a .exe in Windows[/QUOTE]

Yeah that was the first thing i did - i just assumed it would run - like windows. Anyway, when i double click on the file Gedit runs - starts trying to read the file then after a 1 minute pause returns an error message saying that i need to assign an appropriate program to deal with shell script. Since i'm a complete noob to linux i'm not sure which program to assign it to.

[QUOTE=Horndog]What directory is the file in? The terminal has to be in the directory of the file.
If the file is on your desktop then:
Code:

```
john@ubuntu:~$ cd Desktop
```

Then:
Code:

```
john@ubuntu:~/Desktop$ sudo ./et-linux-2.60.x86.run
```[/QUOTE]

OK thank you i will try once i get home and report back.

---

### Post by wolf_3d on 2006-03-13
ok thank you very much akiro.yamamoto for that. The command worked perfectly and installation succeeded. Now there is a new problem. I need to install the proper NVIDIA drivers for my graphics card - because i can't run the game without the OpenGL and the generic drivers are useless. So i downloaded the drivers from the website and i need to install them. I have successfuly managed to get to the root (why didn't this work before? well i didn't set a password in the Users Group) and i get this error message: 

 [CENTER] ERROR: Unable to find the system utility `ld`; please make sure you have the
         package 'binutils' installed.  If you do have binutils installed,
         then please check that `ld` is in your PATH.

                                       OK[/CENTER]

what is this?

---

