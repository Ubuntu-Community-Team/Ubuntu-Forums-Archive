---
title: "Black screen after logout"
date: 2011-01-12
forum: Desktop Environments
---

### Post by dargaud on 2011-01-12
Hello all,
If I try to logout or switch user, I end up with a black screen and a blinking cursor. I can type and the letters show up on the screen but don't do anything. I can do Ctrl-Alt-F1 and then "sudo service kdm restart", but I'd rather fix the underlying problem...
Google gives several pages with similar problems but they all seem pretty old (2007), and they don't seem to apply to 10.10.
Any idea ?
Thanks

---

### Post by Zorael on 2011-01-12
What videocard driver are you using?

In the past, some drivers (notably Intel's) made the X server crash when trying to regenerate the X session at logout. In essence, instead of shutting down X and starting it again, it tries to reuse the same process to save time and resources. If so, I think there will be a crash backtrace in **/var/log/kdm.log**.

You can disable this resetting behavior in **/etc/kde4/kdm/kdmrc** by finding the **TerminateServer=true** line and uncommenting it.

```
# Restart instead of resetting the local X-server after session exit.
# Use it if the server leaks memory etc.
# Default is false
**[COLOR="Green"]TerminateServer=true[/COLOR]**
```
Use whichever text editor you're comfortable with.

To do it all from the terminal;
```
$ FILE=/etc/kde4/kdm/kdmrc
$ sudo cp $FILE ${FILE}.orig
$ sudo sed -ie 's/\#TerminateServer/TerminateServer/g' $FILE
```

---

### Post by dargaud on 2011-01-13
Thanks for the suggestions:
```
# lshw
           *-display
                description: VGA compatible controller
                product: Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:17 memory:c8000000-cfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff

```
As for /etc/kde4/kdm/kdmrc, there's no such TerminateServer in it:
```
[General]
ConfigVersion=2.4
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
GreeterUID=kdm
PidFile=/var/run/kdm.pid
ReserveServers=:1,:2,:3
ServerVTs=-7
StaticServers=:0

[Shutdown]
BootManager=None
HaltCmd=/sbin/halt
RebootCmd=/sbin/reboot

[X-*-Core]
AllowNullPasswd=false
AllowRootLogin=false
AllowShutdown=Root
AutoReLogin=false
ClientLogFile=.xsession-errors-%d
Reset=/etc/kde4/kdm/Xreset
Session=/etc/kde4/kdm/Xsession
Setup=/etc/kde4/kdm/Xsetup
Startup=/etc/kde4/kdm/Xstartup

[X-*-Greeter]
AntiAliasing=false
ColorScheme=
FaceSource=AdminOnly
FailFont=Sans Serif,10,-1,5,75,0,0,0,0,0
GUIStyle=
GreetFont=Serif,20,-1,5,50,0,0,0,0,0
GreetString=Welcome to %s at %n
GreeterPos=50,50
HiddenUsers=
Language=en_US
LogoArea=Logo
LogoPixmap=/usr/share/kde4/apps/kdm/pics/kdelogo.png
MaxShowUID=29999
MinShowUID=1000
Preloader=/usr/bin/preloadkde
SelectedUsers=
ShowUsers=NotHidden
SortUsers=true
StdFont=Sans Serif,9,-1,5,50,0,0,0,0,0
Theme=/usr/share/kde4/apps/kdm/themes/ethais
UseBackground=true
UseTheme=true
UserCompletion=false
UserList=true

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-nr -nolisten tcp
ServerCmd=/usr/bin/X

[X-:*-Greeter]
AllowClose=true
DefaultUser=dargaud
FocusPasswd=true
LoginMode=DefaultLocal
PreselectUser=Previous

[X-:0-Core]
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=
ClientLogFile=.xsession-errors

[Xdmcp]
Enable=false
Willing=/etc/kde4/kdm/Xwilling

```
I could try adding it, but to which section ? As for /var/log/kdm.log, nothing much of interest there. Maybe right after a lockup, I'll check next time:
```
ddxSigGiveUp: Closing log

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux darlap 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=dd00ea4d-5c75-4997-bd3e-3fbdd959deba ro quiet splash
Build Date: 23 November 2010  09:54:06PM
xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 13 11:07:11 2011
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] Kernel modesetting enabled.
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/1205778025/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

```

---

### Post by dargaud on 2011-01-13
Well, I added TerminateServer=true to the [X-*-Core] section and it seems to logout fine now. Thanks.

---

### Post by Wolf-Ekkehard on 2011-02-19
Thanks a bunch guys!  

The problem also occurred with my ASUS motherboard M4A88TD-V EVO/USB3 featuring an integrated ATI Radeon HD 4250 GPU running 10.10 64bit and a non-free driver that Ubuntu was kind enough to find and install for me.  Again, there is no commented out TerminateServer line in the /etc/kde4/kdm/kdmrc file, but sticking a new line in the [X-*-Core] section of that file did the trick for me as well.

Many thanks again.

---

### Post by cuyo on 2011-02-21
Great
Thanks

---

### Post by OldGaf on 2011-04-19
Works like a charm.... thanks!

---

### Post by lcb1 on 2011-05-08
I do not see how to delete messages.

---

### Post by Wolf-Ekkehard on 2011-05-19
New Kubuntu version (11.04) - same problem :-( - same solution ;-)

---

### Post by a.frings on 2012-03-31
Thank you, that terminate option helped me also (Kubuntu 11.10 on a HP notebook model 635)

---

