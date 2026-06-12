---
title: "launcher for GoogleEarth does not work, command line does"
date: 2006-01-15
forum: Desktop Environments
---

### Post by sup on 2006-01-15
Hello, following this great wiki page: [https://wiki.ubuntu.com/GoogleEarth]("https://wiki.ubuntu.com/GoogleEarth"), I managed to have Google Earth working, when launched from command line. I also tried to make a launcher for it but with no succes. 
The command I can launch Google Earth with is either ```
WINEDLLOVERRIDES="ole32,usp10,msvcrt=n" wine /home/tom/.wine/drive_c/Program\ Files/Google/Google\ Earth/GoogleEarth.exe
```
or simply(see the guide) ```
gEarth
```
when I click on a panel>>Add to Panel>>Custom Application Launcher and fill gEarth in command table, I got following error message:

Cannot launch icon
Details: Failed to execute child process "gEarth" (No such file or directory)

putting 
WINEDLLOVERRIDES="ole32,usp10,msvcrt=n" wine /home/tom/.wine/drive_c/Program\ Files/Google/Google\ Earth/GoogleEarth.exe 
in there gives nothing, when I try to run it in terminal, it opens and closes in less then one second.

So I tried to put 
wine /home/tom/.wine/drive_c/Program\ Files/Google/Google\ Earth/GoogleEarth.exe
in the command line and 
WINEDLLOVERRIDES="ole32,usp10,msvcrt=n"
in advanced>>try this before using

Then, when I try to run it with checked run in terminal, I get this:
```
fixme:atl:AtlModuleInit SEMI-STUB (0x466920 0x4658f0 0x400000)
fixme:imm:ImmGetContext (0x10020): stub
fixme:imm:ImmReleaseContext (0x10020, 0x7fda87f8): stub
fixme:imm:ImmGetContext (0x10020): stub
fixme:imm:ImmReleaseContext (0x10020, 0x7fda87f8): stub
fixme:secur32:GetUserNameExW 2 0x3a0e87d0 0x7fadf95c
fixme:imm:ImmGetContext (0x10024): stub
fixme:imm:ImmReleaseContext (0x10024, 0x7fda87f8): stub

```

Any ideas?

---

### Post by awi on 2006-01-17
I see, according to the guide, that gEarth is an alias' bash, which works only when you  are running from bash.
I'm not sure that gnome (panel, launchers, etc.) gets bash environment, including alias. 
You should try making a bash script called gEarth, and put ir some place on your path.

---

### Post by sup on 2006-01-27
thanks, 
```
sudo vi /usr/local/bin/gEarth
```
```
#/bin/bash
WINEDLLOVERRIDES=\"ole32,usp10,msvcrt=n\"
wine /home/tom/.wine/drive_c/Program\ Files/Google/Google\ Earth/GoogleEarth.exe

```
```
sudo chmod +x gEarth
```
and the filling in command in launcher properties gEarth made it.
I even made an icon for the launcher, see the attached file (.png, 16x16 a nice idea to place it would be /usr/share/icons/crystalsvg/16x16/apps/)

---

