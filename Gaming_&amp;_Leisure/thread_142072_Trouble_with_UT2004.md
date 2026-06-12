---
title: "Trouble with UT2004"
date: 2006-03-09
forum: Gaming &amp; Leisure
---

### Post by dabs on 2006-03-09
Hi all, was wondering if anyone has seen anything like this before:

Installed UT2004 fine, I go to run it and get:

```
dabs@dabs:~$ ut2004
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error
```

humm..

run as root:

```
dabs@dabs:~$ sudo ut2004
ReadFile beyond EOF 0+4/0

History:

Exiting due to error

```

(The splash screen comes up for a second in each occasion).

Applied the latest patch, no change.

Drivers and all that good stuff set up fine.

For the hell of it i tried:

```
dabs@dabs:~$ su
root@dabs:~$ ut2004
```

Fullscreen splash comes up, with mouse pointer, and thats about it  ->  system is completely hung (beyond ctrl+alt+backspace at least).

So thats where i am now...
I checked out ~/.ut2004/System/UT2004.log

```
Log: Log file open, Thu Mar  9 22:32:25 2006
Init: Name subsystem initialized
Init: Version: 3369 (128.29)
Init: Compiled: Dec 12 2005 12:14:12
Init: Command line: 
Init: (This is Linux patch version 3369.1)
Init: Character set: Unicode
Init: Base directory: /opt/ut2004/System/
Init: Ini:UT2004.ini   UserIni:User.ini
Init: Build label: UT2004 Build UT2004_Build_[2005-11-23_16.22]
Init: Object subsystem initialized
Critical: ReadFile beyond EOF 0+4/0
Exit: Executing UObject::StaticShutdownAfterError
Exit: Exiting.
Log: FileManager: Reading 0 GByte 11 MByte 372 KByte 964 Bytes from HD took 0.203240 seconds (0.203240 reading, 0.000000 seeking).
Log: FileManager: 0.000000 seconds spent with misc. duties
Uninitialized: Name subsystem shut down
Uninitialized: Log file closed, Thu Mar  9 22:32:27 2006
```

So no help there then..

I'm kind of at a loss, any help would be much appriciated.

---

### Post by Noremacam on 2006-03-09
To me, it sounds like a file was corrupt(and not replaced by the update). I would attempt a reinstallation...

---

### Post by dabs on 2006-03-09
Already done multiple times, as both myself and root.

I have also tried deleting UT2004.ini, in case that was corrupt, but nup.

---

### Post by Horndog on 2006-03-09
> 
I checked out ~/.ut2004/System/UT2004.log


Try looking for /root/.ut2004/System/UT2004.log

This is what happens when you start ut2004 as root.

---

### Post by dabs on 2006-03-09
yup, already looked, nothing helpful.

Kate complained this was a binary...  Didnt look too pretty when it opened.
Edited out some spaces to improve legibility.


```
Log:Logfileopen,ThuMar919:17:252006
Init:Namesubsysteminitialized
Log: Yourlocale: [UTF-8].

Log: EnabledUNICODEsupport.
Init: Version: 3186 (127.29)
Init: Compiled: Mar 4200403:07:41
Init: Commandline: 
Init: (ThisisLinuxpatchversion3186.0)
Init: Characterset: Unicode
Init: Basedirectory: /opt/ut2004/System/
Init: Ini:UT2004.ini  UserIni:User.ini
Init: Buildlabel: UT2004BuildUT2004 Build [2004-03-03 02.42]
Init: Objectsubsysteminitialized
Warning: MissingClassClassEditor.TransBuffer
Critical: ReadFilebeyondEOF0+4/0
Exit: ExecutingUObject::StaticShutdownAfterError
Exit: Exiting.
Log: FileManager: Reading0GByte11MByte20KByte778BytesfromHDtook0.514626seconds (0.153529reading, 0.361097seeking).
Log: FileManager: 0.000000secondsspentwithmisc. duties
Uninitialized: Namesubsystemshutdown
Uninitialized: Logfileclosed, ThuMar 919:17:292006

```

Cheers for the replies so far.


[edit]
Thats interesting, looking at that log i can see that that is from when i tried running it from inside *su*, and has not been updated when i just used sudo..

On that line of thought, anyone got a clue why i get different results using sudo and su?

---

### Post by Horndog on 2006-03-09
[QUOTE=Harleen]

When running with sudo, you run the program with root priviledges, but with your user's environment variables. So you are not using the configuration from /root/.ut2004 but from /home/<user>/.ut2004. Because some files get the ownership of root after running with sudo, you cannot play as normal user after running once with sudo.
Changing the ownership of that directory to your normal user should enable you to play as normal user.

Try this:
sudo chown <user> ~/.ut2004 -R
ut2004
[/QUOTE]

This may help.

---

### Post by dabs on 2006-03-09
humm, progress of a sort...

now running as myself give me the same error as with sudo does..

```
ReadFile beyond EOF 0+4/0

History:

Exiting due to error

```

---

### Post by Horndog on 2006-03-09
I'm sure this is a permission problem. Check to see if you have write permission on your ut2004.ini, user.ini and make sure you have execute permission on your ut2004-bin

---

### Post by dabs on 2006-03-09
yerp, everything is rw, i even tried setting the install dir writable.

```
dabs@dabs:~$ ls -l .ut2004/System
total 36
-rw-r--r--  1 dabs dabs     0 2006-03-10 02:24 Running.ini
-rw-r--r--  1 dabs root  9516 2006-03-09 22:05 User.ini
-rw-r--r--  1 dabs root 18170 2006-03-09 22:13 UT2004.ini
-rw-r--r--  1 dabs root   806 2006-03-10 02:24 UT2004.log

```

---

### Post by dabs on 2006-03-13
bump

---

### Post by dabs on 2006-03-16
and again

---

### Post by Harleen on 2006-03-18
Have you already tried to run the game directly after install without any additional patches? Does it give you the same error?
Because the latest patches require you to install the Editors Choice Bonus Pack first and may give you that error if you don't do so before.

---

### Post by Scunizi on 2006-03-18
This is the most current UT4 thread I could find.  I got UT to install and run the first couple of times now I try and the splash screen comes up and then disappears.  Looking at the console this is what I see.

WARNING: ALC_EXT_capture is subject to change!
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x131
  Serial number of failed request:  151
  Current serial number in output stream:  152

Any ideas?:???:

---

### Post by dabs on 2006-03-19
yup, i tried it without patches...

going to download it from the net and use my own serial, see if my media is dodgy..

---

### Post by Harleen on 2006-03-19
I don't think that this is a problem of your media. This is an excerpt of my UT2004.log:

```
Init: Build label: UT2004 Build UT2004_Build_[2005-11-23_16.22]
Init: Object subsystem initialized
Log: Initializing OpenGLDrv...
Log: binding libGL.so.1
```

So the next message in the logfile that should be there instead of that cryptic "ReadFile beyond EOF 0+4/0" is about loading the OpenGL driver. Running UT without OpenGL acceleration results in different, more useful output. So there's something other going on.

Try to eliminate the OpenGL-driver as an error cause by using software rendering. This will run awfully slow, but it may give you a direction for searching for the error.
To use the software renderer you need the latest patch 3369 installed.
Then change in your UT2004.ini 

```
[Engine.Engine]
;RenderDevice=D3DDrv.D3DRenderDevice
;RenderDevice=D3D9Drv.D3D9RenderDevice
;RenderDevice=Engine.NullRenderDevice
[COLOR="Red"]RenderDevice=OpenGLDrv.OpenGLRenderDevice
;RenderDevice=PixoDrv.PixoRenderDevice[/COLOR]
```

to this

```
[Engine.Engine]
;RenderDevice=D3DDrv.D3DRenderDevice
;RenderDevice=D3D9Drv.D3D9RenderDevice
;RenderDevice=Engine.NullRenderDevice
[COLOR="Red"];RenderDevice=OpenGLDrv.OpenGLRenderDevice
RenderDevice=PixoDrv.PixoRenderDevice[/COLOR]
```

After that, pray and run UT.

---

### Post by fiendskull9 on 2006-03-23
just a smart *** correction, but the latest LINUX patch is 3355, the microslush patch is 3369.

clay

---

### Post by Harleen on 2006-03-23
No, the linux version of that patch came out just one or two days after the Windows version. You can get it here: [http://download.beyondunreal.com/fileworks.php/official/ut2004/ut2004-lnxpatch3369-2.tar.bz2](http://download.beyondunreal.com/fileworks.php/official/ut2004/ut2004-lnxpatch3369-2.tar.bz2)

---

