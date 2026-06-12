---
title: "kleansweep"
date: 2006-01-13
forum: Desktop Environments
---

### Post by kaber on 2006-01-13
hi,been atit for awhile but still very new.
Downloaded kleansweep-0.2.4.tar.bz2 and tried everything to install it
no joy! Is there another cleaning program that kubuntu will accept?
and a BIG HI to eveyone out there and all the people behind this project,
keep up the good work

---

### Post by MartinG on 2006-01-13
I had the same problem, so installed Kleansweep from the Klik site:
[http://klik.atekon.de/](http://klik.atekon.de/)

Works perfectly.

---

### Post by sargo on 2006-01-13
[QUOTE=kaber]hi,been atit for awhile but still very new.
Downloaded kleansweep-0.2.4.tar.bz2 and tried everything to install it
no joy! Is there another cleaning program that kubuntu will accept?
and a BIG HI to eveyone out there and all the people behind this project,
keep up the good work[/QUOTE]

Compile the application with:

./configure
This instruction don't work but after a warning message unpack de scons script. After this type

./scons
./scons install

To uninstall the application type:

./scons -c install

Sorry for my english.

---

### Post by kaber on 2006-01-13
MartinG,thanks looks good but i have ubuntu with kubuntu desktop and for some reason cannot get it down.
Sargo,thanks for the reply,but still it will not configure it

kaber@ubuntu:~$ cd'/home/kaber/kleansweep/kleansweep-0.2.4'
bash: cd/home/kaber/kleansweep/kleansweep-0.2.4: No such file or directory
kaber@ubuntu:~$ sudo -i
root@ubuntu:~# cd '/home/kaber/kleansweep/kleansweep-0.2.4'
root@ubuntu:/home/kaber/kleansweep/kleansweep-0.2.4# /configure
-bash: /configure: Permission denied
root@ubuntu:/home/kaber/kleansweep/kleansweep-0.2.4#

that is what comes up in my terminal.

---

### Post by f1dave on 2006-01-15
yep, you're typing /configure as opposed to ./configure

That could be your problem

---

### Post by kaber on 2006-01-16
Thanks Dave,you where right but It still gave out errors a bit later in the installation,must be missing something on my system.
kaber

---

### Post by noigeaR on 2006-01-16
how about posting those error messages here so we can help you to get kleansweep compiled?

---

### Post by ice60 on 2006-01-17
can someone show me how to install kleansweep at klik? i couldn't even find a search box so i used google to get to these two pages
[http://kleansweep.klik.atekon.de/](http://kleansweep.klik.atekon.de/)
[http://klik.atekon.de/contrib.php](http://klik.atekon.de/contrib.php)

when i click the download icons i get a message saying it's an unknown protocol. i installed the script or whatever it is using wget from klik on the home page and a popup said i could start installing stuff :rolleyes: . do i need to reboot or something? thanks

i use ubuntu breezy

---

### Post by MartinG on 2006-01-17
The install script makes (made) changes to your fstab, so it's probably a good idea to reboot (I'm not sure if it's absolutely *necessary*:) )

On Kubuntu I have a new menu section titled "Applications (installed by klik)"; I think you should have the same in Ubuntu?  In this is an entry "Install more software", which in fact takes your browser to klik's home page. If you work your way to the app you want, at some stage you will click on a button and be asked "Do you want to download and run <your_app>"? Click yes, and that's it.

NB read the general stuff; a klik install is different from an install from a repository!!

Funny, I've just checked.  I'm sure there *used* to be a search box!

---

### Post by ice60 on 2006-01-17
hi, Martin i can't see it atm i did a killall gnome-panel too.  i might try a reboot in a bit and see if it turns up and if i can do an install, i'd really love to try kleansweep, although, i'm a total newbie but  it should help me learn abit about some of the files on the system

. yeah, no search box :confused: oh well. i did try and compile too and i got this error
```
:~/Desktop/kleansweep-0.2.4$ ./scons
scons: Reading SConscript files ...
Checking for kde-config           :  kde-config was found as /usr/bin/kde-config
Checking for kde version          :  3.4.3
Checking for the qt library       :  qt was not found
Please set QTDIR first (/usr/lib/qt3?) or try scons -h for more options

```
i had alook for the qt3 directory and it's here /usr/lib/qt3 i don't understand why there's a question mark in the error after the qt3. 
```
Please set QTDIR first (/usr/lib/qt3?)
```
but, i think i'll see if i can get klik to work first, i'm sure i tried it once before with the same result :(

---

### Post by ice60 on 2006-01-17
does anyone know if this will set the path? so i can finish the install?
```
export QTDIR=/usr/share/qt3
```
i did a forum search and there's nothing

---

### Post by MartinG on 2006-01-18
[QUOTE=ice60] i did try and compile too and i got this error
```
:~/Desktop/kleansweep-0.2.4$ ./scons
scons: Reading SConscript files ...
Checking for kde-config           :  kde-config was found as /usr/bin/kde-config
Checking for kde version          :  3.4.3
Checking for the qt library       :  qt was not found
Please set QTDIR first (/usr/lib/qt3?) or try scons -h for more options

```
i had alook for the qt3 directory and it's here /usr/lib/qt3 i don't understand why there's a question mark in the error after the qt3. 
```
Please set QTDIR first (/usr/lib/qt3?)
```
but, i think i'll see if i can get klik to work first, i'm sure i tried it once before with the same result :([/QUOTE]Hi, maybe by now you've got the klik version to work:???:  Sorry not to have responded earlier.

The reason I used the klik version was because I too had compiling difficulties.  As to your specific query, I *think* the script is looking for the qt3 dev (development) libraries and headers, which aren't installed by default -- and if they are installed go somewhere else than /usr/lib.  If either or both is true, then ```
export QTDIR=/usr/lib/qt3
``` won't work as what it's looking for isn't there.

If installed, you will have stuff in /usr/share/qt3 and /usr/include/qt3 (well, that's where it is on my system), but in any case AFAIK you shouldn't need to export the path; I think the installation process modifies the path accordingly.

Not as helpful as I'd like to be.  Sorry, and best of luck:)

---

### Post by kaber on 2006-01-18
hi noigeaR
Here is my attemp to install kleansweep

kaber@ubuntu:~/kleansweep-0.2.4/kleansweep-0.2.4$ ./configure
Unpacking scons-mini
This utility uses scons build system. Type:

./scons
./scons install

To compile and install this program. Read INSTALL for deatiled info.
kaber@ubuntu:~/kleansweep-0.2.4/kleansweep-0.2.4$ ./scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
-I/usr/include/kde/ -I/usr/include/qt3 -O2 -DNDEBUG -DNO_DEBUG -DQT_NO_TRANSLATION -DVERSION=\"0.2.4\" -I. -Isrc -c -o src/configdlg.o src/configdlg.cpp
sh: -/: invalid option
Usage:  sh [GNU long option] [option] ...
        sh [GNU long option] [option] script-file ...
GNU long options:
        --debug
        --debugger
        --dump-po-strings
        --dump-strings
        --help
        --init-file
        --login
        --noediting
        --noprofile
        --norc
        --posix
        --protected
        --rcfile
        --restricted
        --verbose
        --version
        --wordexp
Shell options:
        -irsD or -c command or -O shopt_option          (invocation only)
        -abefhkmnptuvxBCHP or -o option
scons: *** [src/configdlg.o] Error 2
scons: building terminated because of errors.
kaber@ubuntu:~/kleansweep-0.2.4/kleansweep-0.2.4$ ./scons install
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
-I/usr/include/kde/ -I/usr/include/qt3 -O2 -DNDEBUG -DNO_DEBUG -DQT_NO_TRANSLATION -DVERSION=\"0.2.4\" -I. -Isrc -c -o src/configdlg.o src/configdlg.cpp
sh: -/: invalid option
Usage:  sh [GNU long option] [option] ...
        sh [GNU long option] [option] script-file ...
GNU long options:
        --debug
        --debugger
        --dump-po-strings
        --dump-strings
        --help
        --init-file
        --login
        --noediting
        --noprofile
        --norc
        --posix
        --protected
        --rcfile
        --restricted
        --verbose
        --version
        --wordexp
Shell options:
        -irsD or -c command or -O shopt_option          (invocation only)
        -abefhkmnptuvxBCHP or -o option
scons: *** [src/configdlg.o] Error 2
scons: building terminated because of errors.
kaber@ubuntu:~/kleansweep-0.2.4/kleansweep-0.2.4$

---

### Post by ice60 on 2006-01-20
hi, thanks for the help. i didn't get klik working. but, i installed FSlint instead, there's a thread which mentions it [here](http://ubuntuforums.org/showthread.php?t=116220)  #14 onward. if FSlint doesn't work for me i'll have another go at installing kleansweep.

---

