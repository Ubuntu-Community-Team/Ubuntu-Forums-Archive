---
title: "doom3 wont start"
date: 2006-10-29
forum: Gaming &amp; Leisure
---

### Post by Jason711 on 2006-10-29
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - <deleted>
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/sujay/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg


anybody know what im doing wrong?

i have an a64 3700+ w/6800gs on edgy

---

### Post by pay on 2006-10-29
Do you have the Nvidia drivers installeD?

---

### Post by Jason711 on 2006-10-29
yeah, verified 3d acceleration through glxgears.  installed the driver through automatix2.

---

### Post by _simon_ on 2006-10-29
You seem to be missing pak004.pk4

---

### Post by Jason711 on 2006-10-29
i have that in there... :confused:

---

### Post by Iarwain ben-adar on 2006-10-29
Do you have the default.cfg file in your doom3_dir/base folder?

You have to copy that too ;)


Iarwain

---

### Post by _simon_ on 2006-10-29
> **Jason711 said:**
> i have that in there... :confused:

Strange!

Compare what I get when I load Doom 3 to what you get:

```

Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/simon/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)

```

---

### Post by Jason711 on 2006-10-30
i dont recall copying a cfg file... ill look for that. thnx.

---

### Post by Jason711 on 2006-10-30
i couldnt find a cfg file to copy.... im not sure what else i can do.

---

### Post by Iarwain ben-adar on 2006-10-31
You can have mine,
if it could help you..


Iarwain

---

### Post by paparappa on 2007-04-12
I've copied all .pk4 files and the cfg file to $installdir/base/ but what do i do know? What do i type in terminal to start Doom 3? Im sorry but i'm such a linux rookie.

---

### Post by Iarwain ben-adar on 2007-04-12
Hiya :D

Don't worry, be happy ;)

So for your Doom3 problem:
Did you install it? (don't know any links, but have a search for 'doom install' on these forums)

To start from the terminal, type 
```
./name_of_doom3_file
```
once you cd'd in the right dir..

(quick how to!)
```
pwd
>> /home/iarwain/
cd doom3
pwd
>> /home/iarwain/doom3/
./name_of_doom3_file
```

This should get you started i think..
cd stands for Change Directory
pwd stands for Print Working Dir
>> is the output from your terminal

! cd to the dir where Doom is installed !
(e.g. /usr/share/doom3/ )


Iarwain

---

### Post by paparappa on 2007-04-13
I'm sorry but i dont get it :S

What I've done is that i ran the doom3-linux-1.3.1.1304-sdk.x86.run
Then I copied every .pk4 files from the CDs to usr/local/games/doom3/base .
But what do i do know? That's my question :P

And in terminal where you say i shall write "./name_of_doom3_file"
What is the doom3 file for an example look like and is it on the cd or in the usr/local/games/doom3/ folder?

Sorry for being so noobish :P

---

### Post by Iarwain ben-adar on 2007-04-13
No problem man ;)

So, it is a long time since i installed Doom3 (don't have the cd's anymore), and don't got it installed anymore.

Have you tried entering 'doom3' as a command?


Iarwain

---

### Post by paparappa on 2007-04-13
well thats the thing... where do i enter a command? Can you maybe upload a printscreen or something how it looks when you enter a command :P

---

### Post by Iarwain ben-adar on 2007-04-13
Just say so ;)

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

And the screenie ^^
(i use Kubuntu, the link is for Ubuntu)


Iarwain

---

### Post by paparappa on 2007-04-13
when i type doom3 in terminal it sais something like 

"bash: doom3: command not found"

---

### Post by Iarwain ben-adar on 2007-04-13
Hi there,
if you are sure you installed the game..
check these locations ;)

```
iarwain@iarwain-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

Or do a ```
locate doom3
```

This should give the locate of the doom3 file ;-)

To execute, just type in the location with /doom3 after it 
e.g. /usr/bin/doom3


Iarwain

---

### Post by paparappa on 2007-04-13
thank so much for helping.. but im not done yet :P

Well here's where my doom3 is "/usr/local/games/doom3-sdk/"

and when i  type locat doom3 it just prints every file inside of the doom3-sdk folder :/

---

### Post by Iarwain ben-adar on 2007-04-13
:D

Type this
```
cd /usr/local/games/doom3-sdk/
./doom3
```

This should get your game running =)


Iarwain

---

### Post by paparappa on 2007-04-13
so i rename the folder to doom3 and then type doom3 in terminal?
It's just the same thing... isn't there a file or something somewhere wich i just can double-click... this is so complex :P

---

### Post by Iarwain ben-adar on 2007-04-13
You can double-click 'doom3' in the folder '/usr/local/games/doom3-sdk' ;)

And you need not to rename a folder.. Just cd into it (Change Dir) and then execute doom3 ;)


Iarwain

---

### Post by white shadow on 2008-06-02
i dont have the default.cfg on the dvd:( . where can i get one?

---

### Post by Sleaka J on 2008-06-03
> **white shadow said:**
> i dont have the default.cfg on the dvd:( . where can i get one?

default.cfg is created by the game once it starts to load. It doesn't exist on the discs.

To the OP: I had that exact error message when I'd only copied the PK4 files from Disc 1 (There's only 2 PK4 files on Disc 1). Once I'd copied all 5 PK4 files (PAK000.PK4, PAK001.PK4, PAK002.PK4, PAK003.PK4, PAK004.PK4) from all 3 CDs, I got into the game fine.

If you don't have the following files in your /doom3/base directory, the game won't start:

GAME01.PK4 (Put there by the installation script)
GAME02.PK4 (Put there by the installation script)
GAME03.PK4 (Put there by the installation script)
PAK000.PK4
PAK001.PK4
PAK002.PK4
PAK003.PK4
PAK004.PK4
PAK005.PK4 (Put there by the installation script)
PAK006.PK4 (Put there by the installation script)
PAK007.PK4 (Put there by the installation script)
PAK008.PK4 (Put there by the installation script)

To paparappa: Sounds like you downloaded the SDK, not the game client. You should have downloaded the following file:

doom3-linux-1.3.1.1304.x86.run (20.16Mb)

not

doom3-linux-1.3.1.1304-sdk.x86.run (10.54Mb)

---

