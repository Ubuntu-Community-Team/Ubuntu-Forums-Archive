---
title: "Installing Ut2004 PLZ HElp"
date: 2006-12-20
forum: Gaming &amp; Leisure
---

### Post by kiyometane on 2006-12-20
i got ut2004 cd version.
i'm using edgy amd64 and I'm new to Linux
i would like to install ut2004.
how do i do it and what do i need to do prior installation.:confused: 

i also heard about ut2004 bit, is it included in the retail cd?
thanks

---

### Post by Rhubarb on 2006-12-20
This may help:
[http://www.ubuntuforums.org/showthread.php?t=268851&highlight=ut2004](http://www.ubuntuforums.org/showthread.php?t=268851&highlight=ut2004)

I haven't tried it on the 64bit version of Edgy, so I don't know.
There is a wealth of information here about getting UT2004 to work in Dapper / Edgy, they're just hidden here in the forums :)

---

### Post by kiyometane on 2006-12-20
i finish installing the game, but i dont even know were the game is and in what folder
when i type ut2004 in console i get this error

kyo@kyo-desktop:~$ ut2004
./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
kyo@kyo-desktop:~$ 

any idea?

---

### Post by handy on 2006-12-20
Following is the call with the path (that I have added into the games menu via the **Alacarte Menu Editor**) that I use to start UT2k4.  It ran fine on Edgy for me, but I like Dapper better for other reasons.  I have also run it under 64bit Breezy with no problems.  UT2k4 actually installs a 64bit version of itself if it can.

**/home/handy/ut2004/ut2004**

So have a look in your **/home** for the **ut2004** directory, try using the search function from the menu to find it?

I searched for your ***libstdc++.so.5*** in synaptic it doesn't exist there for installation, it is part of the OS or of another package.

The path on my machine is:

**/usr/lib/libstdc++.so.5 **

Try searching for ut2004, & then specify the path to the executable ut2004.

---

### Post by kiyometane on 2006-12-21
i tried the search and the ut2004 folder is not even found in my system and yet it was installed.

---

### Post by kiyometane on 2006-12-21
I also cant even play the game. the game look like it will start and then it shuts. this is ther error i get
-desktop:~$ ut2004
Assertion failed: sizeof(*this)==GetClass()->GetPropertiesSize() [File:UnGame.cpp] [Line: 149]

History: 

Exiting due to error

---

### Post by handy on 2006-12-21
Did you copy the linux-installer.sh from CD-1 (not the Play Disk) onto the Ubuntu desktop & run it from there?

If not it might be a good idea to reinstall doing it that way.  The word is it is the most reliable method.  I have done it this way multiple times on different machines running different versions of Ubuntu without a problem.

---

### Post by handy on 2006-12-21
> **kiyometane said:**
> i tried the search and the ut2004 folder is not even found in my system and yet it was installed.

Did you search the **File System**?

---

### Post by kiyometane on 2006-12-21
i did not copy the installer to home. i run from cd. I finally got the location os the the folder
/us/local/games/ut2004
i dont know why the search can not find it in file system

---

### Post by handy on 2006-12-21
> **kiyometane said:**
> i did not copy the installer to home. i run from cd. I finally got the location os the the folder
/us/local/games/ut2004
i dont know why the search can not find it in file system

Does it run if you go into **/usr/local/games/ut2004**  & run **ut2004** ?

If not reinstall by copying the **linux-install.sh** onto the **_Desktop_** & run it from there.

---

### Post by kiyometane on 2006-12-21
no it does not. the game will start and immediately close up.

---

### Post by handy on 2006-12-21
You do have a 3D graphics card that is upto the task, with the latest drivers installed I hope?

---

### Post by kiyometane on 2006-12-21
i  upgraded my nvidia drivers but i dont know if it is the latest or he correct one.
can you tell me how to upgrade my drivers to the latest, not the beta drivers.
i have an nvidia 6600.
additionally i would like to know if i need to enable 3d acceleration or do some tweakings to my configuration in order to play 3d games such as ut2004](*,)

---

### Post by handy on 2006-12-21
> **kiyometane said:**
> i  upgraded my nvidia drivers but i dont know if it is the latest or he correct one.
can you tell me how to upgrade my drivers to the latest, not the beta drivers.
i have an nvidia 6600.
additionally i would like to know if i need to enable 3d acceleration or do some tweakings to my configuration in order to play 3d games such as ut2004](*,)

You don't have to tweak at all,  your card will be great for UT2k4 :-)

The way I allways install my nVidia drivers is by using Automatix, have a look at their site & follow the instructions for your version of Ubuntu.

Automatix, once installed, gives you options to install over 45 pieces of very popular software!  So, choose what you can use, leave the rest & it will do all the hard work (for us beginners that is! ) for you.

Here is the link:

 [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by kiyometane on 2006-12-21
automatix is great but is not good for a noob like me.](*,)

---

### Post by kiyometane on 2006-12-21
the problem was the megapack i installed from ubuntu gamer site i installed and i dont know how to remove it.
everything was working fine before i installed it.
i used the command 
cd && cd Desktop
sudo sh ut2004.megapack-english-2.run
 now i want to remove it but i dont what command to use
i would like also to install the patch 3369 a different way
thanks

---

### Post by handy on 2006-12-23
I would just delete the ut2k4 directory & reinstall, it will be the easy solution, possibly the only solution!

Don't forget, next time you install, copy the **unreal-install.sh** onto your **Desktop**, & then run it from there.

---

