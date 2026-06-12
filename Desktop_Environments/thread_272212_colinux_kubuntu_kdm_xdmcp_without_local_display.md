---
title: "colinux kubuntu kdm xdmcp without local display"
date: 2006-10-05
forum: Desktop Environments
---

### Post by fastguy on 2006-10-05
Hi,

I've spent a few hours to make kdm work without a local display adapter (no local :0 display) but could not succeed.

I'm running my normal kubuntu 6.06 installation inside colinux, and thus I don't have a local display adapter to start with kdm. If I can start kdm with -only- xdmcp support, then I will be able to use xming to have the login screen.

if it was gdm, i can just comment the :0 display in Xservers file, but Kubuntu (KDE) does not have such file. 

Could you please comment what I should change in which file (kdmrc?) to make kdm start without a local display?

Thanks and best regards,

Fast

---

### Post by Richard Menke on 2008-05-06
I was having the same problem, this worked for me (Kubuntu 7.10 AMD64) :

Edit the kdmrc file and comment out or delete the values after the following keys in the section "General"

```

[General]
StaticServers=#:0
ReserveServers=#:1,:2,:3

```

You can actually use this to create multiple sessions on one machine at start up. I used this on my client PC to create 1 session locally and one session on a xdmcp server.

```

[General]
StaticServers=:0,:1
ReserveServers=:2,:3,:4

```

you probably also want to create a copy of the sections  [X-:0-Core] and [X-:0-Greeter], and name them  [X-:1-Core] and [X-:1-Greeter]. You can do you're settings here

here is a example of the kdmrc :

```

[General]
ConfigVersion=2.3
StaticServers=:0,:1
ReserveServers=:2,:3,:4
ServerVTs=-9
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
PidFile=/var/run/kdm.pid

[Xdmcp]
Enable=true
Willing=/etc/kde3/kdm/Xwilling

[Shutdown]
BootManager=Grub

# Greeter config for all displays
[X-*-Core]
Setup=/etc/kde3/kdm/Xsetup
Startup=/etc/kde3/kdm/Xstartup
Reset=/etc/kde3/kdm/Xreset
Session=/etc/kde3/kdm/Xsession
AllowRootLogin=false
AllowNullPasswd=false
AllowShutdown=Root
AllowSdForceNow=Root
DefaultSdMode=ForceNow
ScheduledSd=Never
ClientLogFile=.xsession-errors-%s
UseSessReg=true

# Greeter config for all displays
[X-*-Greeter]
LogoArea=Clock
LogoPixmap=/usr/share/apps/kdm/pics/kdelogo.png
GreetString=Welcome to %s - %r at %h using display %d
AntiAliasing=true
UserCompletion=true
MinShowUID=1000
MaxShowUID=29999
FaceSource=PreferUser
PreselectUser=Previous
FocusPasswd=true
EchoMode=OneStar
Preloader=/usr/bin/preloadkde
Theme=@@@ToBeReplacedByDesktopBase@@@
AllowClose=true

# Core config for local displays
[X-:*-Core]
ServerCmd=/usr/bin/X -br
ServerArgsLocal=-nolisten tcp
AllowNullPasswd=false
AllowShutdown=All
AllowSdForceNow=All
NoPassEnable=false

# Greeter config for local displays
[X-:*-Greeter]
PreselectUser=Previous
FocusPasswd=true
LoginMode=DefaultLocal
AllowClose=true

# Core config for 1st local display
[X-:0-Core]
ServerVT=9
AutoLoginEnable=true
AutoLoginAgain=false
AutoLoginDelay=0
AutoLoginUser=richard
AutoLoginLocked=false

# Greeter config for 1st local display
[X-:0-Greeter]
PreselectUser=Default
DefaultUser=richard
FocusPasswd=true
LoginMode=LocalOnly
AllowClose=true

# Core config for 1st remote display
[X-dceRouter:1-Core]
ServerVT=10
AutoLoginEnable=true
AutoLoginAgain=false
AutoLoginDelay=0
AutoLoginUser=richard
AutoLoginLocked=false

# Greeter config for 1st remote display
[X-dceRouter:1-Greeter]
PreselectUser=Default
DefaultUser=richard
FocusPasswd=true
LoginMode=RemoteOnly
AllowClose=true

```

I'm still not sure if I actually not starting kde itself so that I run this server with minimal recourse's. But at least kdm is started because xdmcp is working fine.

I hope this helped.

---

