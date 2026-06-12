---
title: "WoW Performance"
date: 2006-03-31
forum: Gaming &amp; Leisure
---

### Post by dragge on 2006-03-31
Hey, ive been trying all hacks and stuff i could find soon and still got lousy performance.
Playing my alt around Westfall area renders me with ~15-20fps which i think is pretty low.

System specs:
P4 3,5Ghz
2Gb RAM
NVIDIA 6800 Ultra 256 PCI-E with the newest NVIDIA drivers.

Ubuntu 5.10
Wine 0.9.9 with misc wow patches.

Havent playd wow for quite some time now, last time i played i got better fps in linux than in windows.
Anyone got some info that might be of use for me to help increase performance?

Thanks // Marcus

---

### Post by dermotti on 2006-03-31
I always got at least -25% performance under Linux/Wine. The thing that helped performance the most was tuning down the clip range and running under opengl

---

### Post by Zer0d on 2006-03-31
I have preformance problems with WoW on cedega, it's like 10-15 FPS...

---

### Post by Zer0d on 2006-03-31
Read up on this one:
[http://ubuntuforums.org/showthread.php?t=120615]("http://ubuntuforums.org/showthread.php?t=120615")

---

### Post by dragge on 2006-03-31
[QUOTE=dermotti]I always got at least -25% performance under Linux/Wine. The thing that helped performance the most was tuning down the clip range and running under opengl[/QUOTE]

Im running it under opengl.
Last time i tried playing i got 65-70fps in Darnassus for example.
Now i got 15fps O_o

Even with graphic settings turned down to minimum.

---

### Post by dragge on 2006-03-31
[QUOTE=Zer0d]Read up on this one:
[http://ubuntuforums.org/showthread.php?t=120615]("http://ubuntuforums.org/showthread.php?t=120615")[/QUOTE]

I have read throu that one and tried every hack and so on and still this lack of performance. :(

---

### Post by theh0g on 2006-03-31
Running it under Cedega with OpenGL, which is much faster than D3D, not to mention shaders I can use. I have 15 - 25 FPS in IF, 30+ outside and 50+ in instanced. I have gf4200Ti, Athlon 1700xp and 512MB RAM...I think that's pretty fast for this configuration.

I've tried running with wine and it's pretty fast, but there are some black blocks on ground around me and other players so I can't play like that. Is there a fix for that? I'd love to ditch Cedega so I can play WoW legaly on Linux.

---

### Post by Zer0d on 2006-03-31
Do I need to configure cedega to use OpenGL or is it automatic?
Hardware:
2GB DDR 2 RAM
4.2GHz 1048MHz BUSS
Nvidia 6600

My hardware should not be a problem :S Sometimes the game is down to 5FPS and it's very annoying...

---

### Post by Zer0d on 2006-04-01
[IMG]http://img425.imageshack.us/img425/116/screenshot4kb.png[/IMG]

As you can see the the processor is running 100% somehow, is that normal or is something wrong? I tryed to do wine WoW.exe -opengl and start it with cedega but it uses the same amount of processing power...( The mouse doesent work properly in wine )

---

### Post by pirast on 2006-04-01
wow works fine for me under dapper with cedega and with
geforce 5200
athlon xp 3000+
1gb ram

---

### Post by Zer0d on 2006-04-01
How high is the processor load for you?
What cedega version do you use?
Engine version?
Wine version?
:p

---

### Post by Zer0d on 2006-04-01
I need to run cedega from the terminal or else it wont start :(

---

### Post by smack on 2006-04-01
Runs at 15-20fps in busy areas on my 2ghz opteron and 7800gtx. I'd consider the performance unplayable.

---

### Post by pirast on 2006-04-01
system usage:
> top - 00:54:54 up 12:12,  4 users,  load average: 1.22, 0.66, 0.28
Tasks: 111 total,   1 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s): 35.0% us, 13.5% sy,  0.0% ni, 50.0% id,  0.9% wa,  0.2% hi,  0.5% si
Mem:   1034668k total,  1015152k used,    19516k free,    18872k buffers
Swap:  1558264k total,    18428k used,  1539836k free,   424348k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
28680 martin    25   0  416m 227m  18m S 93.1 22.6   0:49.56 wine



cedega version: 5.1
engine version:  5.1.2

glxgears fps (1280x1024):
> 6520 frames in 5.0 seconds = 1303.886 FPS
6420 frames in 5.0 seconds = 1283.930 FPS


WoW FPS: ~30, but I do not notice any lags, it runs as fluid as it should

You may want to know that I do not run WoW.exe with -opengl.

---

### Post by Zer0d on 2006-04-01
I use the same cedega and engine version. How do i get the FPS output with glxgears? I know how to run it but not how to get the FPS output...

---

### Post by pirast on 2006-04-01
Open the file config which is usally stored in ~/.cedega/NAME, for example ~/.cedega/World of Warcraft.

search for

"ShowFPS" = "N"

change to

"ShowFPS" = "Y"

hf martin

---

### Post by Zer0d on 2006-04-01
Thanks ;) I did as you said but where is the output of the FPS? Is it suppose to show up in the game or in cedega?...

---

### Post by Zer0d on 2006-04-01
Ok gonna try the new post to hehe

---

### Post by Zer0d on 2006-04-01
Checked the config file and it was set to yes "Y"..

---

### Post by Zer0d on 2006-04-01
Still i cant find where the FPS status is showed :P

---

### Post by pirast on 2006-04-01
It should be displayed at the left top of the game.

Are you sure that you edited the correct file? When you do not tell cmdcedega which profile it should use then cedega uses the Dot Transgaming config in ~/.cedega/Dot TransGaming

martin

---

### Post by Zer0d on 2006-04-01
I edited ~/.cedega/WoW/config-cedega_5.1.2
and
~/.cedega/configuration_profiles/cedega_5.1.2
and
~/.cedega/WoW/config

lol but it still does not show the FPS in the upper left corner of the game. I also tryed to change the Profile by right clicking on the icon and Icon Properties and change the Configuration Profile..

---

### Post by pirast on 2006-04-01
As I said. Since you do not start WoW with the cedega -config option you have to edit

~/.cedega/Dot TransGaming/config

I think

martin

---

### Post by Zer0d on 2006-04-01
Yeah if i could find the folder...

```
root@zer0d:~/.cedega# ls -al
total 28
drwxr-xr-x  7 zer0d zer0d 4096 2006-04-01 13:57 .
drwxr-xr-x 23 zer0d zer0d 4096 2006-04-01 15:19 ..
drwxr-xr-x  2 zer0d zer0d 4096 2006-04-01 13:57 configuration_profiles
drwxr-xr-x  2 zer0d zer0d 4096 2006-04-01 13:43 .default_configuration_profiles
drwxr-xr-x  2 zer0d zer0d 4096 2006-04-01 13:42 .languages
drwxr-xr-x  3 zer0d zer0d 4096 2006-04-01 13:43 .winex_ver
drwxr-xr-x  5 zer0d zer0d 4096 2006-04-01 15:49 WoW
root@zer0d:~/.cedega# updatedb
root@zer0d:~/.cedega# locate .TransGaming
root@zer0d:~/.cedega# locate "Dot TransGaming"


```

---

### Post by pirast on 2006-04-01
sorry.. I do not know what to do then.. :-| 

n8,
martin

---

### Post by Zer0d on 2006-04-01
hehe ;) I'll just keep on trying ;)

---

### Post by Zer0d on 2006-04-01
```
root@zer0d:~/Desktop# glxgears -iacknowledgethatthistoolisnotabenchmark
19469 frames in 5.0 seconds = 3893.627 FPS
19474 frames in 5.0 seconds = 3894.683 FPS
19476 frames in 5.0 seconds = 3895.145 FPS
19477 frames in 5.0 seconds = 3895.349 FPS
19482 frames in 5.0 seconds = 3896.226 FPS
19477 frames in 5.0 seconds = 3895.335 FPS
19483 frames in 5.0 seconds = 3896.510 FPS
19480 frames in 5.0 seconds = 3895.926 FPS
19476 frames in 5.0 seconds = 3895.091 FPS
19481 frames in 5.0 seconds = 3896.141 FPS
19476 frames in 5.0 seconds = 3895.023 FPS
```

Does this show that the Graphic Card is installed right? :P Nvidia Geforce 6600...

---

### Post by dragge on 2006-04-02
I'm using latest cvs Wine 0.9.10.
I heard on the Gentoo forums that 0.9.11 are on its way with a nice patch to it to increase gaming performance on most games (directx patch).
Ill perhaps wait for that one.

> Sujet : WineD3D: Do not set the mipmap level count for old
textures

The attached patch stops WineD3D from re-setting the GL_TEXTURE_MAX_LEVEL
texture parameter every time a texture is used. It is not necessary, as the
max level is a property of the texture and not the active unit(according to
Lionel Ulmer). Setting the maximum level causes the 3d driver to dirtify the
texture in the video memory, which has to be reloaded then every time it is
used.

This patch should greatly increase the performance of most games. (I noticed
an fps improvement of a factor of 5)

Changelog:
Stefan Dösinger: Do not set the mipmap level count every time a texture is
used.

This is not yet applied to the cvs tree.

-------

Still, i cant seem to locate my problem, i still got around 20fps in westfall with my alt. When running under windows, i get 70fps~.
If i had gotten around 40-50fps under linux my win partition would have been long gone by now. :/

---

### Post by Zer0d on 2006-04-02
Good news :)

---

### Post by clarke.rainey on 2006-06-07
Well I am running WoW in the newest version of wine using the guide on the forums... I get with everything turned to max and at 1920X1200

between 25 and 30 fps... nvr higher or lower...

6800GTX 256MB
Dapper
P4 3.2 EMT64

back in the day in cedega my fps would go over 30 and be around 60ish... it is playable to 30... I am just confused and would like to fix it...
oh I am runningin Opengl...

---

