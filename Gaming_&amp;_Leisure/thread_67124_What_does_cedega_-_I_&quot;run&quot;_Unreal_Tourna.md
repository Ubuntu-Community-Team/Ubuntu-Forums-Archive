---
title: "What does cedega??? - I &quot;run&quot; Unreal Tournament without it!"
date: 2005-09-19
forum: Gaming &amp; Leisure
---

### Post by daller on 2005-09-19
Hi All,

What does cedega??? - And how is it activated?

Running UT with cedega freaks:

killall kicker;cedega "/home/daniel/.wine/drive_c/UnrealTournament/System/UnrealTournament.exe";kicker

...The display is blank, but I can hear the intro sound playing! (Used Ctrl+Alt+ESC to exit - no other way!!!)

I run UT directly with Wine, I run it in OpenGL mode, with the 840x525 resolution... (Can't run any higher - but I have a 1680x1050 LCD display)

The command: killall kicker;wine "/home/daniel/.wine/drive_c/UnrealTournament/System/UnrealTournament.exe";kicker

...not killing kicker makes it appear in the bottom of the screen - even in fullscreen!

The gameplay is way to fast - guess a higher resolution will fix that!

"Quake III Arena" and "Counter Strike" starts windowed, and i can't get the cursor into the window, entering the border of the window, the cursor zeroes (50%,50% - the middle of the screen)
Also there is no sound in Quake III Arena (The intro)
When entering Quake III Arena, this errormessage is displayed:

It is highly unlikely that a correct windowed display can be initialized with the current desktop display depth. Select OK to try anyway. Press CANCEL if you have a 3Dfx Voodoo, Voodoo 2, or Voodoo Rush 3D accelerator installed, or if you otherwise like to quit!

Any suggestions? (Getting UT to work is definately TOP PRIORITY!!!)

This is my system:

Centrino 1300 MHz
256 MB ram
Nvidia Ti 4200 Go

daniel@dallap:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
14077 frames in 5.0 seconds = 2815.384 FPS
14209 frames in 5.0 seconds = 2841.677 FPS
14206 frames in 5.0 seconds = 2841.167 FPS
14184 frames in 5.0 seconds = 2836.664 FPS
14156 frames in 5.0 seconds = 2831.062 FPS
14028 frames in 5.0 seconds = 2805.493 FPS
14200 frames in 5.0 seconds = 2839.873 FPS
14172 frames in 5.0 seconds = 2834.213 FPS

---

### Post by Harleen on 2005-09-19
Why don't you use the native Linux versions for UT and Quake III? They should run with less trouble than using an emulator.

UT:
[http://liflg.org/?catid=6&gameid=51](http://liflg.org/?catid=6&gameid=51)

QIII:
[ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run](ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run)

---

### Post by daller on 2005-09-19
Thanks, I'll try to get it running!

Is there any other cool games, available like that?

Commandos 3?
Hitman (2)?
Serious Sam?
Disciples 2?
Max Payne?
Battlefield 1942?

---

### Post by daller on 2005-09-19
Running UT now:

[email]daniel@dallap:~/.ut[/email]$ sh ut
Signal: SIGIOT [iot trap]
Aborting.

What does that mean?

---

### Post by daller on 2005-09-19
Think I found the problem: (ran the sh command, writing the output to a logfile)

LOG..............

Gdk-WARNING **: locale not supported by Xlib, locale set to C
chdir(push: /home/daniel/ut): No such file or directory
Could not write uninstall script: /home/daniel/ut/uninstall
Loki Patch Tools 1.0.2
Usage: ./setup.data/bin/Linux/x86/loki_patch [--info] patch-file [install-path]
daniel@dallap:~/downloads$ sh unreal.tournament_436-multilanguage.run > log_ut

Gdk-WARNING **: locale not supported by Xlib, locale set to C
chdir(push: /home/daniel/ut): No such file or directory
Could not write uninstall script: /home/daniel/ut/uninstall
Loki Patch Tools 1.0.2
Usage: ./setup.data/bin/Linux/x86/loki_patch [--info] patch-file [install-path]
daniel@dallap:~/downloads$ sh unreal.tournament_436-multilanguage.run > log_ut

Gdk-WARNING **: locale not supported by Xlib, locale set to C
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: 'kdevjavadebugger.desktop' specifies undefined mimetype/servicetype 'KDevelop/Part'
kbuildsycoca: WARNING: 'gvimagepart.desktop' specifies undefined mimetype/servicetype 'image/x-krl'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-math.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.math'
kbuildsycoca: WARNING: '/usr/share/applications/kde/konversation.desktop' specifies undefined mimetype/servicetype 'DCOP/InstantMessenger;DCOP/Unique'
kbuildsycoca: WARNING: 'kfile_ooo.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: 'kfile_ooo.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.math'
kbuildsycoca: WARNING: '/usr/share/applications/firefox.desktop' specifies undefined mimetype/servicetype 'application/rss+xml'
kbuildsycoca: WARNING: '/usr/share/applications/firefox.desktop' specifies undefined mimetype/servicetype 'application/rdf+xml'
kbuildsycoca: WARNING: '/usr/share/applications/firefox.desktop' specifies undefined mimetype/servicetype 'x-directory/webdav'
kbuildsycoca: WARNING: '/usr/share/applications/firefox.desktop' specifies undefined mimetype/servicetype 'x-directory/webdav-prefer-directory'
kbuildsycoca: WARNING: '/usr/share/applications/wine.desktop' specifies undefined mimetype/servicetype 'application/x-ms-dos-executable'
kbuildsycoca: WARNING: '/usr/share/applications/wine.desktop' specifies undefined mimetype/servicetype 'application/x-msdownload'
kbuildsycoca: WARNING: '/usr/share/applications/wine.desktop' specifies undefined mimetype/servicetype 'application/exe'
kbuildsycoca: WARNING: '/usr/share/applications/wine.desktop' specifies undefined mimetype/servicetype 'application/x-exe'
kbuildsycoca: WARNING: '/usr/share/applications/wine.desktop' specifies undefined mimetype/servicetype 'application/dos-exe'
kbuildsycoca: WARNING: '/usr/share/applications/wine.desktop' specifies undefined mimetype/servicetype 'vms/exe'
kbuildsycoca: WARNING: '/usr/share/applications/wine.desktop' specifies undefined mimetype/servicetype 'application/x-winexe'
kbuildsycoca: WARNING: '/usr/share/applications/wine.desktop' specifies undefined mimetype/servicetype 'application/msdos-windows'
kbuildsycoca: WARNING: '/usr/share/applications/wine.desktop' specifies undefined mimetype/servicetype 'application/x-zip-compressed'
kbuildsycoca: WARNING: 'overview.desktop' specifies undefined mimetype/servicetype 'KitchenSync/ActionPart'
kbuildsycoca: WARNING: '/usr/share/applications/kde/kmymoney2.desktop' specifies undefined mimetype/servicetype 'application/vnd.intu.qfx'
kbuildsycoca: WARNING: '/usr/share/applications/kde/kmymoney2.desktop' specifies undefined mimetype/servicetype 'application/x-ofx'
kbuildsycoca: WARNING: 'qeditor_part.desktop' specifies undefined mimetype/servicetype 'text/english'
kbuildsycoca: WARNING: 'qeditor_part.desktop' specifies undefined mimetype/servicetype 'text/x-c'
kbuildsycoca: WARNING: 'qeditor_part.desktop' specifies undefined mimetype/servicetype 'text/x-c++'
kbuildsycoca: WARNING: 'qeditor_part.desktop' specifies undefined mimetype/servicetype 'text/x-sql'
kbuildsycoca: WARNING: '/usr/share/applications/kde/amarok.desktop' specifies undefined mimetype/servicetype 'audio/x-sid'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'KMediaPart'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'audio/x-ogg'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-realaudio-plugin'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'video/msvideo'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'video/x-avi'
kbuildsycoca: WARNING: 'gstreamer_part.desktop' specifies undefined mimetype/servicetype 'video/x-fli'
kbuildsycoca: WARNING: 'kcertpart.desktop' specifies undefined mimetype/servicetype 'application/binary-certificate'
kbuildsycoca: WARNING: '/home/daniel/.local/share/applications/kde-kaffeine.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/home/daniel/.local/share/applications/kde-kaffeine.desktop' specifies undefined mimetype/servicetype 'audio/x-ogg'
kbuildsycoca: WARNING: '/home/daniel/.local/share/applications/kde-kaffeine.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-realaudio-plugin'
kbuildsycoca: WARNING: '/home/daniel/.local/share/applications/kde-kaffeine.desktop' specifies undefined mimetype/servicetype 'video/msvideo'
kbuildsycoca: WARNING: '/home/daniel/.local/share/applications/kde-kaffeine.desktop' specifies undefined mimetype/servicetype 'video/x-avi'
kbuildsycoca: WARNING: '/home/daniel/.local/share/applications/kde-kaffeine.desktop' specifies undefined mimetype/servicetype 'video/x-fli'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'KMediaPart'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'audio/x-ogg'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-realaudio-plugin'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'video/msvideo'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'video/x-avi'
kbuildsycoca: WARNING: 'kaffeine_part.desktop' specifies undefined mimetype/servicetype 'video/x-fli'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/g3fax'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/jpg'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-compressed-xcf'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-fits'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-gray'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-portable-anymap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-portable-graymap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-psd'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-sgi'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-sun-raster'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-tga'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xbitmap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xcf'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xpixmap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xwindowdump'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-impress.desktop' specifies undefined mimetype/servicetype 'application/vnd.ms-powerpoint'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefined mimetype/servicetype 'audio/wav'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefined mimetype/servicetype 'audio/mp3'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/blender.desktop' specifies undefined mimetype/servicetype 'application/x-blender'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.oasis.opendocument.text-web'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.oasis.opendocument.text-master'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-writer.desktop' specifies undefined mimetype/servicetype 'application/x-doc'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.wordperfect'
kbuildsycoca: WARNING: 'knotify.desktop' specifies undefined mimetype/servicetype 'KNotify'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-base.desktop' specifies undefined mimetype/servicetype 'application/vnd.oasis.opendocument.database'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-base.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.base'
kbuildsycoca: WARNING: '/usr/share/applications/kde/showfoto.desktop' specifies undefined mimetype/servicetype 'image/x-psd'
kbuildsycoca: WARNING: '/usr/share/applications/kde/showfoto.desktop' specifies undefined mimetype/servicetype 'image/x-eim'
sh: /home/daniel/ut: is a directory
daniel@dallap:~/downloads$               

----------------------

I have the "Game of the year edition" of the game! - does that cause the errors?

---

### Post by daller on 2005-09-19
Q3 runs now- but without sound! - How do I fix that?

---

### Post by daller on 2005-09-19
...also the game starts with a black border around it (im having a 1680x1050 display) - Is there a way to enable wide screen?

A friend told me that this could be edited in an autoexec-file - but where is this file located, and what do I have to edit?

EDIT: A reboot made the sound work!!!

---

### Post by daller on 2005-09-23
Found a linux-installer on happypenguin.org...

...now everything works, and I don't need wine or cedega!!!

---

### Post by Mishura on 2005-09-23
[QUOTE=daller]Thanks, I'll try to get it running!

Is there any other cool games, available like that?

Commandos 3?
Hitman (2)?
Serious Sam?
Disciples 2?
Max Payne?
Battlefield 1942?[/QUOTE]

Commandos 3 - Never heard of it.
Hitman (2) - I hear Hitman 1 can work in Cedega.  Give that a try.
Serious Sam - Both First and Second Encounters have (beta) linux versions.  They're hard to find, do a search for "Serious Sam Linux" in Google.
Disciples 2 - Linux port in progress.  Windows version works in Cedega according to [http://digital-conquest.ath.cx/wiki/index.php/Main_Page](http://digital-conquest.ath.cx/wiki/index.php/Main_Page)
Max Payne - Cedega supported.
Battlefield 1942 - Cedega supported.  Don't bother with punkbuster servers.  They don't work.  When you can ever find a non-punkbuster server, you can play there.. or Single player.

---

### Post by BLTicklemonster on 2005-10-07
[QUOTE=daller]Found a linux-installer on happypenguin.org...

...now everything works, and I don't need wine or cedega!!![/QUOTE]


Wow, gnice. I got it, too. Gnow what?

This is my first time trying to do this. I have tried several different versions of linux, all the way from slackware to redhat to mandrake, et al, and gnever liked them solely because I don't wish to be bothered with the command line. Ever. If I want to type, I open my script editor, and work on UT mods or hack helios bots to see how to mess them up online. If I want to install something, I click on an icon. That's the extent of my desire to have to do anything in an operating system. I'm a hard head about it. Operating systems are to operate from, not write code. Why gno one has created a DOS version that will run ... gnever mind, I'm going to alienate people here.

SO.... Being a gnubie, I am lost as to what I am to do to get Unreal Tournament to run. 

IMHO, all sites should remember that they are visible to people who have gno clue (me), and that telling people like me  stuff like, 

> 
frequently asked questions

How to use the installer?
Type following commands in a shell:
sh installer.run
or
chmod +x installer.run
./installer.run

How to use the installer on 64 bits CPUs?
You will need the linux32 tool([ftp://ftp.x86-64.org/pub/linux/tools/linux32/)](ftp://ftp.x86-64.org/pub/linux/tools/linux32/)).
Type following commands in a shell:
linux32 sh installer.run
or
chmod +x installer.run
linux32 ./installer.run

Besides the installer, what else do I need to install my game?
Most of our installers, especially the wine(x) installers, will ask you for the cds or dvd of the game. So you will need the original discs the game came on.

The installer does not find the CD!
First try to export the CD-ROM environment variable: (Especially for auto/supermount users e.g. Mandrake).
export SETUP_CDROM=/path/to/your/mounted/cdrom


is basically like saying... well, that up there, which is total gnibberish to people like me. 

so, keeping in mind that I am a total idiot, please someone help me understand what I am to do now that I have a .run file on my desktop that gneeds to be installed. 

How (like I really want to know, but gneed to, apparently, if I'm going to ever migrate away from Windows) do I get these things to work? Am I going to have to chisel my own wheel every time I want to go for a ride, or will Ubuntu remember what to do? Why doesn't it already know what to do? How hard would it be for it to be programmed to in the first place?

I would like to, however, congratulate the Ubuntu folks for creating this fine OS. You got me up and running without having to manually install anything whatsoever, and I'm online without having to use a wizard. Very impressive. I am looking forward to removing windows from all the machines here at the house, and turning other peple on to this.

( Gnow, once I am lead by the nose into knowing how to execute files, I want to know what I can use to burn dvds/cds? Does dvdshrink work? how do I play dvds?, etc.)

Thank you, and I hope I haven't alienated anyone, or anything like that. I'm just frustrated at every turn when it comes to linux.


Have a gnice day.


(oh, for you UT folks, 67.19.84.40 is our server, The Black Legion Zark Weapons Server. Stop by some time!)

---

### Post by DutchLau on 2005-10-07
Are you serious? You have to at least make an effort to try installing stuff. Your quote explains exactly how you must install and run UT. Try it. Opening a shell = open up a terminal.

---

### Post by BLTicklemonster on 2005-10-07
Okay. Shell. Open. Sorry, I'm in the mountains, no shells up here, and it's relevance to terminals is irrelevant to me. I found the terminal, and I get an error.


Honestly, YOU know what open a shell means, and glibbly just toss it out there like everyone knows what it means. I on the other hand have no earthly idea what open a shell means. I have downloaded linux for dummies. Useless to me. What does open a shell equate to in normal speak? Where is this mysterious shell you speak of? And if you say you open it from the command line, I'm going to hunt you down! J/k, no really, I don't know a shell from a command line from a .. what was it I stumbled across earlier? Oh, Synaptic Package Manager. Nice little thing, makes now sense to me. 

Sorry, but hey, I'm totally new to all this. And to state that I have to at least make an effort is way out of line. An effort has been made all day. Efforts out the wazzooo. More efforts than you can shake a stick at. But nothing makes sense to me. There is no site or reference that I can find anywhere that even remotely hints at how to get from point a to point b. I'm eager to learn, but I need some direction, not comments. 

But thanks for taking the time to belittle me, I miss my first wife something terrible, and now I have that warm cozy feeling again.

again, j/k. I don't miss that swine at all!

So, ah, can you be of assistance if I ask nicely?
'

Huh. I just read that and I don't like my tone of voice, so let me go at it this way:

Where do I download the files to? I'm not as familiar with this file structure as I am with windows, so instead of 

sh installer.run

I imagine I put sh pathto\rile.run right?

maybe?

---

### Post by BLTicklemonster on 2005-10-07
> sh -ihb unreal.tournament_436-multilanguage.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage Installer...................................................................................
/home/ticklemonster/.setup8986: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory



Got that far each time. I put -ihb because the guide for people like me (dummies) made some vague reference to it installing stuff. 

Now what?

---

### Post by BLTicklemonster on 2005-10-07
... went back to synaptic package thing... chose all the libgtk packages that it showed not on the computer, got them installed, then went to the terminal, sh unreal.tournament_436-multilanguage.run and it installed. Said to type ut to play. So I did. And it says this:

Signal: SIGIOT [iot trap]
Aborting.


Nice, eh?

Um, where is ut? I can't find it to see if the editor will work, or to see what files are there, or if uccmake works or anything.


*edit: okay, got the bonus pack installed now, too. Had to use the synaptic thing again for some stuff, can't remember what it was now. But I can't play it, I still get the above error. I'm gonna get this one way or another.

---

### Post by online14230 on 2005-10-08
Hey there tickle!!
I hear you!!!

I asked a guy for help with IrDA earlier and I was told to add something to the kernel and recompile it.  ?!?!?!
Im just as much a newbie as you are .. even more. See, I know you have to use wine as an emulator. I d/loaded it but now what? My Ubuntu machine isnt online(no netcard) yet, so I have to do all this manually. I tried telling this to one of the guys and all he did was send me a link. Checked it out and it tells me to tar this and make that .. ?? huh? Ive just gotten the OS installed! Gee!! Its a VERY first for me. Seems these people arent too helpful here. Maybe switching to Impi or some other distro is the best for me.. at least I ll get some help that Ill understand. I dont speak geekese yet so maybe switching to a distro where I can get some english help is the answer for me. Have fun here: I dont intend staying long.

---

### Post by BLTicklemonster on 2005-10-08
No no no, don't rush off. We may be able to help one another if these folks won't. Besides if we do, imagine how embarassing it would be to them for some newbies to come in here and help themselves.

We can beat it, it's just going to take some time.

First thing I'd do is find a nic to put in that machine!


(Every forum I go to, I use the name Ticklemonster, or BLTicklemonster. And at every forum, someone calls me Tickle, which is what the UT community calls me. Now are these people from the UT community, or is Tickle just easier to say than Monster?)

---

### Post by BLTicklemonster on 2005-10-08
Copying UT files (the maps on my machine are still compressed) from one of the other computers on my network to my machine and I'll see if it plays then.

I got a bit further by going like this:

Applications>System Tools>Terminal 

and typing:

cd /home/ticklemonster/ut/System

then typing

./ut-bin -log

and it told me that it couldn't find entry.

(that up there is what the site admins want people who post here to do. read the stickys, old timers) :razz:

---

### Post by shawn on 2005-10-08
@BLTicklemonster - I understand your pain hehe. See if this helps you:

1 - right click on the .bin file on your desktop

2 - choose properties

3 - look for permission settings, they are in there somewhere

4 - click all three checkboxes that say 'Execute'

5 - click OK

6 - Double click the .bin file on your desktop

I hope that should start installing. What that does is make the file executable for all users, which means you will be able to run it. This does the same as 'chmod a+x' in a terminal but its easier.

@online14230 - I'm almost 100% certain that Ubuntu has one of the most helpful communities behind it possible, and I am sorry you don't seem to see it like that. I can tell you now for nothing, go over to another Distro's forums and ask questions like these and you are almost guaranteed the resopnse "RTFM" - I know cos I have been there.

@both of you - there is a lot to learn and get used to and some people will assume you have a basic knowledge of linux. If you don't understand something all you need to do is ask and the answer will come eventually.

So, I advise you both to look through these links if you have not already:

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)  - will help you set ubuntu up to do all windows can do and more.

[http://linuxshop.ru/linuxbegin/win-lin-soft-en/table.shtml](http://linuxshop.ru/linuxbegin/win-lin-soft-en/table.shtml)  - if you used software in Windows and need a linux alternative look here.

[http://www.ubuntuforums.org/forumdisplay.php?f=73](http://www.ubuntuforums.org/forumdisplay.php?f=73)  - Ubuntu forums absolute begginer talk. If you want to know what a shell is, or what tar means ask in here.

I hope this didn't come accross as patronising, I am trying to help. One last piece of advice - don't bite the hand that feeds you. If you give someone stick because YOU lack basic knowledge of the linux OS they will be reluctant to help you in the future. These people are helping you with their free time, appreciate it.

---

### Post by BLTicklemonster on 2005-10-08
Copying the maps got me almost there, then this happened:

> ticklemonster@ubuntumonster:~/ut/System$ ./ut-bin -log
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Bound to Fire.so
Case-insensitive search: Botpack -> ..\System\BotPack.u
Bound to IpDrv.so
Game class is 'UTIntro'
Level is Level Entry.MyLevel
Bringing Level Entry.MyLevel up for play (0)...
InitGame:
Base Mutator is Entry.Mutator0
Browse: CityIntro.unr?Name={BL}Ticklemonster?Class=Botpack.TMale2?team=255?skin=SoldierSkins.blkt?Face=SoldierSkins.Othello
LoadMap: CityIntro.unr?Name={BL}Ticklemonster?Class=Botpack.TMale2?team=255?skin=SoldierSkins.blkt?Face=SoldierSkins.Othello
Case-insensitive search: genfluid -> ..\Textures\GenFluid.utx
Collecting garbage
Purging garbage
-0.0ms Unloading: Package Render
Garbage: objects: 16409->16408; refs: 224522
Game class is 'UTIntro'
Level is Level CityIntro.MyLevel
Bringing Level CityIntro.MyLevel up for play (0)...
InitGame: ?Name={BL}Ticklemonster?Class=Botpack.TMale2?team=255?skin=SoldierSkins.blkt?Face=SoldierSkins.Othello
Base Mutator is CityIntro.Mutator1
Initialized moving brush tracker for Level CityIntro.MyLevel
Created and initialized a new SDL viewport.
Bound to UWeb.so
Team 255
Login: {BL}Ticklemonster
Case-insensitive search: SoldierSkins -> ..\Textures\Soldierskins.utx
Possessed PlayerPawn: TMale2 CityIntro.TMale0
Input system initialized for SDLViewport0
Opening SDL viewport.
Bound to OpenGLDrv.so
Loaded render device class.
Initializing OpenGLDrv...
binding libGL.so.1
Resizing SDL viewport. X: 640 Y: 480
OpenGL
GL_VENDOR     : Mesa project: [www.mesa3d.org](www.mesa3d.org)
GL_RENDERER   : Mesa GLX Indirect
GL_VERSION    : 1.2 (1.5 Mesa 6.2.1)
GL_EXTENSIONS : GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays Device supports: GL
Device supports: GL_EXT_bgra
Device supports: GL_EXT_texture_env_combine
Device supports: GL_ARB_texture_env_combine
Device supports: GL_SGIS_texture_lod
Device supports: GL_EXT_texture_lod_bias
Device supports: GL_EXT_secondary_color
Device supports: GL_ARB_multitexture
8 Texture Mapping Units found
MinLogTextureSize = 2
MaxLogTextureSize = 8
Bound to ALAudio.so
fcntl: Operation not permitted
fcntl: Operation not permitted
OpenAL Audio subsystem initialized.
Game engine initialized
Startup time: 1.634242 seconds.
Entering main loop.
OpenGL Error: GL_INVALID_ENUM (please report this bug)
Signal: SIGSEGV [segmentation fault]
Aborting.
Exiting.
Name subsystem shut down
Allocation checking disabled
Segmentation fault
ticklemonster@ubuntumonster:~/ut/System$



Sez to report this bug, so here it is. ;)

Perhaps if I can remember how to change to d3d I can edit the ini file and try it like that... riiiight. lol

---

### Post by BLTicklemonster on 2005-10-08
Shawn, thanks for the help. I still can't get past that error. I'm installing it again, and going to try it again.

---

### Post by BLTicklemonster on 2005-10-10
I'm such a noob. I have nvidia drivers now. I just noticed that the author of this thread said that wine is used... koff koff so i'm downloading wine. I'll try ut with it. :)

---

### Post by BLTicklemonster on 2005-10-10
got wine... now how the heck do I get it to run with ut? Looked on the site, and it was sort of like non informative.

---

### Post by alvonsius on 2005-10-10
Forgive me not post this question in a new thread, coz i think its related. 

I'm curently trying to run Counter Strike from my Hoary with wine. It run well, but sometime before i get into the main menu, wine just stop responding and quit the games. And in another time it run safely until i come to the game (the part when i must choose my part as a terorrist or counter-terrorist), the wine stopped responding. Is there any settings that I missed or else, cz i got nothing in winehq and i read that Daller can play counter strike.

Thanks

---

### Post by seethru on 2005-10-10
By wine you mean cedega?
Theres not a heck of a lot you can do, I experience the lock up before the menu loads every now and then, however I've never experienced the lock up when getting in the game.
Do you have antialiasing turned on? Anisotropic filtering?
If yes, try turning them off, or just try turning down your graphics settings in general.

What are your system specs?

---

### Post by online14230 on 2005-10-10
First off, let me apologise for beeing an absolute (*%^*(*&!!
The thing is, Ive been trying for loooooong to get hoary installed and now that I do, all I can do is play the embedded games. Its pathetic. I cant even listen to music. Unluckily for me, I still have W98 on a spare HDD so I just slot it in to listen to music.
Anyway, I dloaded some codecs and now I have a problem: I cannot su to root.
It asks for a passsword but I dont have one. I NEVER supplied on and Im a bit confussed... I created a user with a password while installing, and I login using that. Any takers for that one??
B.
ps: When I try to play, it tells me it cant open location for writing .. this is after it pauses. I cant remember which program it uses, but as soon as I press play, it switches back to pause....

---

### Post by BLTicklemonster on 2005-10-10
[QUOTE=seethru]By wine you mean cedega?
Theres not a heck of a lot you can do, I experience the lock up before the menu loads every now and then, however I've never experienced the lock up when getting in the game.
Do you have antialiasing turned on? Anisotropic filtering?
If yes, try turning them off, or just try turning down your graphics settings in general.

What are your system specs?[/QUOTE]

Oooh, nice stuff, how do you get to the part where you can change all that stuff in graphics? And how does one run wine in the first place? Is there a script you must run? I looked at the wine site, and apparently any instructions were hidden in technobabble so efficiently that it totally escaped my attempts to find it. (why they do that, then give people a hard time about not using linux is kinda dumb. you see it here, too. )

---

### Post by seethru on 2005-10-10
[QUOTE=online14230]First off, let me apologise for beeing an absolute (*%^*(*&!!
The thing is, Ive been trying for loooooong to get hoary installed and now that I do, all I can do is play the embedded games. Its pathetic. I cant even listen to music. Unluckily for me, I still have W98 on a spare HDD so I just slot it in to listen to music.
Anyway, I dloaded some codecs and now I have a problem: I cannot su to root.
It asks for a passsword but I dont have one. I NEVER supplied on and Im a bit confussed... I created a user with a password while installing, and I login using that. Any takers for that one??
B.
ps: When I try to play, it tells me it cant open location for writing .. this is after it pauses. I cant remember which program it uses, but as soon as I press play, it switches back to pause....[/QUOTE]
sudo is the command you're looking for, this replaces su root in Ubuntu.

[QUOTE=BLTicklemonster]Oooh, nice stuff, how do you get to the part where you can change all that stuff in graphics? And how does one run wine in the first place? Is there a script you must run? I looked at the wine site, and apparently any instructions were hidden in technobabble so efficiently that it totally escaped my attempts to find it. (why they do that, then give people a hard time about not using linux is kinda dumb. you see it here, too. )[/QUOTE]
As for wine, Wine won't run most games because of directx, however Cedega aka WineX will, but costs money. You change the graphics settings inside the game.

To install wine do the following:

Open a terminal and type
```
sudo gedit /etc/apt/sources.list
```

Scroll to the bottom of that file and paste the following lines
```
# Wine
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/
```

Close the file and then in the terminal type the following
```
sudo apt-get update
```

Once that command is finished running type
```
sudo apt-get install wine
```

---

### Post by BLTicklemonster on 2005-10-10
I've already installed wine, but don't you have to run it in the background while UT is running? There's a fellow who comes to our server, and he uses linux, (utdc says so) and he plays very well, so I know it can be played on linux.

---

### Post by seethru on 2005-10-10
Unreal Tournament has a native client for Linux, theres no emulation needed.

Original UT (GOTY) [http://files.filefront.com/ut+install+436+GOTY/;1634336;;/fileinfo.html](http://files.filefront.com/ut+install+436+GOTY/;1634336;;/fileinfo.html)

UT 2003 [http://files.filefront.com/UT2003+Linux+v2225+Patch/;2127345;;/fileinfo.html](http://files.filefront.com/UT2003+Linux+v2225+Patch/;2127345;;/fileinfo.html)

UT 2004 [http://files.filefront.com/UT2004+Linux+Patch+v3355/;3815050;;/fileinfo.html](http://files.filefront.com/UT2004+Linux+Patch+v3355/;3815050;;/fileinfo.html)

---

### Post by shawn on 2005-10-10
online14230 - the root password is the same as your user password, that confused me when I first got Ubuntu running too. In Ubuntu when the root account needs to do something like install software you must use the 'sudo' command which means superuser do. It is a little safer this way as you can't log in as the root user and forget about it or make silly mistakes. The root account can mess with important files and the like, but your user account cannot. You could say the root account is a system administration account, and sudo lets you use the account without logging into it permanently.

As for your music problem, all I did to set Ubuntu of for multimedia use was use:

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

And all was well for me. Good luck!

---

### Post by BLTicklemonster on 2005-10-10
> **seethru]Unreal Tournament has a native client for Linux, theres no emulation needed.

Original UT (GOTY) [url]http://files.filefront.com/ut+install+436+GOTY/ said:**
> 

UT 2003 [http://files.filefront.com/UT2003+Linux+v2225+Patch/;2127345;;/fileinfo.html](http://files.filefront.com/UT2003+Linux+v2225+Patch/;2127345;;/fileinfo.html)

UT 2004 [http://files.filefront.com/UT2004+Linux+Patch+v3355/;3815050;;/fileinfo.html](http://files.filefront.com/UT2004+Linux+Patch+v3355/;3815050;;/fileinfo.html)


!!! Whoa! So the thing I downloaded from Loki ran at like 2 fps and the sound was totally wrong. This will take care of it? I'll try it tonight!!! Thanks seethru, you keep coming through for me!

---

### Post by BLTicklemonster on 2005-10-10
( I wonder how you ping a server? Bring up the terminal and  put ping 67.19.84.40 like you woule in cmd in winderz? )

---

### Post by seethru on 2005-10-10
[QUOTE=BLTicklemonster]( I wonder how you ping a server? Bring up the terminal and  put ping 67.19.84.40 like you woule in cmd in winderz? )[/QUOTE]

ping -c 5 google.com

-c is the number of times to send a ping, if you don't specify it will ping forever until you end the command.

---

### Post by BLTicklemonster on 2005-10-10
bill@ubuntumonster:~$ ping -c 5 67.19.84.40
PING 67.19.84.40 (67.19.84.40) 56(84) bytes of data.
64 bytes from 67.19.84.40: icmp_seq=1 ttl=111 time=37.5 ms
64 bytes from 67.19.84.40: icmp_seq=2 ttl=111 time=39.0 ms
64 bytes from 67.19.84.40: icmp_seq=3 ttl=111 time=36.4 ms
64 bytes from 67.19.84.40: icmp_seq=4 ttl=111 time=38.5 ms
64 bytes from 67.19.84.40: icmp_seq=5 ttl=111 time=36.6 ms

--- 67.19.84.40 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 36.435/37.637/39.037/1.020 ms
bill@ubuntumonster:~$


heh heh cool. thanks

---

### Post by BLTicklemonster on 2005-10-10
Blast. I have the new ut file. I have uninstalled the old ut, and rm -r ut from /usr/local directory. I try to install ut, and I get this:

no write permissions on the install directory.

Shouldn't that say "in" the install directo- no wait, that's not what has me upset...

WHY CAN'T I INSTALL IT? #-o

---

### Post by seethru on 2005-10-10
since it's installing in /usr/local, are you using sudo to run the install file?

---

### Post by BLTicklemonster on 2005-10-11
Yeah, it won't install any other way now.

---

### Post by BLTicklemonster on 2005-10-11
Wait a minute, that's where it's been installing all along. But at first it woud install with sh, it now installs only with sudo. (how you like the way I worded that?)

---

### Post by seethru on 2005-10-11
if a program is installing anywhere outside of your home directory you've always gotta use sudo.

---

### Post by BLTicklemonster on 2005-10-11
I wonder then, how can I force it to install elsewhere? I can possibly edit where it says to install, but I'd have to do it from sudo of course. If I did, and put it in home, then would I be free of having to run in root? If I dont' hear back by the time I get home, I'll try that and see.

---

### Post by seethru on 2005-10-11
you shouldn't have to run the actual program as root...just the install. I'll try to find my UT2k4 discs and see if I can reproduce what you're experiencing.

---

### Post by BLTicklemonster on 2005-10-11
You probably can, using 2k4, but I was using this [http://files.filefront.com/ut+install+436+GOTY/;1634336;;/fileinfo.html](http://files.filefront.com/ut+install+436+GOTY/;1634336;;/fileinfo.html) with my ut goty install disk. I wonder if it's something to do with that file? This didn't happen with the one from loki.

---

### Post by seethru on 2005-10-11
ahh all I've got is 2k3 and 2k4 heh :/

when you run the installer, does it ask you to specify where to install it to?

---

### Post by BLTicklemonster on 2005-10-11
Yes, well, it shows the path, and I can change it. I was afraid to change it, because I was in root, and assumed (hee haw) that no matter where I changed it to, I'd still have to be root to play it. I'm thinking you will now tell me that I am wrong, to go ahead and change it from /urs/loca/games/ut to /home/bill/games/ut ?

---

### Post by seethru on 2005-10-11
yep you should be able to, might need to change ownership though once it is installed.

---

### Post by BLTicklemonster on 2005-10-11
AHA! um what's that mean? I'll see if I can find the answer, but if I don't, if you'd not mind just dropping a little hint...

---

### Post by seethru on 2005-10-11
if the ownership is set to root on the ut directory just run (in a terminal)

```
cd /enter/games/directory/here
sudo chown -R yourusername utdirectory

```

---

### Post by BLTicklemonster on 2005-10-11
I'm installing it now (okay, so I got another hard drive out and loaded up breezy, sorry. BUT, check this out, I was tripping bigtime! There was no terminal in applications>system tools!!! So I get inventive and started looking around and found the applications menu editor, and found it in system tools unchecked, so I checked it, and now actually it's root terminal, what the heck.) Anyway, I changed it to /home/bill/games/ut and it still said I couldn't do it, so I changed where it was going to put a path to /usr/bins and it let me install it. Perhaps this will take care of it. Also, this time when I installed just the nvidia-glx, I rebooted, and I saw a nvidia splash screen, so I think ... yeah, probably the nvidia drivers are loaded. 
I installed wine, also, but I never saw it come up, and I don't see it in applications anywhere, so I have no idea if it's running or not, but I guess I am about to find out.

I need to find a community of folks who use ut with linux, and who map and script/mod. OOh, got blender and wings 3d for modelling, now if I can just figure them out!!!

sheesh!

---

### Post by seethru on 2005-10-11
you won't need to worry about Wine when running UT, since it's a Linux client. Wine doesn't have an application link either, as all it's used for is running other programs.

---

### Post by BLTicklemonster on 2005-10-12
Wow. UT runs smoother in Ubuntu than it does in XP, and looks ten times better. This is sweet. Now to find out how to get unreal editor to work! 

Thanks for all your help!!! 

Oh, and I didn't use the loki files, I used [http://files.filefront.com/ut+install+436+GOTY/;1634336;;/fileinfo.html](http://files.filefront.com/ut+install+436+GOTY/;1634336;;/fileinfo.html)

---

### Post by seethru on 2005-10-12
yep, glad it's working for you :)

---

### Post by Cathbard on 2005-10-12
This may be of interest to you also. It's Cedega specifically, not wine in general.
I found it to be quite useful.
[Unofficial Trangaming Wiki]("http://cedegawiki.sweetleafstudios.com/index.php?title=Main_Page")

PS: If you want a GUI interface to view and change permissions on things just open nautilus, right click on the folder of interest and select properties. Select the permissions tab and it's all laid out in front of you.
To do this as root simply open a shell/terminal/console and type:
sudo nautilus --browser

Don't rag on the command line. There is always a command line behind any gui even if it's hidden from you like in Winblows. This is linux, it gives you access to the nuts and bolts. Learn how to use it. Learn how to use your computer not just a program. [Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by daller on 2005-10-12
Just upgraded to KDE3.5, and now the sound doesn't work in Q3 an UT2004...

Running them from commandline I get an error about /dev/dsp/ being busy!

What can I do about that?

---

### Post by daller on 2005-10-12
Killing artsd fixed this!

How do I prevent artsd from blocking the sound?

---

### Post by Shantanu80 on 2005-10-19
shantanu@Shantanu:~$ ut
dirname: too few arguments
Try `dirname --help' for more information.
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?


What does this mean?????? Happens if I try to run UT. Installed it using the Linux Installer.
Help

---

### Post by BLTicklemonster on 2005-10-19
Try doing what I did. I had that path problem, too.

---

### Post by Shantanu80 on 2005-10-19
dude.. how did you uninstall the previously installed Game?

---

### Post by Shantanu80 on 2005-10-19
nvm got the loki uninstallr and uninstalled the previous installation.. lets hope the new installation works

---

### Post by Shantanu80 on 2005-10-19
*sigh* nope.. i uninstalled the old game and installed it again using the installer mentioned in this thread. I kept the installation path as /usr/local/games/ut
and /usr/local/bin
but it still gives me the same damn error
HELP!

---

### Post by BLTicklemonster on 2005-10-19
[QUOTE=Shantanu80]*sigh* nope.. i uninstalled the old game and installed it again using the installer mentioned in this thread. I kept the installation path as /usr/local/games/ut
and /usr/local/bin
but it still gives me the same damn error
HELP![/QUOTE]
Sorry, this ought to be a bit more precise. It's all in one place step by step:

[http://ubuntuforums.org/showthread.php?t=74623](http://ubuntuforums.org/showthread.php?t=74623)

---

### Post by Shantanu80 on 2005-10-20
YAY UT Works!!! thank you TickleMonster but i got it working last night itself.. just forgot to post lol... KUbuntu ROX!!!

---

### Post by BLTicklemonster on 2005-10-20
Cool! I'm glad to get a fellow UTer up and running! Now let me ask you, did you follow the instructions exactly? If you deviated at all, can you post what you did differently? The reason I ask is that I can play, (try running the resolution up as high as you can get it, turn on all the bells and whistles, start playing, hit ~ and type in timedemo 1 and see what your frame rate is. I had 50 fps, but it played better than UT ever did at 100+ fps in windows. and if you get your mouse set up right if it's optical, it's incredible) but if the server changes maps, I get stuck and cannot reconnect. Now I haven't found a /loki/ folder anywhere on my computer, so I suspect that this is the cause of my problem. I need to find out how to get one so that the correct set up can be used.


(oh, and drop by 67.19.84.40 sometime and check out the Zark Assault Rifle. Tell them Ticklemonster sent you :) )

---

### Post by BLTicklemonster on 2005-10-20
Um... don't tell me that the reason I'm having these problems is because of this "loki installer" thing I just discovered... I installed it, now I'm installing UT again. If that was all it was, I'm ... deserving of finger pointing and being called a newb, I suppose.


*edit:

Nope. 

Back to the drawing board.

---

### Post by blaze on 2005-10-31
Hey tick, I was reading your post here (imagine that I actually listened to something you told Ron (or is it that he actually tolds me, I dont know, anyway)

I am stuck at the point where i get this error


laura@ubuntu:~$ sh unreal.tournament_436-multilanguage.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage Installer...................................................................................
/home/laura/.setup13684: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
laura@ubuntu:~$

I read where you went to  synaptic package, but i dont know where that is.  I continued to read but I got lost. (sorry, more of a newb then you and not as smart!)

---

### Post by BLTicklemonster on 2005-11-01
You got it since then, though, right?

---

### Post by Shantanu80 on 2005-11-16
heya Tickle. Firstly.. thanx for the help. Secondly.. i only play insta and i play from India so i ping round 500 avg to any given server.. lol also.. i need zp running os i dont think you'd like me mentioning anywhere that i know you hehe. Also, i'm having trouble finding the /.loki folder myself .. it says its in the home dir but its not. tho you can try taking a snapshot or record a demo by using demorec <filename> in the game console before you start a game and try doing a search for a *.dem file after the game. The filename you used shows up and it normally points at the .loki folder. Tell me if it helped

---

### Post by Shantanu80 on 2005-11-16
I tried a lot to set up Binds but i couldnt.. dunno how that works on Linux. Anyone can shed some light on this? I found the .loki folder and theres another user.ini in the system folder there.. however even when i edited the user.ini there it wouldnt set up binds for me :/ dunno why.

---

### Post by Biased turkey on 2005-11-16
Cedega does nothing, it just empty your pocket by $ 5.00 a month.
I subscribed for 6 months and NONE of the game I tried to install works.
I installed the Native Linux port of UT without any problem, then tried to install it using cedega and never had any success.

---

### Post by BLTicklemonster on 2005-11-18
God, sorry I haven't been back, here's what you do to get the loki folder and ini files.

Applications>System Tools>Configuration Editor

Desktop>gnome>file views

(possible other than gnome if you aren't using it)

check show_hidden_files

close


/home/yourname/.loki/ut/System

viola.

---

### Post by BLTicklemonster on 2005-11-18
[QUOTE=blaze]Hey tick, I was reading your post here (imagine that I actually listened to something you told Ron (or is it that he actually tolds me, I dont know, anyway)

I am stuck at the point where i get this error


laura@ubuntu:~$ sh unreal.tournament_436-multilanguage.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage Installer...................................................................................
/home/laura/.setup13684: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
laura@ubuntu:~$

I read where you went to  synaptic package, but i dont know where that is.  I continued to read but I got lost. (sorry, more of a newb then you and not as smart!)[/QUOTE]

Yes, she got it fixed, and her old man (they are in the same clan as me) kicked my butt the first map I saw him in, lmao. (but he told me he could swear I use a bot the other night, so yeah, I got him back) 

(and no, I don't use artificial aiming... hey, Shantanu, you aren't.. nah)

---

### Post by weise on 2007-01-25
Hi,

I installed Ubuntu 6.10 x86_64.

I installed ia32-libs, ia32-libs-gtk, ia32-libs-openoffice.org, ia32-libs-sdl, ia32-sun-java5-bin, lib32asound2, lib32gcc1                                      , lib32ncurses5, lib32stdc++6, lib32z1.

I installed UT99 with sucess.

When I run ut, I get the following error:

> 
jurandy@weise:/usr/local/games/ut/System$ linux32 ./ut 
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Bound to Fire.so
Case-insensitive search: Botpack -> ..\System\BotPack.u
Bound to IpDrv.so
appError called:
Class Actor Member Owner problem: Script=48 C++=52
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down


Is there any way I can make it work???

Weise

---

### Post by Shantanu80 on 2007-01-26
I think the goty installer is only for 32 bit.
I tried running UT on the 64 bit version myself with no success. Guess theres no 64 bit installer
But if you find anything.. let me know

---

### Post by weise on 2007-01-26
> **Shantanu80 said:**
> I think the goty installer is only for 32 bit.
I tried running UT on the 64 bit version myself with no success. Guess theres no 64 bit installer
But if you find anything.. let me know

hi,

the goty installer is only for 32 bit, but you can install on the 64 bit...

see   [http://forums.epicgames.com/showthread.php?t=558177]("http://forums.epicgames.com/showthread.php?t=558177")

Weise

---

### Post by weise on 2007-01-26
I resolved the problem.

The [www.liflg.org](www.liflg.org) create a new ut99 installer with 64bit support.

I downloaded [http://www.liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.run]("http://www.liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.run")
and installed ut99.

When I ran the game I got the following error:

> "/usr/local/bin/ut: 29: Syntax error: Bad substitution"

I applied this patch:

> --- ut.tmp      2007-01-26 11:28:00.000000000 -0200
+++ ut  2007-01-26 11:54:57.000000000 -0200
@@ -26,7 +26,7 @@
     
     if [ -L "$path" ]; then
         ll="$(LC_ALL=C ls -l "$path" 2> /dev/null)" &&
-       echo "${ll/* -> }"
+       echo "$ll" | sed -e "s/.* -> //" | sed -e "s/\*//"
     else
        return 1
     fi


And the game ran with sucess.

Weise

---

