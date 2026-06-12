---
title: "Urban Terror Resolution problem (not able to open game)"
date: 2008-04-18
forum: Gaming &amp; Leisure
---

### Post by hullap on 2008-04-18
Hi, im new here and this is my first post
the problem this that im not able to even open UrT
 ](*,)
when i run it from the terminal i get this ```
hullap@hullap:~$ /home/hullap/UrbanTerror/ioUrbanTerror.i386
ioQ3 1.35urt linux-i386 Dec 20 2007
----- FS_Startup -----
Going through search path...

----------------------
8042 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode -1: 1600 1024
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x1a5
  Serial number of failed request:  137
  Current serial number in output stream:  139
hullap@hullap:~$ 

```
even after deleting the q3config file i get the same result
pls help

 
Thnx,
hullap

---

### Post by Perfect Storm on 2008-04-18
Which card do you have?

---

### Post by hullap on 2008-04-18
actually the gme was working previously, by mistake i change the resolution to 1600X1280
i have NVIDIA 7100GS gfx card

---

### Post by Perfect Storm on 2008-04-18
Where did you cange the resolution in the game or in the xorg.conf?

---

### Post by Rhubarb on 2008-04-18
You need to delete the q3config file relating to q3ut4:
```
rm /home/hullap/.q3a/q3ut4/q3config.cfg
```

Or just delete your /home/hullap/.q3a directory

---

### Post by Perfect Storm on 2008-04-18
if it's the config file of the game  - just edit it and change it to prefer resolution.

---

### Post by hullap on 2008-04-18
> **Rhubarb said:**
> You need to delete the q3config file relating to q3ut4:
```
rm /home/hullap/.q3a/q3ut4/q3config.cfg
```

Or just delete your /home/hullap/.q3a directory
thnx dude,
this worked

BTW Artificial Intelligence pls close this thread, as my problem is solved

---

### Post by Perfect Storm on 2008-04-18
We don't close threads, as there might be other who some day may have the same problem.

---

### Post by hullap on 2008-04-18
fine.
as im new here i didnt know

---

### Post by Trinidado on 2008-04-18
Thank-you so much for this thread! I have had the same problem for a couple months now! This fixed it.

Thanks again!

---

### Post by Kane_of_NOD on 2008-05-17
Hello,

I did delete the file, and I'm still with the same problem

When i click to start the game, my screen goes black and comes a message: 


ATTENTION

CANNOT DISPLAY THIS VIDEO MODE, CHANGE COMPUTER DISPLAY INPUT TO 1280x1024@60Hz



What should  I do?

My monitor is a Philips 170C  17"
My graphic card is : Gforce 6200LE

Ubuntu 8.04
1.5Gb RAM
1.8Ghz AMD's CPU

All drivers are installed and running (I got Compiz working fast and fine)



Help please!

---

### Post by max-k on 2008-07-14
Hello, to solve your problem, you must edit the file located in ~/.urbanterror/q3ut4/q3config.cfg and edit the following lines :

seta r_mode "-1"
seta r_customwidth "1280"
seta r_customheight "1024"

save and enjoy !

You can modify the config via the setup menu to set the resolution to 1280x1024 now but it can works well with this config.

P.S : It works with all resolutions, standard or wide screens.

Bye

---

### Post by akadruid on 2008-11-09
Thanks very much!

After I upgraded 8.04 -> 8.10, I could not start UT, just got flickry lines across the screen.

I had:
```
seta r_mode "6"
```
I changed it to to:
```
seta r_mode "-1"
```
worked fine for me.

Out of curiosity, what does r_mode control?

Thanks

aka

---

### Post by Gen2ly on 2009-02-17
thanks max-k r_mode to -1 did it for me too.  Also you can change to windowed-mode with Alt+Enter.

---

### Post by whistlerspa on 2009-06-06
I read another post that said to delete the *.cfg file so I tried that - to no avail. Then I read this post and tried to reinstall the game from the zip file so that i could try these ideas. This time and once more after the *.cfg file was not created and I'm wondering why. 

However the alt + Enter thing worked so thanks for that.

---

