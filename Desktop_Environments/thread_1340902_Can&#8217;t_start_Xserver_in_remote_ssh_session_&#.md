---
title: "Can&#8217;t start Xserver in remote ssh session &#8211; X11 forwarding problem ?"
date: 2009-11-29
forum: Desktop Environments
---

### Post by cfmarshall on 2009-11-29
[FONT="Arial"]I&#8217;ve recently loaded Ubuntu 9.1 server and installed the desktop.
 
I have a Radeon HD 2600 PRO video card  and I managed to get the GUI working after installing the latest Catalyst 9.10  drivers (ati-driver-installer-9-10-x86.x86_64.run) and  
following the guidance of [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide").
. 

Everything apparently works as it should on the server. The desktop is displayed as expected and all apps work.

However, I want to run a secure remote desktop from my Acer 8930 laptop using Windows Vista Home Premium within my local network.

Following the advice in [http://digitizor.com/2009/03/01/how-to-forward-an-x11-session-to-windows-over-ssh/]("http://digitizor.com/2009/03/01/how-to-forward-an-x11-session-to-windows-over-ssh/") I have loaded Xming and putty on the client and openssh-server on the server.

I can use putty to open a ssh terminal session and successfully logon.

My problems start when I &#8220;startx -- :1&#8221;.

My log is as follows:

[INDENT][FONT="Courier New"]X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubserver 2.6.31-15-generic-pae #50-Ubuntu SMP Tue Nov 10 16:12:10 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic-pae root=UUID=9bcdfcb1-d12b-490e-8a99-7ea961009e9b ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sat Nov 28 17:22:50 2009
(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Module fglrx not found.
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(EE) fglrx(0): XMM failed to open CMMQS connection.
[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server[/FONT][/INDENT]

Lovely.

My xorg.conf looks like this :

[INDENT][FONT="Courier New"]Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection[/FONT][/INDENT]

My Xwrapper.config has &#8220;allowed_users = anybody&#8221; set.

My user account has read and write access to  both .Xauthority and .ICEauthority.

&#8220;Xauth list&#8221; on the remote ssh terminal session produces :

[INDENT][FONT="Courier New"]ubserver /unix:0  MIT-MAGIC-COOKIE-1  9b4476fd0c44ad0803aa711fe7ded165
ubserver.lan:0  MIT-MAGIC-COOKIE-1  9b4476fd0c44ad0803aa711fe7ded165
ubserver /unix:10  MIT-MAGIC-COOKIE-1  20fdbb9ad4692691233db7374ebc100a[/FONT][/INDENT]

If I run &#8220;sudo fglrxinfo&#8221; from my remote ssh terminal I get
 
[INDENT][FONT="Courier New"]&#8220;Error: Unable to open display (null)&#8221;.[/FONT][/INDENT]

Interestingly, when I &#8220;sudo fglrxinfo&#8221; from my terminal on the server I get :

[INDENT][FONT="Courier New"]X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14[/FONT][/INDENT]

I would very much appreciate any advice.

Many Thanks,
Colin
[/FONT]

---

### Post by scorp123 on 2009-11-29
Why not start GNOME directly? You don't need the "startx" script at all. For Unix-like OS the syntax would be:
```
ssh -X remote-user@server gnome-session
```

I'd say if you have X11 working locally in Windows (Hummingbird Exceed, Xming, whatever ...) and configured "Putty" for X11 forwarding you could simply test the connection with something simple, e.g.
```
xclock
xterm
gnome-terminal
```

If those work then remotely launching the full desktop should work too.

---

### Post by cfmarshall on 2009-11-29
Thanks for the prompt reply [scorp123]("http://ubuntuforums.org/member.php?u=109288").

xclock
xterm
gnome-terminal
All the above work after ssh -X command within putty on my laptop.

Maybe I'm asking the wrong question - what is the command line to remotely launch my full  desktop ? (I thought it was startx...)

---

### Post by scorp123 on 2009-11-29
> **cfmarshall said:**
> Maybe I'm asking the wrong question - what is the command line to remotely launch my full  desktop ? Maybe you could read posting #2 again? All of it? Not just the lower parts? ... ;)

---

### Post by cfmarshall on 2009-11-30
I can't run ssh from Vista, so I opened a putty terminal and logged on to the remote server and tried  "ssh -X user@servername  gnome-session". It returned 

[INDENT]** (gnome-session:3738:WARNING **:Cannot open display:

[/INDENT]Any thoughts ?

---

### Post by cfmarshall on 2009-12-03
Aha ! 

We are getting somewhere.

I can open Kubuntu desktop using the StartKDE command.

I think this must mean the issue lies in the gnome configuration, but for now I'm happy using KDE.

Thanks for the help.

---

