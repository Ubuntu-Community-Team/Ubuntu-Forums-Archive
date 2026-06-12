---
title: "Koctave doesn't work"
date: 2006-09-30
forum: Education &amp; Science
---

### Post by anoir on 2006-09-30
Hi.

I installed koctave from the universe repository of dapper. It just worked fine first time, but I cannot run it successfully again. After splash screen, a dialog comes up and the whole application quits automatically. The dialog says,

> Konsole is unable to open a PTY (pseudo teletype). It is likely that this is due to an incorrect configuration of the PTY devices. Konsole needs to have read/write access to the PTY devices.


I have no idea about what this means... The same thing happens in kde session as well. Octave seems to work flawlessly.

Does anybody have some ideas about this?

---

### Post by akniss on 2006-09-30
Googleing the error message brings up  quite a few hits... it looks like the 'pseudo teletype' message usually comes up when konsole is told to run a script that does not exist.  Could you possibly check to see what scripts koctave is trying to run when you start it up?

---

### Post by anoir on 2006-10-01
Thanks for reply.

Attached at the end of this post is the error message displayed when I try to run koctave from GNOME Terminal. There are some entries which resemble my case.

[INDENT][http://ubuntuforums.org/archive/index.php/t-177333.html](http://ubuntuforums.org/archive/index.php/t-177333.html)[/INDENT]
In this case the way koctave fails is little different from mine.

[INDENT][http://www.ubuntuforums.org/showthread.php?t=264427](http://www.ubuntuforums.org/showthread.php?t=264427)[/INDENT]
It works here even with the same kind of error.

As for pty device, mount shows
[INDENT]devpts on /dev/pts type devpts (rw,gid=5,mode=620)
[/INDENT]

Did anyone successfully run koctave?

> 
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
Link points to "/tmp/ksocket-rion"
Link points to "/tmp/kde-rion"
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
kbuildsycoca running...
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file kOctaveui.rc
ScimInputContextPlugin()
WARNING: please edit ~/.scim/global and change /DefaultConfigModule to kconfig
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
Uh oh.. can't write data..
kOctave: WARNING: Unable to open a pseudo teletype!
Uh oh.. can't get terminal attributes..
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
Launched ok, pid = 5252
~ScimInputContextPlugin()
rion@athlon:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x32002cc
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x32002cc
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x32002cc
ICE default IO error handler doing an exit(), pid = 5249, errno = 0


---

### Post by mips on 2006-10-01
Works fine in Kubuntu.

---

### Post by u04f061 on 2006-10-10
i am using koctave with kubuntu. it works fine on my pc. try to reinstall it.

---

### Post by anoir on 2006-10-10
Thanks for reports.

It seems that koctave works fine with kubuntu installation, while at least in my case ubuntu with kubuntu-desktop has an issue.

I'll try to install kubuntu from scratch when I can afford that much time(maybe around new year...).

---

### Post by majestros on 2007-04-24
installing kdebase with synaptic solved my problem, koctave works fine now.  

After I noticed someone posting their error messages from the terminal, I ran it from the terminal and my errors specifically mentioned "do you have kdebase installed correctly?"

After installing kdebase and its associated packages, it works fine.

---

### Post by anoir on 2007-04-24
Thanks for your information!

Now with feisty fresh install, I also got the error message that asks for kdebase.

After installing kdebase, koctave runs fine in GNOME as well, although it has some errors (I think this kind of error message often show up when I launch other KDE apps from terminal as well).

```

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
kbuildsycoca running...
DCOP Cleaning up dead connections.
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file kOctaveui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
kdecore (KProcess): WARNING: _attachPty() 12

```

---

### Post by bsingh79 on 2007-05-29
I'm using Koctave on kubuntu..it was working fine until I tried to reconfigure its settings to change the start up directory..

I've already tried reinstalling and installing kdebase..both don't seem to have fixed the error

Could anyone please help me fix this problem?

The error message is :
Konsole is unable to open a PTY (pseudo teletype). It is likely that this is due to an incorrect configuration of the PTY devices. Konsole needs to have read/write access to the PTY devices.

I'm getting the following error when I run it thru terminal:

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file kOctaveui.rc
ScimInputContextPlugin()
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
Uh oh.. can't write data..
kOctave: WARNING: Unable to open a pseudo teletype!
Uh oh.. can't get terminal attributes..
~ScimInputContextPlugin()
bsingh@bsingh-laptop:~/code/octave_files$ koctave
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file kOctaveui.rc
ScimInputContextPlugin()
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
Uh oh.. can't write data..
kOctave: WARNING: Unable to open a pseudo teletype!
Uh oh.. can't get terminal attributes..
~ScimInputContextPlugin()

---

### Post by u04f061 on 2007-05-29
does koctave works for octave2.9?

---

### Post by sawjew on 2007-05-29
Koctave is old and no longer developed.  If you want a new interface for octave check out Qtoctave [https://forja.rediris.es/projects/csl-qtoctave/]("https://forja.rediris.es/projects/csl-qtoctave/").

I am currently using this and it works fine on Ubuntu and it is highly configurable.

---

### Post by rockets on 2007-06-05
> **u04f061 said:**
> does koctave works for octave2.9?

I installed octave 2.9 and koctave forced octave 2.1 also. 
I launched kOctave, went to Settings-Configure and pointed the path to /usr/bin/octave2.9.
It appears to work...

---

### Post by vikasmk on 2007-10-07
i use ubuntu 7.04  , and i installed koctave recently. i just cant seem to run any programs on it.
 whenever i write a program and hit save and run koctave closes and that's it .nothing happens. can any one help me????

---

### Post by sawjew on 2007-10-07
For Koctave to work correctly on Ubuntu you need to install kdebase; ```
sudo apt-get install kdebase
```

After that it should work properly, however I would strongly recommend trying Qtoctave which I mentioned a couple of posts back.  Follow the link in that post and download the source and compile and install it.  Koctave hasn't been actively developed for years whereas Qtoctave is under constant development and, in my opinion, is a lot more useful than Koctave.

If you are not happy with compiling from source it is quite easy, especially if you use Checkinstall which enables you to uninstall with Apt/Synaptic like anything else.

---

### Post by LaserJock on 2007-10-08
Quick note, qtoctave is in Debian [http://packages.debian.org/qtoctave](http://packages.debian.org/qtoctave) and if you download the .debs you can probably install them OK (haven't tested any though so I'm just guessing).

Given that qtoctave is packaged up and the dead upstream for koctave I think I'll be removing koctave from Hardy and syncing qtoctave over from Debian.

-LaserJock

---

