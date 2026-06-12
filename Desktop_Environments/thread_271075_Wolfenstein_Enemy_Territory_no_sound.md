---
title: "Wolfenstein Enemy Territory no sound"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Monstroxus on 2006-10-04
Installed enemy territory, but no sound. I tried several suggested solutions as offered on this forum (echo this and that etc) but still no sound. Other games are fine, but enemy territory, which I want to play quite badly, doesn't. Anyone can provide some help? Thanks!

P.S. seems I have three soundcards in my pc (at least that what's I see under the soundcard option) when I want to set it to another default soundcard, it will jump back to the first one listed. I thought setting the default soundcard to another might solve the problem.

---

### Post by pay on 2006-10-04
Can you run the game in the terminal by typing it's name so we can see the error message.

---

### Post by Sambie on 2006-10-15
I'm also having a diffcult time getting the sounds to work. heres the log...

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/brittany/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/brittany/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/brittany/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No                                                               such file or directory"
Sys_LoadDll(/home/brittany/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae60ff40
Sys_LoadDll(ui) succeeded!

---

### Post by blackmh on 2006-10-15
Kill artsd before starting the game. Also, open etconfig.cfg in /home/username/.etwolf/etmain and check if it contains this line : seta snddevice "/dev/dsp"

---

### Post by Sambie on 2006-10-15
I do not have the file **etconfig.cfg** and when I **kill artsd** before starting the game it does not fix the problem.

---

### Post by jongkind on 2006-10-16
This is what works for me (from terminal):

sudo killall esd
sudo -i 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et

---

### Post by meborc on 2006-10-17
ahhh... finally something that works... i've been looking around for a year now for a complete solution... this works every time... thanks... (used to have to reboot every time to get sound) ;)

---

### Post by Sambie on 2006-10-17
> **jongkind said:**
> This is what works for me (from terminal):

sudo killall esd
sudo -i 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et

Thank you so much for helping me! This did the trick! thanks again!

---

### Post by Sambie on 2006-12-15
> **blackmh said:**
> Kill artsd before starting the game. Also, open etconfig.cfg in /home/username/.etwolf/etmain and check if it contains this line : seta snddevice "/dev/dsp"

The noobieness came to me.. 
I do have the file and yes it does have** seta snddevice "/dev/dsp"** on it. What can I do to fix it?

---

### Post by Malvolio on 2007-07-28
Yes, I was wondering if there was a permanent fix.  The terminal commands work but they only work for the OS session you did it in, reboot and you have to do them all over again.

---

### Post by EvilMarshmallow on 2007-08-05
Bumping for **Malvolio's** question above.

I am able to follow the instructions given by **jongkind,** but I'd like a permanent fix if there is one.

---

### Post by avik on 2007-08-05
Just put the instructions in a file, make it executable (right click->properties->permissions->allow executing file as program), then use that as the shortcut.  You can add it to the main menu by right clicking on the main menu and using Edit Menus.

---

### Post by MepisReign on 2007-08-05
If you want permanent sound on ET do this (I found this googling around some time ago):

in a terminal type: 
Code:
sudo -s 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 
exit


to get this commands started after booting automatically: 
open an editor with root rights (gedit) and type 
Code:
#!/bin/sh 
#Bug in Wolfenstein ET 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

save the file as "et-sound" in "/etc/init.d/". after this file is created you need to tell your system about it: 
Code:
sudo chmod 755 /etc/init.d/et-sound 
sudo update-rc.d et-sound defaults


------------- 

Edit: 
in case of 
bash: /proc/asound/card0/pcm0p/oss: Permission denied 
type in a terminal 
sudo chmod 777 /proc/asound/card0/pcm0p/oss

I have been playing this game for 3 years now and this solution was the absolute one...

Hoping this helps

Regards

MepisReign a.k.a (HAM)Reign***

---

### Post by bouncingmolar on 2007-10-15
cool thanks that worked for me

---

### Post by dhruva023 on 2007-10-15
> **jongkind said:**
> This is what works for me (from terminal):

sudo killall esd
sudo -i 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et

thanks,

it workd for me too.

thank you very much

---

### Post by darkstar8 on 2007-12-04
dude thank you so much. I kept reading about echo this and that but everytime it would say permission denied.
no one ever mentioned the sudo -i switch
I betcha this works for quake 3 too. maybe even quake 2!

---

### Post by troykd on 2008-02-05
Thanks so much... worked for me with Gutsy on my Dell 1500

> **MepisReign said:**
> If you want permanent sound on ET do this (I found this googling around some time ago):

in a terminal type: 
Code:
sudo -s 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 
exit


to get this commands started after booting automatically: 
open an editor with root rights (gedit) and type 
Code:
#!/bin/sh 
#Bug in Wolfenstein ET 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

save the file as "et-sound" in "/etc/init.d/". after this file is created you need to tell your system about it: 
Code:
sudo chmod 755 /etc/init.d/et-sound 
sudo update-rc.d et-sound defaults
*

---

