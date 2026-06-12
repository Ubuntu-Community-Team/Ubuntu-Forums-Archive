---
title: "create a bash file to run a perl scirpt"
date: 2009-06-14
forum: General Help
---

### Post by calvinlyp on 2009-06-14
hi i am new to xubuntu platform.

i require to create a bash file to run a perl script. 
as it is a long command to run the script thus was thinking is it possible to create a bash file and double click it will auto run the long command to invoke the perl script.

please advise.

---

### Post by Altay_H on 2009-06-14
If you can run the command from the terminal, you should just be able to create a bash script out of it:

```
#!/bin/sh

[COMMAND TO RUN SCRIPT]
```
Obviously replace [COMMAND TO RUN SCRIPT] with however you want to call your perl script.

However, based on your description I'm wondering why you don't just create a shortcut/link to the perl file.

---

### Post by calvinlyp on 2009-06-14
> **Altay_H said:**
> If you can run the command from the terminal, you should just be able to create a bash script out of it:

```
#!/bin/sh

[COMMAND TO RUN SCRIPT]
```Obviously replace [COMMAND TO RUN SCRIPT] with however you want to call your perl script.

However, based on your description I'm wondering why you don't just create a shortcut/link to the perl file.

it is because to run the script it requires some addtional specification of the some config files.

eg like this is what i have to type in the terminal:
user@user: CONFIG=/home/xxx/yyy/ccc/aaa.xml ./myscript.pl --configfile /home/yyy/sss/eee

furthermore this command have to be invoke in the folder of where the perl file reside.
does the bash file has to be in the same folder?

please advise.
thx in advance.

---

### Post by Altay_H on 2009-06-14
> **calvinlyp said:**
> eg like this is what i have to type in the terminal:
user@user: CONFIG=/home/xxx/yyy/ccc/aaa.xml ./myscript.pl --configfile /home/yyy/sss/eee
I think that should still work if you place it in a shortcut/launcher. It's hard to say without actually trying it out. Give it a try and see if it works (unless you'd rather just use a bash file).

> **calvinlyp said:**
> furthermore this command have to be invoke in the folder of where the perl file reside.
does the bash file has to be in the same folder?
The bash file doesn't have to be in the same folder if you use an absolute address rather than a relative address. To do this change this part of the command:
```
 ./myscript.pl 
```
to the location at which the perl file will reside. For example:
```
 /home/user/perl/myscript.pl 
```

---

### Post by calvinlyp on 2009-06-14
thanks for the quick reply!!

> **Altay_H said:**
> I think that should still work if you place it in a shortcut/launcher. It's hard to say without actually trying it out. Give it a try and see if it works (unless you'd rather just use a bash file).

what i meant was in the terminal, i have to change directory to the folder where the perl file resides.

next i need to type the command which i shown in my previous thread.

thus from what you mention about shortcut/launcher is it possible? or how do i go about doing it?

but if i was to use the previous example you given 
```

     #!/bin/sh

[COMMAND TO RUN SCRIPT]

```the [COMMAND TO RUN SCRIPT] 
will be replace by:
CONFIG=/home/xxx/yyy/ccc/aaa.xml ./myscript.pl --configfile /home/yyy/sss/eee

is that correct?

> **Altay_H said:**
> 
The bash file doesn't have to be in the same folder if you use an absolute address rather than a relative address. To do this change this part of the command:
```
 ./myscript.pl 
```to the location at which the perl file will reside. For example:
```
 /home/user/perl/myscript.pl 
```

yeap i understand about giving the absolute path, and i can create the bash file using mousepad and save as a .sh extention?
and i do not need to place the bash file in /bin folder right?

your help will be greatly appreciated.

---

### Post by Altay_H on 2009-06-14
> **calvinlyp said:**
> what i meant was in the terminal, i have to change directory to the folder where the perl file resides.

next i need to type the command which i shown in my previous thread.

thus from what you mention about shortcut/launcher is it possible? or how do i go about doing it?
I'm convinced the only reason you need to change the directory in the terminal is because you're using a relative path. If you change it to an absolute path, it should work in a shortcut/launcher.

I forget the details of creating a launcher in xubuntu, but I know in Ubuntu you just right-click the desktop and choose "Create Launcher" and it asks you for a command. I think it might be a little more complicated in xubuntu. Let me know if you want step-by-step instructions.

> **calvinlyp said:**
> 
but if i was to use the previous example you given the [COMMAND TO RUN SCRIPT] 
will be replace by:
CONFIG=/home/xxx/yyy/ccc/aaa.xml ./myscript.pl --configfile /home/yyy/sss/eee

is that correct?
Yes, that's correct. However, don't forget to change the relative path to an absolute one.

> **calvinlyp said:**
> 
yeap i understand about giving the absolute path, and i can create the bash file using mousepad and save as a .sh extention?
In Linux the extension doesn't actually matter, but the .sh extension is the one typically used with bash files, so yes.

> **calvinlyp said:**
> 
and i do not need to place the bash file in /bin folder right?
No, you don't need to place it in the /bin folder. However, you do need to make it executable. Let me know if you're not familiar with that process.

---

### Post by calvinlyp on 2009-06-15
> **Altay_H said:**
> I'm convinced the only reason you need to change the directory in the terminal is because you're using a relative path. If you change it to an absolute path, it should work in a shortcut/launcher.
 
I forget the details of creating a launcher in xubuntu, but I know in Ubuntu you just right-click the desktop and choose "Create Launcher" and it asks you for a command. I think it might be a little more complicated in xubuntu. Let me know if you want step-by-step instructions.
 
 

 
 
there is a link to youtube on the create of launcher
[http://www.youtube.com/watch?v=x8kfob6fBO8](http://www.youtube.com/watch?v=x8kfob6fBO8)
 
however that is the shortcut to create launcher,
is there a way to create a launcher with the predefine command for the terminal?

---

### Post by asmoore82 on 2009-06-15
you can make a launcher that uses the "env" wrapper command to set up the environment
and launch the program.

Here is my Counter Strike launcher with Wine's files in a non-standard location:
```
[COLOR="Lime"]**$** cat bin/Counter\ Strike\ 1.6\ Non\ Steam.desktop [/COLOR]
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Counter Strike 1.6 Non Steam
**Exec=env WINEPREFIX="/home/asmoore/Games/wine-cstrike" wine "C:\\Program Files\\Valve\\hl.exe" -nomaster -game cstrike +localinfo mm_gamedll dlls/zbotcz.dll**
Type=Application
StartupWMClass=Wine
Comment=Counter Strike 1.6 Non Steam - Cumulative patch V21
Path=/home/asmoore/Games/wine-cstrike/dosdevices/c:/Program Files/Valve
Icon=/home/asmoore/Games/wine-cstrike/drive_c/Program Files/Valve/cstrike/cstrike.ico
GenericName[en_US]=
```

---

