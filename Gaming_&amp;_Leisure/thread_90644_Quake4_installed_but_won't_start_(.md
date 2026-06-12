---
title: "Quake4 installed but won't start :("
date: 2005-11-15
forum: Gaming &amp; Leisure
---

### Post by nolan- on 2005-11-15
Hi everyone,
I am new to Kubuntu and have limited Linux experience so go easy :)

OK I have installed Quake4 and copied pak files etc into the q4base dir and when i open a terminal in the q4 dir and type "quake4" it gives "command not found". 
I guessed at "sh quake4" and i get an error :-

"./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory"

Now i have read other posts and the Quake4 GNU/Linux FAQ from ID and have only installed libsdl1.2debian and libsdl1.2debian-oss. 

So i'm kinda stuck, especially since Doom3 is a very similar install and it works by just clicking on the doom3 shell script icon in the install dir?

HELP !      Thanks...

---

### Post by daller on 2005-12-01
Try installing this package:

libsdl1.2-dev

---

### Post by Laterix on 2006-01-10
> 
libsdl1.2debian and libsdl1.2debian-oss.

I have only these two and it works just fine. At least demo version.

---

### Post by defuseme2k on 2006-01-10
yeah q4 works, took some screwing around with downloading the i386 versions of those files, and updating ld.so.conf and running ldconfig.  However alsa sounds like pure shit, but the one thing I haven't tried is libsdl1.2.dev which is most likely graphics stuff?  I thought the sdl side of it was for the nvidia side of things.

---

### Post by Deker on 2006-02-08
I had the same problem.  Solution for me was to add the following to your command.

quake4 +set s_driver oss

or, create a quick launch icon and add +ser s_driver oss in the executable box

hope this helps :)

---

### Post by mthaddon on 2006-02-19
I've tried installing libsdl1.2-dev and also the quake4-demo +set s_driver oss option.

No joy on either. Is there anything else I can try?

---

### Post by TasKiNG on 2006-03-01
Check this out [http://www.lucentplum.com/?p=16](http://www.lucentplum.com/?p=16)

it worked for me :) Now got Quake4 running on Dapper Drake. Much smoother than XP

Note: when you unpack to /tmp for some reason your /tmp directory permissions are changed preventing xwindows starting next time you log on. So before you log off type:-              sudo chmod 777 /tmp

Cheers

TasKiNG

---

### Post by R3linquish3r on 2006-03-03
You need to install the PATCH. It will install the rest of the necessary files you need to run. Just extracting the pk4 files from the CD gives you the shell of the game. Sorry but I'm leaving for school so I don't have time to find you a link for it.....

Also, when you install the patch you need to launch the game using "sudo quake4" in the console. It's got screwy permissions :P. If you try just using "quake4" in the console or launching fom a shortcut it resizes your screeen res so you can't see and the game won't start. Joy for me to figure that one out :P

---

### Post by Tosa on 2006-03-10
Well, I have a problem too, but no solution so far.

Quake4 worked fine on my mashine, but some time ago, all of a sudden it stoped working. When I start it I get black screen for a few seconds and the it closes and that's it.

When I ran it in terminal I got these:
....
[COLOR="RoyalBlue"]execing default.cfg
"ALT" isn't a valid key
"CTRL" isn't a valid key
couldn't exec editor.cfg
execing Quake4Config.cfg
couldn't exec autoexec.cfg[/COLOR]
....
[COLOR="RoyalBlue"]------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, d
on't bother.
/dev/dsp - bit rate: 16, channels: 6, frequency: 44100
allocated a mix buffer of 49152 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
--------------------------------------[/COLOR]

and at the and

[COLOR="RoyalBlue"]found DLL in pak file: /home/gazda/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/gazda/.quake4/q4base/gamex86.so
signal caught: Segmentation fault
si_code 2
Trying to exit gracefully..
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
Shutting down SDL subsystem
/home/gazda/bin/quake4: line 6: 10424 Segmentation fault      ./quake4.x86 $*[/COLOR]

Any ideas what went wrong?

---

### Post by mogelhead on 2006-06-20
[QUOTE=nolan-]
"./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory"
[/QUOTE]

I'm using Kubuntu Dapper (6.06) for amd64 and I had the exact same error message when trying to start the Quake4 demo. Are you also using amd64? In that case you can try installing the **ia32-libs-sdl** package. It solved the problem for me. Comments for the package displayed in Adept:
[INDENT]"This package contains runtime libraries for the ia32/i386 architecture, configured for use on an amd64 or ia64 Ubuntu system running a 64-bit kernel. These are packages related to sdl. Commercial games like Quake4 are known to work with this package installed"[/INDENT]

---

### Post by mixim on 2006-06-20
I Got the game running fine with the guide, but only with Low (maybe less,) quality... I can set it to high or ultra and it stays that way in the settings, but well in the game i can clearly see the textures beeing really really crappy as if it stayed in Low...

What could be wrong?

// And yeeeh, i've got the latest everything... Patches, drivers etc...

---

