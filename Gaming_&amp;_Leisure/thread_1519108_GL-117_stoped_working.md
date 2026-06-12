---
title: "GL-117 stoped working"
date: 2010-06-27
forum: Gaming &amp; Leisure
---

### Post by linuxnoob420 on 2010-06-27
okay so this has been a problem i been having gl-117 no longer starts in  ubuntu 10.04 i tried reinstalling but no go this has happend   in  ubuntu 8.10 as well as 9.10 im not at all sure what i did but when i go  to start the game nothing happends! is anone  haveing this problem and  does anyone know how to fix it please im in a rut here thanks in advance  :)

---

### Post by hikaricore on 2010-06-28
Terminal output please.

---

### Post by linuxnoob420 on 2010-06-28
exp@exp-laptop:~$ gl-117
Info: Found gl-117 data directory /usr/share/games/gl-117 
Info: Startup gl-117, V1.3 ... 
Info: Loading /home/exp/.gl-117/conf 
Info: Saving /home/exp/.gl-117/conf 
Info: Loading /home/exp/.gl-117/conf.interface 
Info: Saving /home/exp/.gl-117/conf.interface 
Info: Using SDL and GLUT
Segmentation fault
exp@exp-laptop:~$

---

### Post by Hairybudda on 2010-06-28
You're gonna need to use GDB and get us a backtrace

---

### Post by linuxnoob420 on 2010-06-29
okay i have no idea how to use GDB i know its a debugger but im not sure how to use it im still a noob here!

---

### Post by linuxnoob420 on 2010-06-29
a little help please maybe a command i could use to get the right output

---

### Post by ecatodarcus on 2011-01-25
hello!

i have the same problem. when i launch it my screen gets black. The same happens with Egoboo which is another 3d game but it does not happen with supertuxkart, blender or other 3d applications.
thank you

---

### Post by jalms on 2011-09-16
Same problem here, with Natty Narwhal (11.04).
Terminal says:
almeida@ubuntu:~$ gl-117
Info: Found gl-117 data directory /usr/share/games/gl-117 
Info: Startup gl-117, V1.3 ... 
Info: Loading /home/almeida/.gl-117/conf 
Info: Saving /home/almeida/.gl-117/conf 
Info: Loading /home/almeida/.gl-117/conf.interface 
Info: Saving /home/almeida/.gl-117/conf.interface 
Info: Using SDL and GLUT
Info: Using SDL_mixer
Falha de segmentação
[means "Segmentation Fault"]

Tried re-install but no good.

Thanks in advance

---

### Post by Anson S on 2011-11-18
And I'm having the same issue, here is the Terminal output:

Info: Found gl-117 data directory /usr/share/games/gl-117 
Info: Startup gl-117, V1.3 ... 
Info: Loading /home/roger/.gl-117/conf 
Info: Saving /home/roger/.gl-117/conf 
Info: Loading /home/roger/.gl-117/conf.interface 
Info: Saving /home/roger/.gl-117/conf.interface 
Warning: Could not load saves/pilots
Warning: Could not load pilot
Info: Using SDL and GLUT
Info: Using SDL_mixer
there is no soundcard
Info: Joystick "Microsoft Microsoft® 2.4GHz Transceiver v7.0" detected
Segmentation fault

Help anyone?

---

### Post by samnjosh6 on 2011-12-02
Hi I know nothing.
Less than a week ago I installed gl-117 and it started up fine.I went to the options and changed the graphics quality setting higher. I played the game and it was great fun. I exited the game. That was the only time I played it. Now when I try to open it the music will start for 1 second with a black screen and then close. I figure that the setting i changed didnt take effect until after I exited the game and now my computer is unable to handle the higher graphics settings. I have reinstalled it a couple of times but that isnt working. If this helps anyone thats great. if anyone can help me fix my prob that would be great too thanks bye.

---

### Post by ocirne94 on 2011-12-03
Please post some more of your configuration, on Kubuntu 11.10 Nvidia 250 GTS I manage to run Gl-117 absolutely fine.
Cheers
Ocirne

---

### Post by Starter1961 on 2012-01-24
> **samnjosh6 said:**
> Hi I know nothing.
Less than a week ago I installed gl-117 and it started up fine.I went to the options and changed the graphics quality setting higher. I played the game and it was great fun. I exited the game. That was the only time I played it. Now when I try to open it the music will start for 1 second with a black screen and then close. I figure that the setting i changed didnt take effect until after I exited the game and now my computer is unable to handle the higher graphics settings. I have reinstalled it a couple of times but that isnt working. If this helps anyone thats great. if anyone can help me fix my prob that would be great too thanks bye.
I had the dame problem.  Just delete the .gl-117 folder (hidden folder use CTRL + H to see it) in your home directory, and then start the game again.  It should be fine, but you'll lose all your data.

---

### Post by Wolfy32 on 2012-07-27
You have probably set an unsupported GL resolution and then upon restart it gives you segmentation fault.

Simplest Solution:
Just delete configuration options : rm ~.gl-117

---

### Post by imkaushal on 2012-10-08
Hi guys, it did not even run once for me (Ubuntu 10.04) :( :mad:

```
me@my-desktop:~$ gl-117 -d5
Info: Entering debug level 5
Info: Found gl-117 data directory /usr/share/games/gl-117 
Info: Startup gl-117, V1.3 ... 
Debug: Getting directory locations
Info: Loading /home/me/.gl-117/conf 
Info: Saving /home/me/.gl-117/conf 
Info: Loading /home/me/.gl-117/conf.interface 
Info: Saving /home/me/.gl-117/conf.interface 
Debug: Creating/Loading pilots list
Warning: Could not load saves/pilots
Warning: Could not load pilot
Info: Using SDL and GLUT
Debug: Setting SDL caption
Debug: Creating sound system
Info: Using SDL_mixer
Debug: Playing startup music
Debug: Calling main initialization method
Debug: Creating calculation tables
Debug: Creating advanced OpenGL methods
Debug: Loading textures
Segmentation fault
```

any help appreciated !!!

---

### Post by imkaushal on 2012-10-08
> **imkaushal said:**
> Hi guys, it did not even run once for me (Ubuntu 10.04) :( :mad:

```
me@my-desktop:~$ gl-117 -d5
Info: Entering debug level 5
Info: Found gl-117 data directory /usr/share/games/gl-117 
Info: Startup gl-117, V1.3 ... 
Debug: Getting directory locations
Info: Loading /home/me/.gl-117/conf 
Info: Saving /home/me/.gl-117/conf 
Info: Loading /home/me/.gl-117/conf.interface 
Info: Saving /home/me/.gl-117/conf.interface 
Debug: Creating/Loading pilots list
Warning: Could not load saves/pilots
Warning: Could not load pilot
Info: Using SDL and GLUT
Debug: Setting SDL caption
Debug: Creating sound system
Info: Using SDL_mixer
Debug: Playing startup music
Debug: Calling main initialization method
Debug: Creating calculation tables
Debug: Creating advanced OpenGL methods
Debug: Loading textures
Segmentation fault
```any help appreciated !!!

IT'S DONE!!!



Opened the *conf* file in folder *.gl-117* & changed the *width x height* values from *1024 x 768* to *800 x 600* as my monitor's native resolution is 1280 x 720
(possible values mentioned in the file are 640x480, 800x600, 1024x768, 1152x864, 1280x768, 1280x960, 1280x1024)

:guitar:

:lolflag:

---

