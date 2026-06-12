---
title: "i want to know about command copy file ?"
date: 2009-05-26
forum: Desktop Environments
---

### Post by tonjaa on 2009-05-26
if i want to copy file to root of folder how to use command ?
i new for linux ubuntu many time i download themes or some file but i can't in stall file to
folder in true way. now i want to install Ubuntulooks Engine they write tell copy file [COLOR=SandyBrown]libubuntulooks.so and libubuntulooks.la to /usr/lib/gtk-2.0/2.*.*/engines as root (substitute "2.*.*" with your version number) 
[COLOR=Black]that i want to know command [COLOR=SeaGreen]to copy file to folder[/COLOR] . or structure of command .
please tell me by step. thank you.
[/COLOR][/COLOR]

---

### Post by Boondoklife on 2009-05-26
> **tonjaa said:**
> if i want to copy file to root of folder how to use command ?
i new for linux ubuntu many time i download themes or some file but i can't in stall file to
folder in true way. now i want to install Ubuntulooks Engine they write tell copy file [COLOR=SandyBrown]libubuntulooks.so and libubuntulooks.la to /usr/lib/gtk-2.0/2.*.*/engines as root (substitute "2.*.*" with your version number) 
[COLOR=Black]that i want to know command [COLOR=SeaGreen]to copy file to folder[/COLOR] . or structure of command .
please tell me by step. thank you.
[/COLOR][/COLOR]

Ok I think I understand what you are trying to ask, if you copy things into a restricted part of the drive then use the sudo command.```
sudo cp filename /usr/lib/filename
```

What is your native language?

---

### Post by tonjaa on 2009-05-26
[COLOR=Green]thank you very much.[/COLOR] [COLOR=DarkOrange]for human beings[/COLOR]

---

### Post by tonjaa on 2009-05-26
[COLOR=Green]what's [COLOR=Red]wrong[/COLOR] ? i use command like this but i can't to copy file to engines .[/COLOR]
[COLOR=DarkOrange]tonjaa@tonjaa-desktop:~$ sudo cp libubuntulooks.so libubuntulooks.la /usr/lib/gtk-2.0/2.10.0/engines/
[sudo] password for tonjaa: 
cp: cannot stat `libubuntulooks.so': No such file or directory
cp: cannot stat `libubuntulooks.la': No such file or directory[/COLOR]
what is true command to copy ?
please tell me the way.

---

### Post by SuperSonic4 on 2009-05-26
It means those two files you specified are not in ~/Desktop. Was is a tarball you extracted? If so they usually decompress into their own folder so you might need to cd to that directory.

You can check the contents of the directory you are in by typing ```
ls
```

Also it's customary to wrap terminal output in code tags like [noparse]```
sudo make me a sandwich
```[/noparse]

---

### Post by tad1073 on 2009-05-26
you have to cd into the directory where the file lives.

example
```
cd /directory/of/some/file.file
sudo cp /directory/of/some/file.file /directory/of/some/file.file.1

```

---

### Post by themusicalduck on 2009-05-26
You want to install the Ubuntulooks engine? Isn't that in synaptic? Surely it'd be easier to install it from there.

System > Administration > Synaptic Package Manager

Or even just type 

```
sudo apt-get install gtk2-engines-ubuntulooks
```

into a terminal.

I'm assuming that that is the actual package you want.

---

### Post by ugm6hr on 2009-05-26
If you prefer to use GUI, try
```
gksudo nautilus
```

Copy & paste as usual.

Remember to close window when done, since nautilus will not alert you if you delete critical system files in this mode.

---

### Post by tonjaa on 2009-05-27
thank you very much for all answe r . 
[COLOR=SandyBrown]for human beings.[/COLOR]

---

### Post by Richiegs on 2009-10-20
Can anyone tell me how to copy a file on the desktop into /tmp as root?
I am new to Ubuntu. Many thanks in advance.

---

### Post by KeLa on 2009-10-20
Open terminal and then write
sudo cp ./Desktop/filename.ext /tmp

---

### Post by Boondoklife on 2009-10-20
you have two easy options, you can use `sudo cp FILE /tmp` or `gksudo nautilus`.
The later will give you a browsable interface instead of all command line.

---

