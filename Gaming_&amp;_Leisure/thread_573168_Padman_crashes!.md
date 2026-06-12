---
title: "Padman crashes!"
date: 2007-10-11
forum: Gaming &amp; Leisure
---

### Post by s_spiff on 2007-10-11
I downloaded the .run for WOP and installed it. Now everytime i run the game, under default settings, it crashes. I've tried hosting a local server with bots, and it rreachs the point untill the 'Loading' is complete.. and then everything blacks out and I'm back to my Desktop.
Can someone please tell me what I should do about this?

I'm running a AMD x64 System, with NVidia GeForce 6100 onboard graphic card, 1 gb RAM and Compiz-Fusion installed on Feisty.

---

### Post by cyrsan on 2007-10-11
Does the console contain any kind of error message after the crash?

---

### Post by Perfect Storm on 2007-10-11
Which resolution do you run your Desktop in? If World of padman doesn't have that resolution you have to add it to its .ini file.

As cyrsan said, we need the output of WOP

---

### Post by s_spiff on 2007-10-12
My desktop is at 1280x1204 and i run padman at 1024x786 full screen. Btw when I run wop in the terminal, i get the error ' command not found' so i launch the game from its folder, which words only if i double click by mouse, doesnt work via terminal either!!! i'm gonna try using sudo sh worldofpadman.run , hopefully that'll get it to work ! :( Last time i had just run it without sudo. Mebbe thats the issue?

Btw, since i cant run it from a CLI, i dont get to see what the error output is :(.

EDIt: running it thru the terminal using sudo resulted in this, I think this error was there the last time too, only the 'k' in the errors made me think that its prolly something to do with KDE... oh well don't ask.. i know i'm an idiot, anyways, can someone tell me whats the issue?

```

spiff@spiffed:~/Setups/Games$ sudo sh wop
sh: Can't open wop
spiff@spiffed:~/Setups/Games$ sudo sh worldofpadman.run 
Verifying archive integrity... All good.
Uncompressing World of Padman 1.1-final..........................................................................................................................................................................
Warning: kbuildsycoca is unable to register with DCOP.
kbuildsycoca running...
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
kio (KSycoca): ERROR: No database available!
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
spiff@spiffed:~/Setups/Games$ 


```

---

### Post by s_spiff on 2007-10-12
*bump* anyone?

---

### Post by gypsumwolf on 2008-04-06
WoP crashes for me if I try to create with bots; but when  create without bots the game runs fine. Maybe a bad download? Are there any torrents or md5 sums or hash checkers...?

---

### Post by aschueler on 2008-07-12
I have the same crash.

Hopefully I can resurrect this thread.  Anyway, here is what happens when run from command line:
    (I snipped a lot of extra stuff from above)

[SIZE="3"][FONT="Arial"]CL_InitCGame: 11.82 seconds
632 msec to draw all images
Com_TouchMemory: 0 msec
PadPlayer^7 entered the game
Received signal 11, exiting...
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
----- Server Shutdown (Signal caught) -----
==== ShutdownGame ====
AAS shutdown.
---------------------------
Shutdown tty console
aschueler@Frankenputer:~/games/Wop/Wop$
[/FONT][/SIZE]

Any idears?  Oh, it only happens with bots.  As you can see above, it happens right when "PadPlayer^7 entered game" shows up.

---

